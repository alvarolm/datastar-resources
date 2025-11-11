# Datastar Resources

A collection of resources for [Datastar](https://data-star.dev), the hypermedia framework for building reactive web applications.

> **Note:** This repository is not endorsed by Datastar or its authors. It is a community-driven collection of resources.

<details>
<summary>About Datastar</summary>

Datastar is a lightweight hypermedia framework that enables developers to build reactive web applications using simple HTML attributes (`data-*`) and server-side logic. It eliminates the need for complex JavaScript frameworks while providing real-time capabilities, reactive frontend, and other features out of the box.

**Official Links:**
- 🌐 [Official Website](https://data-star.dev)
- 📚 [GitHub Repository](https://github.com/starfederation/datastar/)
- 🏢 [GitHub Organization](https://github.com/starfederation) - Official SDKs for Python, Java, PHP, .NET, Clojure, Rust, Kotlin, Go, Ruby, and more
- 📖 [Documentation](https://data-star.dev/guide)
</details>

---

## Organization

This repository organizes Datastar references by category. The structure and subcategories will be adapted as the collection grows.
When a reference needs additional context or detailed explanation, a dedicated markdown file can be created in the `/docs` directory.

A specific section called **[Using Datastar](#using-datastar)** showcases real-world production applications built with Datastar.

### 📚 References

#### AI Learning Resources 
**(before use, please read the official documentation at [https://data-star.dev/](https://data-star.dev/), always double check the results, use of AI is discouraged by the datastar authors)**

- **[Datastar Wiki on DeepWiki](https://deepwiki.com/starfederation/datastar)** - Comprehensive technical wiki documenting Datastar's architecture, reactive system implementation, plugin architecture, expression engine mechanics, and DOM integration. Includes detailed reference material for backend SDKs, JavaScript library usage, data attributes, build system, and IDE extensions. Covers implementation details like signals-based reactivity and SSE protocol specifications. Updated November 7, 2025. #documentation #wiki #reference #technical

- **[Datastar on Context7](https://context7.com/websites/data-star_dev)** - AI-optimized documentation index aggregating Datastar's official documentation with 487 code snippets, 137 pages, and 52,401 tokens of indexed content. Provides searchable documentation interface and raw documentation tokens for AI model integration. Benchmark score of 70.5 for documentation quality. Updated October 16, 2025. #documentation #ai-index #reference #search

#### Libraries & Tools

- **[dataSPA](https://github.com/dataSPA/dataSPA)** - Friendly fork of the Datastar hypermedia framework that restores features from the beta version that were removed or moved to Datastar Pro. Includes all open-core Datastar attributes and actions (data-bind, data-class, data-computed, HTTP methods), plus restored premium features like data-persist, data-replace-url, data-scroll-into-view, and data-view-transition. Features free browser devtools extension, reproducible builds, and DIY bundler approach. Prioritizes accessibility to previously paid features with community support. By [@lllama](https://github.com/lllama) (Felix Ingram) #frontend #framework #fork #alternative

- **[dataSPA Inspector](https://github.com/dataSPA/dataSPA-inspector)** - Browser inspector/debugger for Datastar and dataSPA applications, providing functionality similar to Datastar Pro's Inspector. Shows current page signals with element highlighting and scroll-to-element on shift-click, displays signal and element patch events from the server with console logging, clipboard copying, and event replay capabilities. Toggle between table and object views for signal inspection. By [@lllama](https://github.com/lllama) (Felix Ingram) #frontend #debugging #devtools #inspector #signals

- **[Datastar VS Code Extension](https://github.com/starfederation/datastar/tree/develop/tools/vscode-extension)** - Official Visual Studio Code extension providing intelligent autocomplete for Datastar syntax and attributes. Works with HTML and common template languages by default, with customizable language support via `datastar.enabledLanguages` setting. Supports custom file extensions (.edge, .njk, etc.) and language IDs (PHP, Twig, etc.). Requires VS Code 1.63.0 or later. MIT License. #frontend #vscode #editor #devtools #autocomplete

- **[Datastar IntelliJ Plugin](https://github.com/starfederation/datastar/tree/develop/tools/intellij-plugin)** - Official JetBrains IntelliJ plugin providing IDE support for Datastar. Features autocomplete for all Datastar custom `data-*` attributes plus DOM attributes and events. Includes optional inline documentation through Code Completion settings. Available on JetBrains Marketplace (Plugin ID: 26072). Compatible with all IntelliJ-based IDEs. #frontend #intellij #jetbrains #editor #devtools #autocomplete

- **[datastar-scoped-signals](https://github.com/Hackder/datastar-scoped-signals)** - Copy-paste utility plugin for adding scoped signal functionality to Datastar. Provides local state management with `data-scope` attribute for isolated signal namespaces, `@scoped()` and `@scopedSet()` functions for reading/writing scoped signals, and automatic cleanup. Includes `data-scoped-indicator` for loading states during async operations. By [@Hackder](https://github.com/Hackder) #frontend #signals #plugin #state-management

- **[datastar-attribute-on-keys](https://github.com/mbolli/datastar-attribute-on-keys)** - Plugin for binding keyboard events to reactive actions via `data-on-keys` attribute. Supports multi-key combinations (Alt-Q, Ctrl-Shift-S), multiple key bindings with OR logic (Escape.Enter), event scope options (global or element focus), and modifier support for preventing defaults and event propagation. Available as npm package `@mbolli/datastar-attribute-on-keys`. By [@mbolli](https://github.com/mbolli) #frontend #plugin #keyboard #events

- **[datastar-attribute-prop](https://github.com/mbolli/datastar-attribute-prop)** - Plugin extending Datastar with property binding capabilities via `data-prop` attribute. Enables reactive signal binding directly to DOM element properties (not HTML attributes) for use cases like input values, checkbox states, and custom web component properties. Supports single property binding and multiple properties using object syntax. Available as npm package `@mbolli/datastar-attribute-prop`. By [@mbolli](https://github.com/mbolli) #frontend #plugin #property-binding #reactivity

- **[data-on-remove](https://github.com/regaez/data-on-remove)** - Lightweight plugin enabling execution of custom Datastar expressions when DOM elements are removed from the page. Provides `data-on-remove` attribute with access to special variables (`el` for removed element, `parent` for former parent node). Use cases include performance measurement, security verification of sensitive data removal, and signal cleanup. MIT License. Available as npm package. By [@Regaez](https://github.com/Regaez) #frontend #plugin #dom #lifecycle

- **[datastar-beacon](https://github.com/regaez/datastar-beacon)** - Custom plugin integrating the browser's Beacon API for telemetry and tracking within Datastar applications. Provides `@beacon` action to send application state data to specified URLs with automatic signal inclusion, flexible include/exclude filtering, dual transmission modes (immediate/delayed), and smart defaults (excludes underscore-prefixed local signals). Useful for debugging, analytics, and capturing user interactions before page navigation or closure. MIT License. Version 1.0.0. By [@Regaez](https://github.com/Regaez) #frontend #plugin #analytics #telemetry #beacon

- **[datastar-cleanup](https://github.com/alvarolm/datastar-cleanup)** - Lightweight plugin (234 bytes minified) for automatic cleanup execution when Datastar's cleanup mechanism is triggered. Provides `data-on-cleanup` attribute for declarative resource disposal, timer cleanup, state management, and logging. Cleanup triggers include element removal, attribute changes, DOM morphing operations, and server patches. Leverages Datastar's built-in cleanup system. By [@alvarolm](https://github.com/alvarolm) #frontend #plugin #dom #lifecycle #cleanup

- **[datastar-resilient](https://github.com/alvarolm/datastar-resilient)** - A library for building resilient web applications with auto-recovering SSE connections. Features configurable backoff/retry strategies, connection state monitoring, and stream manipulation. By [@alvarolm](https://github.com/alvarolm) #frontend #real-time #resilience

- **[Solidstar](https://github.com/solidstarjs/solidstar)** - Almost drop-in replacement for Datastar using SolidJS reactivity system. Enables interoperability between hypermedia-driven frontend logic and Solid components. Features TypeScript support, reactive web components, and efficient signal-based state management (14.7 KiB gzipped). By [@solidstarjs](https://github.com/solidstarjs) #frontend #solidjs #reactivity

- **[via](https://github.com/go-via/via)** - Real-time engine for building reactive web applications entirely in Go. Eliminates templates, JavaScript, transpilation, and hydration through pure Go implementation with single SSE stream for real-time updates. Integrates Datastar for browser reactivity through signals and real-time HTML/Signal patches, plus Gomponents (via `via/h` package) for Go-native HTML composition. Enables full-stack Go development with type safety and composition patterns. Experimental (approaching v0.1.0). By [@go-via](https://github.com/go-via) #go #framework #backend #real-time #experimental

- **[gomponents-datastar](https://github.com/maragudk/gomponents-datastar)** - Go library providing Datastar attributes and helpers for gomponents. Enables integration of Datastar functionality into the gomponents component system with helper functions to streamline Datastar usage in Go-based web development. Mostly feature-complete and actively developed. MIT License. By [@maragudk](https://github.com/maragudk) #go #library #backend #components

- **[DatastarUI](https://github.com/CoreyCole/datastarui)** - Go/templ component library porting shadcn/ui with minimal JavaScript. Provides server-side rendered, reactive components with Tailwind CSS styling, type-safe arguments, built-in dark mode, and comprehensive accessibility support. By [@CoreyCole](https://github.com/CoreyCole) #components #go #templ #backend

- **[northstar](https://github.com/zangster300/northstar)** - Boilerplate for creating real-time hypermedia applications with Datastar, Go, NATS, Templ, and Tailwind CSS. Includes embedded NATS server, live reload, web components support, and Docker containerization. By [@zangster300](https://github.com/zangster300) #backend #boilerplate #go #real-time

- **[HyperPress](https://github.com/EstebanForge/HyperPress)** - WordPress plugin for modern hypermedia development with HTMX, Alpine AJAX, and Datastar. Features REST API for HTML partials, HyperFields (custom metadata API), and HyperBlocks (PHP-first Gutenberg blocks). By [@EstebanForge](https://github.com/EstebanForge) #wordpress #backend #integrations #php

- **[Laravel Datastar](https://github.com/putyourlightson/laravel-datastar)** - Laravel package for building reactive frontends with Datastar. Provides Blade directives for element patching, signal management, and backend-driven state management. Enables live search, infinite scrolling, form submissions, and pagination without frontend frameworks. By [@putyourlightson](https://github.com/putyourlightson) #laravel #backend #integrations #php

- **[Datastar for Craft CMS](https://putyourlightson.com/plugins/datastar)** - Craft CMS plugin for building reactive web interfaces using Twig templates. Features template-driven state management, backend request handling, and support for live search, infinite scroll, and form submissions. Free and open-source (MIT License). By [@putyourlightson](https://github.com/putyourlightson) #craftcms #backend #integrations #php

- **[Electron SSR](https://github.com/StreamUI/ssr-electron)** - Novel approach to building Electron desktop applications using server-side rendering from the main process. Eliminates traditional IPC complexity by allowing direct access to Node.js modules and Electron APIs. Supports htmx, Alpine.js, and Datastar. By [@StreamUI](https://github.com/StreamUI) #electron #desktop #integrations

- **[ft-datastar](https://github.com/banditburai/ft-datastar)** - Python library integrating Datastar with FastHTML framework. Provides helper functions for dynamic attribute binding, two-way form binding, computed properties, event handlers, and conditional rendering. Includes SSE decorator for real-time signal and DOM fragment updates, plus `FastHTMLDatastarSSEResponse` class for streaming responses. Ships with Datastar v1.0.0-beta.8. By [@banditburai](https://github.com/banditburai) #python #backend #library #fasthtml #real-time

- **[starHTML](https://github.com/banditburai/starHTML)** - Python-first hypermedia web framework forked from FastHTML, using Datastar for client-side reactivity. Features type-safe development with IDE support, Server-Sent Events for real-time interactions, and framework-agnostic CSS compatibility. Enables reactive web applications using Python syntax. By [@banditburai](https://github.com/banditburai) #python #backend #framework #real-time

- **[Stario](https://github.com/Bobowski/stario)** - Lightweight Python web framework built on Starlette for joyful, HTML-first development. Features Server-Sent Events support, Datastar patches/signals integration, simple dependency injection, and built-in Brotli compression. Emphasizes minimal complexity and rapid prototyping. By [@Bobowski](https://github.com/Bobowski) #python #backend #framework #real-time

- **[datastar.wow](https://github.com/brianium/datastar.wow)** - Data-oriented Clojure library for building Datastar applications. Provides middleware for Ring handlers with simplified signal handling, data-oriented effects, Hiccup support, and extensible registries. Built on the official Datastar Clojure SDK, Nexus, and optionally Charred (JSON) and Chassis (HTML). By [@brianium](https://github.com/brianium) #clojure #backend #library

- **[gleam-datastar](https://github.com/sporto/gleam-datastar)** - Gleam language bindings for building reactive web applications with Datastar. Includes three packages: core Datastar bindings for frontend actions and server-sent events, Wisp integration, and Lustre integration. Provides type-safe tools for server-side rendering with reactive capabilities. By [@sporto](https://github.com/sporto) #gleam #backend #library

- **[datastar.http.zig](https://github.com/zigster64/datastar.http.zig)** - Zig programming language implementation of the Datastar SDK, fully conforming to the official specification. Features stream-based architecture with no implicit allocations, support for all patch operations (DOM, signals, scripts), built-in pub/sub system for multiplayer scenarios, and passes all official Datastar validation tests. Built on Zig 0.15.2 and http.zig library, optimized for microsecond-level performance and minimal memory footprints. By [@zigster64](https://github.com/zigster64) #zig #backend #library #performance

- **[Datastar for Java](https://github.com/mailq/datajava)** - Unofficial Datastar SDK for any pure Java HTTP server framework like Spring, Quarkus or Jakarta EE. No dependencies, no Maven or any build tool required. Just copy and paste two files to your source tree. By [@mailq](https://github.com/mailq) #java #backend #nobuild

#### Guides & How-tos

- **[The Great Unlearning Doc](https://github.com/starfederation/datastar/issues/482)** - GitHub discussion proposing a comprehensive guide to help developers unlearn common misconceptions about web development with Datastar. Covers SSE compatibility with HTTP features (compression, standard methods), architectural differences from WebSocket approaches, fragment-based updates, backend flexibility, and the "10 Commandments" for working with Datastar. Key insights include keeping state server-side, prioritizing fragments over signals, and understanding that SSE is just HTTP with chunked responses. Community-driven discussion with valuable architectural guidance. #architecture #patterns #getting-started #sse #best-practices

- **[Production Considerations](/docs/considerations.md)** - Comprehensive analysis of Datastar's known limitations, architectural trade-offs, and production challenges. Covers security implications (XSS, CSP requirements), SSE reconnection behavior, HTTP/1.1 compatibility issues, state management limitations, and API stability concerns. Includes framework comparisons, real-world impact assessments, mitigation strategies, and guidance on when Datastar is (or isn't) appropriate for your use case. Essential reading for teams evaluating Datastar for production deployments. #production #security #architecture #decision-making

- **[Datastar RC6 Data Attributes Reference](https://winkler1.github.io/ds-attrs/)** - Technical API reference documenting 30+ Datastar RC6 data attributes. Provides a lookup table of declarative attributes for data binding, event handling, computed values, dynamic styling, request tracking, and change observation. Each entry includes attribute syntax and functionality description. By [@winkler1](https://github.com/winkler1) #reference #api #documentation

- **[Simplicity Is A Virtue: How To Build Modern Web Apps With Datastar](https://iansmith.github.io/dsbook/)** - Comprehensive book and learning guide for Datastar (work in progress). Aims to be the definitive resource for learning Datastar with a focus on simplicity and practical application. Uses the "mirabeau" presentation tool as a demonstration project. By [@delaneyj](https://github.com/delaneyj) and [@iansmith](https://github.com/iansmith) #getting-started #tutorial #learning

- **[TodoMVC with Datastar](https://cablehead.github.io/xs/tutorials/datastar-todomvc/)** - Tutorial demonstrating full-stack web development with event sourcing and "stream driven development" methodology. Shows how to build a TodoMVC application using event streams as the source of truth, with server-driven UI updates through SSE streaming HTML fragments. Integrates xs (event sourcing framework), minijinja-cli (templating), http-nu (HTTP server), and Datastar for reactive frontend bindings without client-side state management. By [@cablehead](https://github.com/cablehead) #tutorial #event-sourcing #real-time #sse #server-driven

- **[Intercepting and Modifying SSE Streams](/docs/intercepting-sse-streams.md)** - Advanced technique using fetch monkey-patching to intercept and transform SSE responses before Datastar processes them. Includes error handling examples. By [@alvarolm](https://github.com/alvarolm) #real-time #patterns #advanced

- **[Signaling When Datastar Has Loaded](/docs/signaling-datastar-loaded.md)** - How to dispatch a custom event when Datastar initializes, enabling third-party libraries to safely interact with Datastar-managed elements. #patterns #integrations #getting-started

- **[Basic SSE Reconnection Workaround](/docs/basic-sse-reconnection-workaround.md)** - Simple polling mechanism to maintain SSE connections through server restarts. Note: This is a basic workaround approach. By [@gazpachoking](https://github.com/gazpachoking) #real-time #patterns #workaround

#### Articles & Blog Posts

- **[Datastar: First Impressions](https://chrismalek.me/posts/data-star-first-impressions/)** - Detailed exploration of Datastar as an alternative to HTMX, covering reactive programming with signals, Server-Sent Events, and server-centric architecture. Compares Datastar with traditional frameworks and explains core concepts like actions and fragments. By Chris Malek #introduction #comparison #architecture

- **[Datastar first impressions, coming from React](https://threadgold.nz/writing/datastar-coming-from-react)** - A React developer's first experience building with Datastar by constructing a spellchecker component. Explores the architectural shift from client-side state management to server-driven rendering, signal-based reactivity, and simplified request handling. Discusses the developer experience compared to React's paradigm, including eliminating build complexity and working with semantic HTTP methods. By [@Regaez](https://github.com/Regaez) (Thomas Threadgold) #introduction #comparison #react #tutorial

- **[Why I Switched from HTMX to Datastar](https://everydaysuperpowers.dev/articles/why-i-switched-from-htmx-to-datastar/)** - Personal account of transitioning from HTMX to Datastar, highlighting Datastar's simpler API, component-based approach, real-time SSE updates, and server-driven state management. Explores multi-user collaborative applications and web-native features like CSS view transitions. By Everyday Superpowers #comparison #htmx #real-time #sse

- **[Datastar + Common Lisp](https://interlaye.red/datastar_002dcommon_002dlisp.html)** - Exploration of using Datastar with a Common Lisp backend for reactive web development. Discusses the benefits of server-side state management and alternative approaches to complex modern frameworks, showcasing a simpler and more enjoyable development experience. #commonlisp #introduction #tutorial

- **[just f*cking use datastar](https://blog.legires.fr/2025/10/11/just_fucking_use_datastar.html)** - Satirical critique of modern web development complexity, advocating for Datastar as a simpler alternative to frameworks like React. Emphasizes native web technologies and reactive data attributes over complicated frontend tooling. By le guide #opinion #comparison #simplicity

- **[ui = fn(state) done right](https://yagni.club/3m3anpetejc23)** - Technical blog post critiquing modern frontend complexity and proposing a simpler "ui = function(state)" approach using hypermedia and server-side rendering. Introduces Single Route Architecture with Datastar for keeping state on the backend, includes practical counter app example. #architecture #simplicity #tutorial #backend

- **[Datastar attribute plugin for signal value translation](https://jasalt.dev/blog/datastar-attribute-plugin/)** - Tutorial on creating a custom Datastar attribute plugin (`data-textlabel`) to decouple UI formatting from signal values. Demonstrates extending the built-in `data-text` attribute with custom processing rules, using a labels object for value translation, and working with Datastar's plugin API. Includes full code examples on GitHub/Codeberg and CodePen. By Jarkko Saltiola #tutorial #plugin #advanced #patterns

- **[Misunderstanding SSE](https://yagni.club/3m475dwkjvc2o)** - Technical article challenging common misconceptions about Server-Sent Events (SSE), explaining that SSE is fundamentally a text-based response format that works with any HTTP method (not just GET) and should be the default for server-driven page updates. Demonstrates progressive updates, form validation, and error handling using Datastar with extensive code examples comparing `text/html` vs `text/event-stream` approaches. By drk (YAGNI Club) #architecture #sse #tutorial #patterns #introduction

#### Examples

- **[1a5s-datastar](https://github.com/delaneyj/1a5s-datastar)** - Reimplementation of the "1 App 5 Stacks" project using Go, Templ, and Datastar, demonstrating high-performance web development with minimal code. Features just 321 lines of Go across 6 files plus ~125 lines of Templ, sub-millisecond query execution, 19MB memory footprint, and single binary deployment with no external dependencies. Uses pure Go SQLite implementation and standard HTTP requests (supports HTTP/2 and HTTP/3). By [@delaneyj](https://github.com/delaneyj) #go #demo #performance #templ #minimal

- **[realworld-datastar](https://github.com/delaneyj/realworld-datastar)** - RealWorld application implementation built with Go, Templ, and Datastar. Provides a full-stack reference implementation demonstrating authentication, database seeding, and task-based development workflow. Requires Go 1.23+ with watch mode for development. MIT License. By [@delaneyj](https://github.com/delaneyj) #go #demo #realworld #templ #fullstack

- **[todostar](https://github.com/romshark/todostar)** - Collaborative todo application demonstrating server-driven web development with minimal JavaScript. Built with Go, Templ templates, Datastar, TailwindCSS, and WebAwesome web components. Showcases hypermedia-first architecture with ~2,000 lines of Go code and hot-reloading via Templier. By [@romshark](https://github.com/romshark) #go #demo #collaborative #server-driven

- **[multi_db](https://github.com/asmorris/multi_db)** - Rails 8 demonstration project showcasing multi-database architecture with SQLite where each user gets their own isolated database. Features automatic database creation on first login, migration management across user databases, Rodauth authentication, and Datastar for frontend interactions. Includes Docker/Kamal deployment configuration. Experimental exploration of per-user database isolation for SaaS applications. By [@asmorris](https://github.com/asmorris) #rails #ruby #sqlite #demo #architecture #saas

- **[Minification Measurements](https://delaneyj.github.io/minification_measurements/)** - Performance measurement tool demonstrating the impact of JavaScript library minification on web page load times. Compares minified vs unminified versions of HTMX, Alpine.js, Datastar, and other libraries using real-world mobile network conditions and Core Web Vitals metrics. By [@delaneyj](https://github.com/delaneyj) #performance #metrics #optimization

- **[hifi-crud](https://github.com/Ramblurr/hifi-crud/)** - Exploration of server-driven web applications built in Clojure using "view = f(state)" principle. Features immediate mode UI updates via Datastar SSE, backend state management, strict CQRS separation, and functional core/imperative shell architecture. Built with Datahike (Datomic-like database), Hiccup templates, and Tailwind CSS. Designed for solo developers and small teams to build scalable business applications without complex technology stacks. EUPL-1.2 License. By [@Ramblurr](https://github.com/Ramblurr) #clojure #demo #architecture #server-driven #real-time

- **[One billion cells](https://cells.andersmurphy.com/)** - A Clojure implementation of the One Billion Row Challenge. By Anders Murphy #clojure #performance

- **[unac](https://github.com/Regaez/unac)** - Ultimate Noughts and Crosses (Tic-Tac-Toe) web game built with Go and Datastar. Live demo at [unac.threadgold.nz](https://unac.threadgold.nz). By [@Regaez](https://github.com/Regaez) #go #game

- **[Blinksy](https://play.putyourlightson.com/blinksy)** - Real-time multiplayer demo application built with Laravel and Datastar. Showcases the capabilities of the Laravel Datastar package for building interactive, multi-user experiences. By [@putyourlightson](https://github.com/putyourlightson) #laravel #multiplayer #real-time #demo

- **[Craft CMS Datastar Demos](https://craftcms.data-star.dev/)** - Interactive demonstration site showcasing Datastar integration with Craft CMS. Features four practical examples: live search, pagination, load more functionality, and filters. Built using the Datastar Plugin for Craft CMS. By [@putyourlightson](https://github.com/putyourlightson) #craftcms #demo #php

- **[Datastar Remix Jam Demos](https://codeberg.org/jmstevers/datastar-remix-jam-demos)** - Collection of demo applications built with Datastar and Remix. By [@jmstevers](https://codeberg.org/jmstevers) #remix #react #demo

- **[Explainers: Gerrymandering](https://schreiaj.github.io/explainers/gerrymandering/)** - Interactive educational tool demonstrating how congressional district boundaries affect electoral outcomes. Uses Datastar's reactive signals, computed properties, and data binding to visualize partisan bias across 435 U.S. House districts with dynamic national outcome simulations. Source: [github.com/schreiaj/explainers](https://github.com/schreiaj/explainers). By [@schreiaj](https://github.com/schreiaj) #demo #educational #visualization

- **[datastar-chat-example-ts](https://github.com/Mortalife/datastar-chat-example-ts)** - Real-time chat application demonstrating Datastar with server-side rendering. Built with TypeScript, Hono web framework, and SQLite/LibSQL database. Features user authentication, session management, and Docker containerization. Includes Tailwind CSS and DaisyUI for styling. By [@Mortalife](https://github.com/Mortalife) #typescript #real-time #chat #hono #demo

- **[Datastar JS Interop Demo](https://github.com/biotz/datastar-js-interop-demo)** - Exploration of bidirectional integration between Datastar and third-party JavaScript libraries. Demonstrates seamless data and control flow using Google Maps API wrapped in a Web Component. Shows how to use `data-bind`, `data-attr`, and `data-ref` for reactive updates and method invocation with external JS libraries. By [@biotz](https://github.com/biotz) #javascript #interoperability #webcomponents #demo

- **[Datastar React Interop Demo](https://github.com/biotz/datastar-react-interop-demo)** - Demonstration of bidirectional integration between Datastar and React components using Web Components as a bridge. Features Floating UI as a practical example, showing how to wrap React components for Datastar compatibility with bidirectional data flow (Datastar signals → React props, React events → Datastar signals). Includes generic conversion function for React-to-Web-Component transformation. By [@biotz](https://github.com/biotz) #react #javascript #interoperability #webcomponents #demo

- **[Chaos - Datastar Spring MVC Game](https://gadnex.duckdns.org/chaos)** - Interactive multiplayer minigame built with Datastar and Spring MVC framework. Designed for players in the same physical room using mobile devices, features real-time chaos meter updates and audio effects using Howl.js. Demonstrates building real-time gaming experiences with Datastar and Java backend. #java #spring #multiplayer #real-time #game #demo

- **[at-a-star-firehose](https://github.com/derekr/at-a-star-firehose)** - Real-time filterable interface for viewing the Bluesky atproto firehose. Demonstrates Datastar's reactive rendering capabilities combined with Bluesky's public data feed for real-time data visualization and filtering. Built with TypeScript and Bun. By [@derekr](https://github.com/derekr) #typescript #bluesky #real-time #demo

- **[kanban-comparison](https://github.com/json-bateman/kanban-comparison)** - Comprehensive comparison of 10 modern web frameworks measuring real-world bundle sizes using identical Kanban board implementations. Compares Next.js, TanStack Start, Nuxt 4, Analog, Marko, SolidStart, SvelteKit, Qwik City, Astro + HTMX, and Datastar. Features rigorous statistical methods with 10 runs per page, outlier removal, and mobile device emulation (Pixel 5, 4G throttling). All frameworks achieve excellent Lighthouse performance scores (100), with Datastar demonstrating competitive bundle size in the MPA/SSE category. By [@json-bateman](https://github.com/json-bateman) #benchmark #comparison #performance #bundle-size

#### Videos & Screencasts

- **[Is Datastar the full-stack SSE framework of the future?](https://www.youtube.com/watch?v=u0I7f6NMZvk)** - A video exploring Datastar's capabilities as a full-stack SSE framework, covering its architecture, real-time features, and potential for building modern web applications. By Everyday Superpowers #video #screencast #introduction

- **[Datastar – The hypermedia framework (Podcast)](https://open.spotify.com/show/2DQ8iwAiLF8BhUaCos3t9U)** - Official Datastar podcast discussing how Datastar helps build reactive web applications with the simplicity of server-side rendering and the power of a full-stack SPA framework. Episodes cover tooling, performance, signals, and framework design. #podcast #introduction #architecture

- **[Datastar Presentation (Slidev)](https://datastar-presentation.onrender.com/)** - Interactive slide deck presentation about Datastar built with Slidev. #presentation #introduction

- **[Real-Time Collaboration with Sprig and Datastar](https://craftcms.com/events/dot-all-2025/sessions/real-time-collaboration-with-sprig-and-datastar)** - Conference session at Dot All 2025 Lisbon (September 24, 2025) exploring how to leverage Sprig and Datastar to create dynamic, real-time, multi-player experiences driven by the backend within Craft CMS sites. By Ben Croker #conference #craftcms #real-time #multiplayer #sprig

#### Community Collections

- **[Awesome Datastar](https://github.com/Yacobolo/awesome-datastar)** - A curated awesome list of Datastar resources including official links, blog posts, development tools, video presentations, example projects, and podcasts. Community-maintained collection for developers learning and using Datastar. By [@Yacobolo](https://github.com/Yacobolo) #community #collection #learning

#### Using Datastar

- **[Conductor Sam](https://conductorsam.com)** - AI-powered train travel assistant for Europe and beyond. Provides instant answers for rail journey planning, route suggestions, seat reservations, station information, and ticket purchasing. Built with Datastar for interactive conversational interface. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. By [@mortalife](https://github.com/mortalife) #ai #travel #production

- **[Muto Mobility](https://mutomobility.com)** - Mobility Intelligence Platform helping companies manage all aspects of mobility including cars, bikes, budgets, contracts, and charging stations in one unified platform. From Latin "to move or change", Muto modernizes how businesses handle evolving mobility needs. *Datastar v1.0.0-beta.11 (detected 2025-10-19)*. #mobility #business #saas #production

- **[Buena Vista Winery](https://buenavistawinery.com/)** - Historic winery website for California's second oldest winery, founded in 1857 by Agoston Haraszthy and located in Sonoma, California. Uses a framework that has Datastar as a dependency. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. #winery #business #production

- **[Pizza Ranch](https://pizzaranch.com/)** - Family-friendly buffet restaurant chain offering pizza, chicken, salad bar, and FunZone Arcade games. Features full menu for carryout and delivery ordering. Uses a framework that has Datastar as a dependency. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. #restaurant #food #business #production

- **[Open Squash](https://opensquash.org/)** - Leading 501(c)(3) nonprofit squash organization in New York City committed to making squash accessible and affordable for everyone. Offers world-class facilities, professional coaching, leagues, clinics, and a vibrant community for players of all ages and levels. Uses a framework that has Datastar as a dependency. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. #sports #nonprofit #community #production

- **[Electrical Wholesaler](https://www.electricalwholesaler.ie/)** - Irish electrical wholesale supplier. *Datastar main version (detected 2025-10-20)*. #business #ecommerce #production

- **[THFC Database](https://thfcdb.com/)** - Interactive comprehensive database for Tottenham Hotspur Football Club featuring detailed historical records and statistics. Provides match results, competition statistics across Premier League, FA Cup, European tournaments, player information, transfer records, and unique Scorigami feature tracking score combinations. Covers over 7,600 competitive matches with detailed filtering and historical analysis. *Datastar v1.0.0-RC.5 (detected 2025-10-20)*. #sports #football #database #statistics #production

- **[10,000 Steps](https://www.10000steps.org.au/)** - Free evidence-based physical activity initiative by CQUniversity Australia, operating since 2001. Provides step tracking, monthly challenges, tournaments, workplace wellness programs, and community engagement features. Mobile app integrates with Apple Health and Health Connect. Over 714,000 members have logged 462+ billion steps. Funded by Health and Wellbeing Queensland. *Datastar main version (detected 2025-10-20)*. #health #fitness #wellness #australia #nonprofit #production

- **[CARM](https://carm.online)** - Christian Apologetics Research Ministry providing educational resources for Christian apologetics and theology. Features articles addressing theological questions, Matt Slick Live Radio broadcasts (M-F 6PM EST), community discussion forums, online schools and courses, and shop for apologetics materials. *Datastar v1.0.0-RC.5 (detected 2025-10-22)*. #education #community #radio #production

---

## Contributing

Contributions are welcome! To add a reference:

1. Add your reference to the **References** section in this README
2. Include clear descriptions and links
3. Add attribution when applicable (author, source, etc.)
4. Hashtags are optional but encouraged for discoverability
5. If additional context is needed, create a markdown file in `/docs`
6. **Version Tracking for "Using Datastar"**: When 
 submitting entries to the "Using Datastar" category, include 
 (if possible) the Datastar version detected and the date when
 it was detected. This helps track framework adoption and 
 compatibility as Datastar evolves.
7. Submit a pull request


---

## Community

- 💬 [Discord](https://discord.gg/bnRNgZjgPh)
- 🎥 [YouTube](https://www.youtube.com/@data-star)
