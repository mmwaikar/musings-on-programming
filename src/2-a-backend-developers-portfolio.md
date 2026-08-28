# A Backend Developer's Portfolio

I have been meaning to write this post for a long time, and this whole time I used to wonder what would be a good title for this post? The 2 titles which came to my mind, and eventually stuck with me were:

- A Developer's Portfolio, and,
- A Portfolio for Developers

But then it struck me that adding *Backend* to the title makes it even more impactful, because that's what this ultimately is - a portfolio of a *backend* developer.

## A portfolio

When I first came across this term long ago (and most likely, it would have been in either films, or modelling or advertising context), I realized that it is such a nice way to share one's work. And then, after starting work as a software engineer, I saw this term being used for frontend developers - specially job openings asking for them to share their, so called portfolio or links to some of their interesting works. So this question becomes relevant - **what would a backend developer share?**

### Links to GitHub or LinkedIn profiles

Many job openings, not surprisingly, ask for your GitHub or LinkedIn profiles, but unfortunately, both of these are *text-only* or *text-first* mediums, and they don't have the same appeal as a pleasing visual medium, like a video, animation, or even a beautifully, colorful website. *The same is true for your blog site, or even to the links of your publications or books*.

### The visual part

So we are back to square one - at the very minimum, you need:

- a **website** if you have to share something with a wider audience
- and second, it has to be **visually pleasing**

### The solutions

[GitHub pages](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages) solve the first problem - *"you can use GitHub Pages to host a website about yourself, your organization, or your project directly from a repository on GitHub. GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website"*.

The key thing to note is the **static** part:

- it cannot run any server-side code
- it can only serve static assets
- any **dynamic** behavior comes from JavaScript running in the browser

### The whole conundrum

This is the problematic part - and where things get **interesting** or **complicating** depending on which camp you belong - **frontend** or **backend**? I should not compartmentalize developers in camps, but the fact is this -

- **A Frontend developer** is one who has only used JS (now TS too) or primarily started his or her career using JS and has either, never used any backend languages (specially, statically typed ones) or used backend languages sparingly - **in short, he or she loves JS**
- **A Backend developer** comes from the other side of the spectrum - he or she started using backend languages first and then had to learn the whole frontend landscape (HTML, CSS or JS) for practical reasons - **so, in short, their first love is not JS**

### The friction

The friction for a backend developer arises from the degree of their dislike for JS. For me, it's hate though 😉 - given a choice, I would want **to use either no JS, or the least amount possible**. So where does that leave me?

## WebAssembly

WebAssembly based solutions are a God-send for people like me and thanks to the developers, or companies who realize this, and take this effort forward. **It is entirely possible to do most of your stuff in a backend language of your choice and rely on JS as less as possible**. Rust is doing a lot for [WebAssembly](https://rust-lang.org/what/wasm/) and [Blazor](https://dotnet.microsoft.com/en-us/apps/aspnet/web-apps/blazor) has become a very mature and stable choice for doing frontend work using C#.

### So why Blazor?

Although, C# is not among the best of the backend languages, I have used it the longest in my career. **And for writing fullstack applications in the same language, the top 3 choices today are Rust, Kotlin and C#** - *with varying degrees of strengths / weaknesses in different areas*. And Blazor's advantages are:

- a mature solution (in the game for almost 8 years now)
- has multiple UI component libraries, both paid and Open-Source, like [MudBlazor](https://mudblazor.com/), [Radzen](https://blazor.radzen.com/), [Blazorise](https://blazorise.com/) and MS's own [Fluent UI Blazor library](https://www.fluentui-blazor.net/)
- **shared code** - unfortunately, developers or companies either do not realize this, or don't understand it's importance, but the very same domain objects, validation rules, business logic can be used across the spectrum (*not writing it twice*)

## The fun in JS part

So after all this reading, you must be thinking that there is no fun in JS, but interestingly, it is in:

- letting people who love JS do the hard work of writing excellent JS libs
- and then using those libs from a (backend) language of our choice 😎

So why am I even talking about JS? Because I used this library called [Cytoscape.js](https://js.cytoscape.org/) as part of my work. This is an excellent *"Graph theory (network) library for visualization and analysis"*. It is extremely simple to use - just hand over the data in a format it expects and it does the hard part of displaying it beautifully. After using it, I used to think of using it in personal contexts, like, maybe displaying a family tree or something similar.

### JSON Resume

I also came across this [JSON Resume](https://jsonresume.org/) website, which describes itself as *"The open-source initiative to create a JSON-based standard for resumes. For developers, by developers."*, and that's the format I've used for my resume.

## The end result

So let's see what all recipes have I used to create my portfolio:

- resume in **JSON Resume** format
- **C# Blazor** (the whole thing is mostly C#, with JS interop only for interacting with Cytoscape.js)
    - *MS Fluent UI Blazor components* (like side bar, header, footer etc.)
    - *MudBlazor* bar chart for displaying my experience (in number of months) in different companies
    - *Cytoscape.js* for displaying my experience:
        - *in companies grouped by countries*: so the first level shows countries I worked in, and when you expand that node, it shows companies for that country
        - *grouped by skills*: so the first level shows a skill (like C# or Agile) and when you click a skill node, it expands into details like frameworks or techniques for that particular skill

**So how does it even look like?** 😠 Well, if I have raised your curiosity even a little bit, then head over to [my portfolio](https://www.codionics.com/Compendium/) and if you want a similar one for yourself, then you can clone my [github repository](https://github.com/mmwaikar/Compendium) and replace my resume with yours, and boom 💥 you'll have your own portfolio (maybe not the prettiest, but much more pleasing than plain textual formats ☺️)

## To conclude

How can we not talk about the **big elephant** in the room called **AI**? I have vibe-coded this portfolio, entirely using GitHub Copilot 😇 - I wanted to do this for a long time, but to use a new technology (like Blazor was for me - I mean, I knew the basics, but not all the intricacies, and certainly not these component libraries) takes time, and to build something working, takes even more time. But thanks to AI, I was able to build this pretty quickly. Enjoy more and more of your fav-lang and less and less of JS 😉