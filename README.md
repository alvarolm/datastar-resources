# Datastar Resources

A curated collection of resources for [Datastar](https://data-star.dev), the hypermedia framework for building reactive web applications.

> **Note:** This repository is not endorsed by Datastar or its authors. It is a community-driven collection of resources.

<details>
<summary>About Datastar</summary>

Datastar is a lightweight hypermedia framework that enables developers to build reactive web applications using simple HTML attributes (`data-*`) and server-side logic. It eliminates the need for complex JavaScript frameworks while providing real-time capabilities, reactive frontend, and multiplayer features out of the box.

**Official Links:**
- 🌐 [Official Website](https://data-star.dev)
- 📚 [GitHub Repository](https://github.com/starfederation/datastar/)
- 📖 [Documentation](https://data-star.dev/guide)
</details>

---

## Organization

This repository organizes Datastar references by category. The structure and subcategories will be adapted as the collection grows.
When a reference needs additional context or detailed explanation, a dedicated markdown file can be created in the `/docs` directory.

### 📚 References

#### Libraries & Tools

- **[datastar-resilient](https://github.com/alvarolm/datastar-resilient)** - A library for building resilient web applications with auto-recovering SSE connections. Features configurable backoff/retry strategies, connection state monitoring, and stream manipulation. By [@alvarolm](https://github.com/alvarolm) #frontend #real-time #resilience

- **[Solidstar](https://github.com/solidstarjs/solidstar)** - Almost drop-in replacement for Datastar using SolidJS reactivity system. Enables interoperability between hypermedia-driven frontend logic and Solid components. Features TypeScript support, reactive web components, and efficient signal-based state management (14.7 KiB gzipped). By [@solidstarjs](https://github.com/solidstarjs) #frontend #solidjs #reactivity

- **[DatastarUI](https://github.com/CoreyCole/datastarui)** - Go/templ component library porting shadcn/ui with minimal JavaScript. Provides server-side rendered, reactive components with Tailwind CSS styling, type-safe arguments, built-in dark mode, and comprehensive accessibility support. By [@CoreyCole](https://github.com/CoreyCole) #components #go #templ #backend

- **[northstar](https://github.com/zangster300/northstar)** - Boilerplate for creating real-time hypermedia applications with Datastar, Go, NATS, Templ, and Tailwind CSS. Includes embedded NATS server, live reload, web components support, and Docker containerization. By [@zangster300](https://github.com/zangster300) #backend #boilerplate #go #real-time

- **[HyperPress](https://github.com/EstebanForge/HyperPress)** - WordPress plugin for modern hypermedia development with HTMX, Alpine AJAX, and Datastar. Features REST API for HTML partials, HyperFields (custom metadata API), and HyperBlocks (PHP-first Gutenberg blocks). By [@EstebanForge](https://github.com/EstebanForge) #wordpress #backend #integrations #php

- **[Laravel Datastar](https://github.com/putyourlightson/laravel-datastar)** - Laravel package for building reactive frontends with Datastar. Provides Blade directives for element patching, signal management, and backend-driven state management. Enables live search, infinite scrolling, form submissions, and pagination without frontend frameworks. By [@putyourlightson](https://github.com/putyourlightson) #laravel #backend #integrations #php

- **[Electron SSR](https://github.com/StreamUI/ssr-electron)** - Novel approach to building Electron desktop applications using server-side rendering from the main process. Eliminates traditional IPC complexity by allowing direct access to Node.js modules and Electron APIs. Supports htmx, Alpine.js, and Datastar. By [@StreamUI](https://github.com/StreamUI) #electron #desktop #integrations

- **[starHTML](https://github.com/banditburai/starHTML)** - Python-first hypermedia web framework forked from FastHTML, using Datastar for client-side reactivity. Features type-safe development with IDE support, Server-Sent Events for real-time interactions, and framework-agnostic CSS compatibility. Enables reactive web applications using Python syntax. By [@banditburai](https://github.com/banditburai) #python #backend #framework #real-time

- **[Stario](https://github.com/Bobowski/stario)** - Lightweight Python web framework built on Starlette for joyful, HTML-first development. Features Server-Sent Events support, Datastar patches/signals integration, simple dependency injection, and built-in Brotli compression. Emphasizes minimal complexity and rapid prototyping. By [@Bobowski](https://github.com/Bobowski) #python #backend #framework #real-time

#### Guides & How-tos

- **[Intercepting and Modifying SSE Streams](/docs/intercepting-sse-streams.md)** - Advanced technique using fetch monkey-patching to intercept and transform SSE responses before Datastar processes them. Includes error handling examples. By [@alvarolm](https://github.com/alvarolm) #real-time #patterns #advanced

- **[Signaling When Datastar Has Loaded](/docs/signaling-datastar-loaded.md)** - How to dispatch a custom event when Datastar initializes, enabling third-party libraries to safely interact with Datastar-managed elements. #patterns #integrations #getting-started

- **[Basic SSE Reconnection Workaround](/docs/basic-sse-reconnection-workaround.md)** - Simple polling mechanism to maintain SSE connections through server restarts. Note: This is a basic workaround approach. By [@gazpachoking](https://github.com/gazpachoking) #real-time #patterns #workaround

#### Articles & Blog Posts

- **[Datastar: First Impressions](https://chrismalek.me/posts/data-star-first-impressions/)** - Detailed exploration of Datastar as an alternative to HTMX, covering reactive programming with signals, Server-Sent Events, and server-centric architecture. Compares Datastar with traditional frameworks and explains core concepts like actions and fragments. By Chris Malek #introduction #comparison #architecture

- **[Why I Switched from HTMX to Datastar](https://everydaysuperpowers.dev/articles/why-i-switched-from-htmx-to-datastar/)** - Personal account of transitioning from HTMX to Datastar, highlighting Datastar's simpler API, component-based approach, real-time SSE updates, and server-driven state management. Explores multi-user collaborative applications and web-native features like CSS view transitions. By Everyday Superpowers #comparison #htmx #real-time #sse

#### Examples

- **[One billion cells](https://cells.andersmurphy.com/)** - A Clojure implementation of the One Billion Row Challenge. By Anders Murphy #clojure #performance

- **[unac](https://github.com/Regaez/unac)** - Ultimate Noughts and Crosses (Tic-Tac-Toe) web game built with Go and Datastar. Live demo at [unac.threadgold.nz](https://unac.threadgold.nz). By [@Regaez](https://github.com/Regaez) #go #game

#### Videos & Screencasts

- **[Is Datastar the full-stack SSE framework of the future?](https://www.youtube.com/watch?v=u0I7f6NMZvk)** - A video exploring Datastar's capabilities as a full-stack SSE framework, covering its architecture, real-time features, and potential for building modern web applications. By Everyday Superpowers #video #screencast #introduction

#### Community Collections

- **[Awesome Datastar](https://github.com/Yacobolo/awesome-datastar)** - A curated awesome list of Datastar resources including official links, blog posts, development tools, video presentations, example projects, and podcasts. Community-maintained collection for developers learning and using Datastar. By [@Yacobolo](https://github.com/Yacobolo) #community #collection #learning

---

## Contributing

Contributions are welcome! To add a reference:

1. Add your reference to the **References** section in this README
2. Include clear descriptions and links
3. Add attribution when applicable (author, source, etc.)
4. Hashtags are optional but encouraged for discoverability
5. If additional context is needed, create a markdown file in `/docs`
6. Submit a pull request

---

## Community

- 💬 [Discord](https://discord.gg/bnRNgZjgPh)
- 🎥 [YouTube](https://www.youtube.com/@data-star)
