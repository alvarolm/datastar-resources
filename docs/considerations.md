# Datastar Production Considerations

> **About This Document**
> This document outlines known limitations, architectural trade-offs, and potential challenges when using Datastar in production environments. It is intended to help developers make informed decisions about when and how to use Datastar effectively. These are community-identified concerns based on framework analysis, GitHub issues, and real-world testing as of **November 2025 (v1.0.0-RC.6)**.
>
> **Disclaimer:** This is not official Datastar documentation. It represents a critical analysis of the framework's current state to supplement the official documentation. Always consult the [official Datastar documentation](https://data-star.dev) and [GitHub repository](https://github.com/starfederation/datastar) for the most current information.

## Documentation Gaps

<details>
<summary><h3>Plugin API: Undocumented and Unofficial</h3></summary>

While plugins are used in the Datastar ecosystem, the plugin API has not been officially announced or documented. When questioned about incomplete documentation, a Datastar maintainer stated:

> "How is it incomplete documentation if it the plugin API has not yet officially been announced?"

This response reveals the core issue: functionality exists and is being used, but without official status. This means:

- No official documentation exists
- No API stability guarantees
- Developers must read source code to understand implementation
- API may change without notice in future releases

The distinction between "in use" and "officially supported" creates uncertainty about whether developers should rely on plugin functionality in production applications.

</details>

<details>
<summary><h3>Missing Build Instructions (no reproducible builds)</h3></summary>

