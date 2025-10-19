# Datastar Resources

A curated collection of resources for [Datastar](https://data-star.dev), the hypermedia framework for building reactive web applications.

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

#### Libraries & Tools

- **[dataSPA Inspector](https://github.com/dataSPA/dataSPA-inspector)** - Browser inspector/debugger for Datastar and dataSPA applications, providing functionality similar to Datastar Pro's Inspector. Shows current page signals with element highlighting and scroll-to-element on shift-click, displays signal and element patch events from the server with console logging, clipboard copying, and event replay capabilities. Toggle between table and object views for signal inspection. By [@lllama](https://github.com/lllama) (Felix Ingram) #frontend #debugging #devtools #inspector #signals

- **[datastar-scoped-signals](https://github.com/Hackder/datastar-scoped-signals)** - Copy-paste utility plugin for adding scoped signal functionality to Datastar. Provides local state management with `data-scope` attribute for isolated signal namespaces, `@scoped()` and `@scopedSet()` functions for reading/writing scoped signals, and automatic cleanup. Includes `data-scoped-indicator` for loading states during async operations. By [@Hackder](https://github.com/Hackder) #frontend #signals #plugin #state-management

- **[datastar-resilient](https://github.com/alvarolm/datastar-resilient)** - A library for building resilient web applications with auto-recovering SSE connections. Features configurable backoff/retry strategies, connection state monitoring, and stream manipulation. By [@alvarolm](https://github.com/alvarolm) #frontend #real-time #resilience

- **[Solidstar](https://github.com/solidstarjs/solidstar)** - Almost drop-in replacement for Datastar using SolidJS reactivity system. Enables interoperability between hypermedia-driven frontend logic and Solid components. Features TypeScript support, reactive web components, and efficient signal-based state management (14.7 KiB gzipped). By [@solidstarjs](https://github.com/solidstarjs) #frontend #solidjs #reactivity

- **[DatastarUI](https://github.com/CoreyCole/datastarui)** - Go/templ component library porting shadcn/ui with minimal JavaScript. Provides server-side rendered, reactive components with Tailwind CSS styling, type-safe arguments, built-in dark mode, and comprehensive accessibility support. By [@CoreyCole](https://github.com/CoreyCole) #components #go #templ #backend

- **[northstar](https://github.com/zangster300/northstar)** - Boilerplate for creating real-time hypermedia applications with Datastar, Go, NATS, Templ, and Tailwind CSS. Includes embedded NATS server, live reload, web components support, and Docker containerization. By [@zangster300](https://github.com/zangster300) #backend #boilerplate #go #real-time

- **[HyperPress](https://github.com/EstebanForge/HyperPress)** - WordPress plugin for modern hypermedia development with HTMX, Alpine AJAX, and Datastar. Features REST API for HTML partials, HyperFields (custom metadata API), and HyperBlocks (PHP-first Gutenberg blocks). By [@EstebanForge](https://github.com/EstebanForge) #wordpress #backend #integrations #php

- **[Laravel Datastar](https://github.com/putyourlightson/laravel-datastar)** - Laravel package for building reactive frontends with Datastar. Provides Blade directives for element patching, signal management, and backend-driven state management. Enables live search, infinite scrolling, form submissions, and pagination without frontend frameworks. By [@putyourlightson](https://github.com/putyourlightson) #laravel #backend #integrations #php

- **[Datastar for Craft CMS](https://putyourlightson.com/plugins/datastar)** - Craft CMS plugin for building reactive web interfaces using Twig templates. Features template-driven state management, backend request handling, and support for live search, infinite scroll, and form submissions. Free and open-source (MIT License). By [@putyourlightson](https://github.com/putyourlightson) #craftcms #backend #integrations #php

- **[Electron SSR](https://github.com/StreamUI/ssr-electron)** - Novel approach to building Electron desktop applications using server-side rendering from the main process. Eliminates traditional IPC complexity by allowing direct access to Node.js modules and Electron APIs. Supports htmx, Alpine.js, and Datastar. By [@StreamUI](https://github.com/StreamUI) #electron #desktop #integrations

- **[starHTML](https://github.com/banditburai/starHTML)** - Python-first hypermedia web framework forked from FastHTML, using Datastar for client-side reactivity. Features type-safe development with IDE support, Server-Sent Events for real-time interactions, and framework-agnostic CSS compatibility. Enables reactive web applications using Python syntax. By [@banditburai](https://github.com/banditburai) #python #backend #framework #real-time

- **[Stario](https://github.com/Bobowski/stario)** - Lightweight Python web framework built on Starlette for joyful, HTML-first development. Features Server-Sent Events support, Datastar patches/signals integration, simple dependency injection, and built-in Brotli compression. Emphasizes minimal complexity and rapid prototyping. By [@Bobowski](https://github.com/Bobowski) #python #backend #framework #real-time

- **[datastar.wow](https://github.com/brianium/datastar.wow)** - Data-oriented Clojure library for building Datastar applications. Provides middleware for Ring handlers with simplified signal handling, data-oriented effects, Hiccup support, and extensible registries. Built on the official Datastar Clojure SDK, Nexus, and optionally Charred (JSON) and Chassis (HTML). By [@brianium](https://github.com/brianium) #clojure #backend #library

- **[gleam-datastar](https://github.com/sporto/gleam-datastar)** - Gleam language bindings for building reactive web applications with Datastar. Includes three packages: core Datastar bindings for frontend actions and server-sent events, Wisp integration, and Lustre integration. Provides type-safe tools for server-side rendering with reactive capabilities. By [@sporto](https://github.com/sporto) #gleam #backend #library

#### Guides & How-tos

- **[Simplicity Is A Virtue: How To Build Modern Web Apps With Datastar](https://iansmith.github.io/dsbook/)** - Comprehensive book and learning guide for Datastar (work in progress). Aims to be the definitive resource for learning Datastar with a focus on simplicity and practical application. Uses the "mirabeau" presentation tool as a demonstration project. By [@delaneyj](https://github.com/delaneyj) and [@iansmith](https://github.com/iansmith) #getting-started #tutorial #learning

- **[Intercepting and Modifying SSE Streams](/docs/intercepting-sse-streams.md)** - Advanced technique using fetch monkey-patching to intercept and transform SSE responses before Datastar processes them. Includes error handling examples. By [@alvarolm](https://github.com/alvarolm) #real-time #patterns #advanced

- **[Signaling When Datastar Has Loaded](/docs/signaling-datastar-loaded.md)** - How to dispatch a custom event when Datastar initializes, enabling third-party libraries to safely interact with Datastar-managed elements. #patterns #integrations #getting-started

- **[Basic SSE Reconnection Workaround](/docs/basic-sse-reconnection-workaround.md)** - Simple polling mechanism to maintain SSE connections through server restarts. Note: This is a basic workaround approach. By [@gazpachoking](https://github.com/gazpachoking) #real-time #patterns #workaround

#### Articles & Blog Posts

- **[Datastar: First Impressions](https://chrismalek.me/posts/data-star-first-impressions/)** - Detailed exploration of Datastar as an alternative to HTMX, covering reactive programming with signals, Server-Sent Events, and server-centric architecture. Compares Datastar with traditional frameworks and explains core concepts like actions and fragments. By Chris Malek #introduction #comparison #architecture

- **[Why I Switched from HTMX to Datastar](https://everydaysuperpowers.dev/articles/why-i-switched-from-htmx-to-datastar/)** - Personal account of transitioning from HTMX to Datastar, highlighting Datastar's simpler API, component-based approach, real-time SSE updates, and server-driven state management. Explores multi-user collaborative applications and web-native features like CSS view transitions. By Everyday Superpowers #comparison #htmx #real-time #sse

- **[Datastar + Common Lisp](https://interlaye.red/datastar_002dcommon_002dlisp.html)** - Exploration of using Datastar with a Common Lisp backend for reactive web development. Discusses the benefits of server-side state management and alternative approaches to complex modern frameworks, showcasing a simpler and more enjoyable development experience. #commonlisp #introduction #tutorial

- **[just f*cking use datastar](https://blog.legires.fr/2025/10/11/just_fucking_use_datastar.html)** - Satirical critique of modern web development complexity, advocating for Datastar as a simpler alternative to frameworks like React. Emphasizes native web technologies and reactive data attributes over complicated frontend tooling. By le guide #opinion #comparison #simplicity

- **[ui = fn(state) done right](https://yagni.club/3m3anpetejc23)** - Technical blog post critiquing modern frontend complexity and proposing a simpler "ui = function(state)" approach using hypermedia and server-side rendering. Introduces Single Route Architecture with Datastar for keeping state on the backend, includes practical counter app example. #architecture #simplicity #tutorial #backend

- **[Datastar attribute plugin for signal value translation](https://jasalt.dev/blog/datastar-attribute-plugin/)** - Tutorial on creating a custom Datastar attribute plugin (`data-textlabel`) to decouple UI formatting from signal values. Demonstrates extending the built-in `data-text` attribute with custom processing rules, using a labels object for value translation, and working with Datastar's plugin API. Includes full code examples on GitHub/Codeberg and CodePen. By Jarkko Saltiola #tutorial #plugin #advanced #patterns

#### Examples

- **[todostar](https://github.com/romshark/todostar)** - Collaborative todo application demonstrating server-driven web development with minimal JavaScript. Built with Go, Templ templates, Datastar, TailwindCSS, and WebAwesome web components. Showcases hypermedia-first architecture with ~2,000 lines of Go code and hot-reloading via Templier. By [@romshark](https://github.com/romshark) #go #demo #collaborative #server-driven

- **[Minification Measurements](https://delaneyj.github.io/minification_measurements/)** - Performance measurement tool demonstrating the impact of JavaScript library minification on web page load times. Compares minified vs unminified versions of HTMX, Alpine.js, Datastar, and other libraries using real-world mobile network conditions and Core Web Vitals metrics. By [@delaneyj](https://github.com/delaneyj) #performance #metrics #optimization

- **[One billion cells](https://cells.andersmurphy.com/)** - A Clojure implementation of the One Billion Row Challenge. By Anders Murphy #clojure #performance

- **[unac](https://github.com/Regaez/unac)** - Ultimate Noughts and Crosses (Tic-Tac-Toe) web game built with Go and Datastar. Live demo at [unac.threadgold.nz](https://unac.threadgold.nz). By [@Regaez](https://github.com/Regaez) #go #game

- **[Blinksy](https://play.putyourlightson.com/blinksy)** - Real-time multiplayer demo application built with Laravel and Datastar. Showcases the capabilities of the Laravel Datastar package for building interactive, multi-user experiences. By [@putyourlightson](https://github.com/putyourlightson) #laravel #multiplayer #real-time #demo

- **[Datastar Remix Jam Demos](https://codeberg.org/jmstevers/datastar-remix-jam-demos)** - Collection of demo applications built with Datastar and Remix. By [@jmstevers](https://codeberg.org/jmstevers) #remix #react #demo

- **[Explainers: Gerrymandering](https://schreiaj.github.io/explainers/gerrymandering/)** - Interactive educational tool demonstrating how congressional district boundaries affect electoral outcomes. Uses Datastar's reactive signals, computed properties, and data binding to visualize partisan bias across 435 U.S. House districts with dynamic national outcome simulations. Source: [github.com/schreiaj/explainers](https://github.com/schreiaj/explainers). By [@schreiaj](https://github.com/schreiaj) #demo #educational #visualization

- **[datastar-chat-example-ts](https://github.com/Mortalife/datastar-chat-example-ts)** - Real-time chat application demonstrating Datastar with server-side rendering. Built with TypeScript, Hono web framework, and SQLite/LibSQL database. Features user authentication, session management, and Docker containerization. Includes Tailwind CSS and DaisyUI for styling. By [@Mortalife](https://github.com/Mortalife) #typescript #real-time #chat #hono #demo

- **[Datastar JS Interop Demo](https://github.com/biotz/datastar-js-interop-demo)** - Exploration of bidirectional integration between Datastar and third-party JavaScript libraries. Demonstrates seamless data and control flow using Google Maps API wrapped in a Web Component. Shows how to use `data-bind`, `data-attr`, and `data-ref` for reactive updates and method invocation with external JS libraries. By [@biotz](https://github.com/biotz) #javascript #interoperability #webcomponents #demo

- **[Datastar React Interop Demo](https://github.com/biotz/datastar-react-interop-demo)** - Demonstration of bidirectional integration between Datastar and React components using Web Components as a bridge. Features Floating UI as a practical example, showing how to wrap React components for Datastar compatibility with bidirectional data flow (Datastar signals → React props, React events → Datastar signals). Includes generic conversion function for React-to-Web-Component transformation. By [@biotz](https://github.com/biotz) #react #javascript #interoperability #webcomponents #demo

#### Videos & Screencasts

- **[Is Datastar the full-stack SSE framework of the future?](https://www.youtube.com/watch?v=u0I7f6NMZvk)** - A video exploring Datastar's capabilities as a full-stack SSE framework, covering its architecture, real-time features, and potential for building modern web applications. By Everyday Superpowers #video #screencast #introduction

- **[Datastar – The hypermedia framework (Podcast)](https://open.spotify.com/show/2DQ8iwAiLF8BhUaCos3t9U)** - Official Datastar podcast discussing how Datastar helps build reactive web applications with the simplicity of server-side rendering and the power of a full-stack SPA framework. Episodes cover tooling, performance, signals, and framework design. #podcast #introduction #architecture

#### Community Collections

- **[Awesome Datastar](https://github.com/Yacobolo/awesome-datastar)** - A curated awesome list of Datastar resources including official links, blog posts, development tools, video presentations, example projects, and podcasts. Community-maintained collection for developers learning and using Datastar. By [@Yacobolo](https://github.com/Yacobolo) #community #collection #learning

#### Using Datastar

- **[Conductor Sam](https://conductorsam.com)** - AI-powered train travel assistant for Europe and beyond. Provides instant answers for rail journey planning, route suggestions, seat reservations, station information, and ticket purchasing. Built with Datastar for interactive conversational interface. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. By [@mortalife](https://github.com/mortalife) #ai #travel #production

- **[Muto Mobility](https://mutomobility.com)** - Mobility Intelligence Platform helping companies manage all aspects of mobility including cars, bikes, budgets, contracts, and charging stations in one unified platform. From Latin "to move or change", Muto modernizes how businesses handle evolving mobility needs. *Datastar v1.0.0-beta.11 (detected 2025-10-19)*. #mobility #business #saas #production

- **[Buena Vista Winery](https://buenavistawinery.com/)** - Historic winery website for California's second oldest winery, founded in 1857 by Agoston Haraszthy and located in Sonoma, California. Uses a framework that has Datastar as a dependency. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. #winery #business #production

- **[Pizza Ranch](https://pizzaranch.com/)** - Family-friendly buffet restaurant chain offering pizza, chicken, salad bar, and FunZone Arcade games. Features full menu for carryout and delivery ordering. Uses a framework that has Datastar as a dependency. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. #restaurant #food #business #production

- **[Open Squash](https://opensquash.org/)** - Leading 501(c)(3) nonprofit squash organization in New York City committed to making squash accessible and affordable for everyone. Offers world-class facilities, professional coaching, leagues, clinics, and a vibrant community for players of all ages and levels. Uses a framework that has Datastar as a dependency. *Datastar v1.0.0-RC.5 (detected 2025-10-19)*. #sports #nonprofit #community #production

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
