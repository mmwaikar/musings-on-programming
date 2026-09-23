# A Rusty Portfolio

In my last blog post [A Backend Developer's Portfolio](https://mmwaikar.wordpress.com/2026/08/30/a-backend-developers-portfolio/) we saw, how we can create a beautiful resume visualizer (website) using C# Blazor and related technologies. We also saw how we can easily interop with JS libraries like Cytoscape.js for showing nodes-edges kind of graph visualization. **The whole point is to leverage as much of the backend language (C#, in this case) to do the heavy-lifting as possible and rely as less as possible on JS.** *So the question is - can we do any better? And the answer is - of course we can!*

And what better backend language to use than **Rust** 😍(as you must have guessed from the title)! It is getting *hotter* with each passing day, not only because of some famous (using AI or otherwise) rewrites like [Rewriting Bun in Rust](https://bun.com/blog/bun-in-rust), [Postgres in Rust](https://github.com/malisper/pgrust) or the [Cross-platform Rust rewrite of the GNU coreutils](https://github.com/uutils/coreutils) *but because of the fact that if you are careful enough*, **then it'll just work, and it will be fast**, as mentioned in this article [AWS shows Rust love at re:Invent: 10 times faster than Kotlin, one tenth the latency of Go](https://www.devclass.com/development/2025/12/08/aws-shows-rust-love-at-reinvent-10-times-faster-than-kotlin-one-tenth-the-latency-of-go/1728671). Yes, there is price to be paid in the form of some extra work (and frustrations) while using strings or objects getting out of scope / consumed earlier (as compared to any GC languages), but in the end, it's all worth it.

## So is Rust ready for the frontend yet?

Well, there are many options (*some more mature than others*) like:

- [Dioxus](https://dioxuslabs.com/) framework for building fullstack web, desktop, and mobile apps
- [Leptos](https://leptos.dev/) - a cutting-edge Rust framework for the modern web
- [gtk4-rs](https://gtk-rs.org/gtk4-rs/git/book/) - GUI development with Rust and GTK 4 (*desktop only, but cross-platform*)
- [topcoat](https://github.com/tokio-rs/topcoat) - a modular, batteries-included Rust framework for building full-stack apps (*the recent contender from* [tokio](https://tokio.rs/))
- [gpui](https://gpui.rs/) - the framework used to write the famous [Zed](https://zed.dev/) editor, and finally,
- [gpui-kit](https://gpui-kit.com/) - a comprehensive Rust desktop framework with a complete UI system, data tables, docking, charts, and a code editor

And this is where things get interesting 😊- although *gpui-kit* describes itself as a Rust **desktop** framework, the website (which of course runs in the browser) showcases all their controls running in the browser. It is also mentioned on the website that it is **Proven in production at Longbridge** with their [Longbridge Pro](https://longbridge.com/desktop/) product (FYI, Longbridge Group, is a financial technology company founded in Singapore in 2019).

### How and why gpui-kit is useful for this project?

When I started my career in **VB6**, it had fantastic UI controls (in-built) like datagrids and treeviews but after the advent of web development, it was all primarily downhill 😞 (w.r.t. time taken to build a fully functioning application, including the backend and the UI):

- more complexity with no type safety (of course JS, until TS came into the picture)
- then the framework tax (choose from one or the other frameworks)
- then choose your UI component stack (I don't know which framework comes with a built-in component stack)
- **the only thing I loved from the very early days was the hot reload feature**

And UI is where the action happens in this project, and for building great UIs, you need great UI components. If those are in-built then there is no problem, but if not, then you have to find a UI component toolkit that fits your needs. So when I look at a UI component toolkit, **there are the 2 controls I look for - a data-grid and a tree-view**. *If it does not have these then it does not pass my benchmark*. If it has these, then I look for charting / graphing controls and other stuff like docking etc. and [gpui-kit](https://gpui-kit.com/) has all these.

## How does it compare with Blazor

Of course, Blazor is more mature because it has been in the game longer. Historically, many companies have commercial / paid UI component toolkits for different MS stacks and same goes for Blazor too. And not only the paid ones, but it has excellent open-source options too (please read my earlier blog post if you are interested).

You may also compare [Compendium](https://www.codionics.com/Compendium/) (my earlier *portfolio* website built using C# Blazor) with [Rustume](https://www.codionics.com/rustume/) (built using Rust and gpui-kit) **and decide for yourselves**. You should observe:

- it's in Rust (the frontend! - so no JS tax)
- beautiful high level components in action - like sliders, dock, data-grids (with resizable columns), tree-view, bar-chart, footer etc.
- **a caveat** - gpui-kit draws everything on a `canvas` so don't expect to find `dom` elements (this is, in principle, the same approach as taken by Kotlin Web or Flutter) and so SEO is a problem - this matters if you have a public facing website but for all other purposes, it's fine

### The unexpected benefit

I decided to not use Cytoscape.js (with JS-interop and decided to build it using gpui-kit primitives), because until I started implementing the nodes-edges graph visualization, *I was mostly testing the application as a desktop application and used to test it in browser once the feature was nearing completion*. And that's when I realized that if I introduce Cytoscape or any other JS dependency, then I'll be limiting myself to the browser😉.

So now if I run:

```
cargo run
```

then it runs as a desktop application and if I run:

```
cargo +nightly build --lib --target wasm32-unknown-unknown --release
npm run dev
```
it runs as a web-app (in the browser).

**Sweet, right?** So on to my usual JS rant 😉and Rust (for the front-end) advocacy:

- **Please stop using JS as your primary language for the front-end work!** You have excellent and mature options to choose from - Kotlin, Flutter (though Dart is boring 🥱), C# (through Blazor WASM) and none other than Rust (*I've demonstrated the last 2*). 
- ***If you haven't started using Rust in your company yet, then you can start using it for the frontend work!*** and you can thank me later 😉