**The Problem:**
Datastar provides pre-built bundles with each release and hosts them on CDN (https://cdn.jsdelivr.net/gh/starfederation/datastar@1.0.0-RC.6/bundles/datastar.js), but **does not document how those bundles are built**. While the source code is available, the absence of build instructions means developers cannot independently reproduce the official releases.

**Why This Matters:**
Without documented build steps, developers face critical challenges:

**Supply Chain Security:** No way to verify that published bundles match the tagged releases
**Reproducible Builds:** Organizations with security requirements cannot independently recreate official releases

**When Build Instructions Are Critical:**
- **Security-conscious environments:** Enterprises, government, healthcare, and financial sectors often require verifying that dependencies can be built from source to match published artifacts
- **Supply chain verification:** Organizations need to confirm that CDN-hosted bundles correspond exactly to the source code at a given tag/release
- **Custom builds:** Projects requiring modifications (e.g., changing the `data-` prefix, custom bundling strategies)
- **CI/CD integration:** Automated pipelines that require building all dependencies from source for audit trails
- **Compliance requirements:** Industries with strict compliance standards (SOC 2, HIPAA, PCI-DSS) may require reproducible builds

**The Reproducibility Gap:**
The core issue is that while Datastar is open-source, **the build process is undocumented**. This creates a gap between source code transparency and artifact transparency. Developers can read the source, but cannot verify that the distributed bundles.

**Current Status:**
Build instructions are now available (as of November 2025) through community documentation. To build Datastar from source:

```bash
cd library/
npx esbuild --bundle src/bundles/datastar.ts --outdir=../bundles/ --minify --sourcemap --target=es2023 --format=esm
```

Custom alias prefixes can be configured using `--define ALIAS=...` when running the build command.

**Best Practice Recommendation:**
For production applications relying on Datastar's CDN or release bundles:
- Pin exact versions in your CDN URLs (avoid floating version tags)
- Document the specific release version being used
- Attempt to build from source and compare checksums against CDN bundles to verify integrity
- Consider self-hosting verified builds rather than depending on external CDN infrastructure

This ensures reproducible deployments and reduces supply chain risk when depending on pre-built artifacts.

**Reference:** [Datastar Tips: Building from Source](https://lllama.github.io/posts/datastartips/)

</details>

## API Stability Concerns

<details>
<summary><h3>Breaking Changes Continue During RC Phase</h3></summary>

The current version (v1.0.0-RC.6) is pre-production by definition. Release candidates should approach stability, but Datastar has continued introducing breaking changes during the RC phase.
A Datastar maintainer stated:

> "rc is our very last chance to break/change things, exposing at the last secnond is the right call"

</details>

## State Management Limitations

<details>
<summary><h3>Server-First State Management</h3></summary>

**Design Philosophy:**
Signals do not persist across page redirects or full page reloads by design. This follows the **traditional web application model** where the server is the source of truth for application state.

**Standard Web Approach:**
Most web applications use server-side state management through cookies (HTTP-based state)

This is how web applications worked before single-page application (SPA) frameworks popularized client-side state management. Datastar returns to this simpler, server-first model.

**Consideration for SPA Developers:**
Developers coming from client-heavy frameworks (React, Vue, Angular) who expect client-side state to persist automatically by default will need to adjust their mental model. This is a return to
traditional web architecture rather than a limitation.

**Applications are recommended to store their state in the backend, if you must store state on the client then you should implement manual mechanisms**

</details>

## Security Vulnerabilities

<details>
<summary><h3>XSS Prevention: Developer Responsibility</h3></summary>

**Acknowledgment:** Documented in official Datastar security documentation

**The Core Issue:**
Datastar expressions execute arbitrary JavaScript via the `Function()` constructor, creating an inherent XSS (Cross-Site Scripting) attack surface. The framework **does not automatically escape user input** in `data-*` attributes. Every user-provided value requires manual escaping, and failure to do so enables arbitrary code execution.

**Developer Responsibility:**
The security documentation explicitly warns "never trust user input" but places the full burden of input sanitization on developers. There are no automatic protections, guardrails, or validation mechanisms built into the framework.

**Content Security Policy Impact:**
This design choice mandates `unsafe-eval` in Content Security Policy (CSP), fundamentally weakening the application's security posture. Organizations with strict CSP requirements (common in enterprise, government, healthcare, and financial sectors) may be unable to use Datastar without violating their security policies.

**Risk Assessment:**
Developers should exercise extreme caution when processing untrusted content, ensuring meticulous manual escaping of every dynamic value. One oversight in input sanitization can compromise the entire application. This architectural choice requires a higher level of security awareness compared to frameworks with built-in escaping mechanisms.

**Framework Comparison:**
Many lightweight frameworks face similar trade-offs between flexibility and security:
- **Alpine.js** uses `Function()` constructor for expression evaluation, requiring `unsafe-eval` in CSP and similar manual escaping vigilance
- **Vue.js** (runtime + compiler) automatically escapes template interpolations by default, with explicit opt-in for raw HTML via `v-html`
- **React** escapes JSX expressions by default, with explicit opt-in for raw HTML via `dangerouslySetInnerHTML`
- **Svelte** escapes template expressions by default during compilation, with explicit opt-in via `{@html}`

Datastar's approach is similar to Alpine.js in prioritizing simplicity and small bundle size over built-in security mechanisms, requiring developers to implement their own escaping strategies. Frameworks with compilation steps (Vue, React, Svelte) can provide better defaults at the cost of build complexity.

**Community Security Efforts:**
There are community efforts exploring enhanced security measures for Datastar. The [datastar fork](https://github.com/starfederation/datastar/compare/develop...MichaelWest22:securestar) by [@MichaelWest22](https://github.com/MichaelWest22) focuses on improving secure evaluation mechanisms and mitigating code execution vulnerabilities through safer handling of dynamic JavaScript evaluation.

</details>

## Impractical Default Behaviors

<details>
<summary><h3>Stale Signal State on SSE Reconnection (Issue #900)</h3></summary>

**Status:** Open issue reported in v1.0.0-beta.11, confirmed in RC.5 and RC.6
**Acknowledgment:** Acknowledged by Datastar team; under evaluation for potential default behavior change

**The Problem:**
When Server-Sent Events (SSE) connections automatically reconnect after interruption, Datastar sends signals with their **initial values from when the connection was first established**, rather than their **current values** at reconnection time. This creates a critical state synchronization problem.

**Real-World Impact:**
Consider a 5-minute SSE connection where users interact with the application, modifying multiple signal values through form inputs, button clicks, and other interactions. If the SSE connection drops and automatically reconnects:
- The server receives outdated signal state from the initial connection
- All user interactions that occurred during the connection are lost
- The application state becomes desynchronized between client and server
- Users may lose work or experience unexpected behavior

**Example Scenario:**
```html
<div data-init="$count++; @get('/endpoint')">
```
If `$count` was incremented from 0 to 50 during the SSE session, a reconnection would send `$count=0` to the server instead of `$count=50`.

**The Semantic Debate:**
The Datastar team argues that semantically, a "retry" implies resending the initial request with initial state. However, multiple users counter that:
- "Reconnect" is conceptually different from "retry"
- A "retry" suggests a failed request that needs to be repeated
- A "reconnect" suggests an interrupted connection that needs to be resumed with current state
- For long-lived SSE connections with user interactions, current state is essential

**Current Workaround:**
Developers must manually handle reconnections using the `data-on:datastar-fetch` event:
```html
<div data-on:datastar-fetch="
  evt.detail.type === 'error' && console.log('Fetch error encountered')
"></div>
```
Users can then manually reinitiate the request, which will send current signals. However, this requires:
- Understanding the edge case exists
- Writing custom error handling logic
- Implementing manual reconnection management
- Additional code complexity

**Proposed Solutions:**
1. **Change default behavior** to send current signal values (currently being investigated by @andersmurphy)
2. **Make behavior configurable** with options:
   - `"original"` (default): Send original request with old signals (semantically correct for retry)
   - `"current"`: Send current signals (practical for reconnect scenarios)
3. **Add explicit `data-on:reconnect` event** to make behavior more explicit and controllable

**Developer Pain Points:**
Multiple developers have reported spending significant time debugging issues caused by this behavior:
- Unexpected state mismatches after reconnection
- Lost form data or user interactions
- Difficulty retrieving current values from sessionStorage to send to server
- Need for additional round-trips to synchronize state
- Documentation gaps around SSE lifecycle and reconnection behavior

**Impact Assessment:**
This is classified as an **impractical default behavior** rather than a bug because:
- It's technically working as semantically designed ("retry" = initial state)
- However, it violates the principle of least surprise for developers
- Real-world usage patterns expect current state on reconnection
- The workaround burden is significant
- It creates a subtle but critical failure mode that's hard to debug

**Resolution Status:**
As of the latest updates (v1.0.0-RC.6), the team is still evaluating whether to change this behavior. The most recent comment indicates active work toward changing the default to send current signals, but no timeline has been provided.

</details>

## Performance Limitations

<details>
<summary><h3>Critical: 6-Connection SSE Limit on HTTP/1.1</h3></summary>

Datastar relies heavily on Server-Sent Events (SSE) for server-to-client communication. This creates a **critical architectural bottleneck** when used over HTTP/1.1.

**Why This Still Matters in 2025:**
According to Cloudflare's 2024 Year in Review (analyzing millions of requests globally), **29.9% of all web requests in 2024 used HTTP/1.x**, with HTTP/2 at 49.6% and HTTP/3 at 20.5%. This means **nearly 30% of global web traffic still operates under HTTP/1.1's 6-connection limit**, making this a current and significant constraint rather than a legacy concern.

**The Problem:**
- HTTP/1.1 browsers enforce a strict limit of 6 concurrent connections per domain (RFC 2616)
- Each SSE connection permanently occupies one of these 6 slots—since SSE responses never complete, the connection remains in a "busy" state
- If all 6 connections are used for SSE, the browser cannot make additional requests to that domain
- This limit applies across all browser tabs for the same domain, meaning opening multiple tabs can quickly exhaust the connection pool
- The limit is implemented by all major browsers (Chrome, Firefox, Safari, Opera) and has been marked as "Won't Fix"

**Real-World Impact:**
When all connections are used by SSE, every action in the UI becomes blocked on a very narrow head-of-line-blocking pipe, as HTTP/1.1 doesn't allow multiplexing. This effectively freezes the application, preventing any other HTTP requests (images, CSS, API calls) from proceeding.

**Why HTTP/1.1 Persists:**
- Legacy infrastructure that hasn't been upgraded
- Break-and-inspect proxies that downgrade connections to HTTP/1.1
- Older server software that doesn't support HTTP/2
- Corporate security policies requiring traffic inspection
- Hosting providers and CDNs not fully migrated to HTTP/2
- Embedded systems and IoT devices with older HTTP stacks

**The HTTP/2 Solution:**
HTTP/2 solves this problem through multiplexing, with the maximum number of simultaneous HTTP streams negotiated between server and client, defaulting to 100. However, not all environments support HTTP/2, making this a deployment risk rather than a complete solution.

**Mitigation Strategies:**
- Ensure HTTP/2 support is mandatory for production deployments
- Design applications to use minimal concurrent SSE connections

**Additional Resources:**
For more SSE best practices and performance optimization tips, see the community-maintained [SSE Survival Guide](https://gist.github.com/derekr/fb8dd720d5c1600fefe3521d91ae83a4) by [@derekr](https://github.com/derekr), which covers connection management, compression strategies, and common gotchas.

</details>

## Community Feedback

Have experiences or insights to share about using Datastar in production? Join the discussion at [GitHub Discussions #5](https://github.com/alvarolm/datastar-resources/discussions/5) to share your feedback, report additional considerations, or discuss workarounds with the community.

## Summary

Datastar presents a compelling hypermedia-driven approach to building reactive web applications, but production adoption requires careful consideration of several architectural trade-offs.
The framework excels when its constraints align with project requirements, but misalignment can lead to significant architectural challenges.

---

*This document reflects the framework state as of v1.0.0-RC.6. Always consult the official Datastar documentation and release notes for the most current information.*

## Sources

- HTTP version statistics: Cloudflare Radar 2024 Year in Review (https://blog.cloudflare.com/radar-2024-year-in-review/)
- Datastar GitHub Repository: https://github.com/starfederation/datastar
- Datastar Issue #900: https://github.com/starfederation/datastar/issues/900
- Datastar Security Documentation: https://data-star.dev/reference/security
