# Semantic HTML

For a while, I was wrapping everything in `<div>` tags and giving them class names like `"header"`, `"nav"`, `"footer"`. Then I learned that HTML already has dedicated tags for all of those — and using them properly makes a real difference for accessibility, SEO, and code readability.

Semantic HTML means using tags that **describe what the content is**, not just how it looks.

---

## Why Bother with Semantics?

| Benefit | What Happens |
|---------|-------------|
| **Accessibility** | Screen readers use semantic tags to build a page outline, letting blind users jump between sections quickly |
| **SEO** | Search engines prioritize content wrapped in meaningful tags over content buried in `<div>` soup |
| **Readability** | Other developers (and future me) can scan the code and immediately understand the page structure |
| **Maintainability** | Well-structured code is easier to modify and debug |

---

## The "Div Soup" Problem

Here's what my early code looked like:

```html
<div class="header">
    <div class="nav">
        <div class="link">Home</div>
        <div class="link">About</div>
    </div>
</div>
<div class="main-content">
    <div class="post">
        <div class="post-title">My First Blog Post</div>
        <div class="post-body">Content here...</div>
    </div>
</div>
<div class="footer">Copyright 2025</div>
```

And here's the same thing with semantic HTML:

```html
<header>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
    </nav>
</header>
<main>
    <article>
        <h2>My First Blog Post</h2>
        <p>Content here...</p>
    </article>
</main>
<footer>Copyright 2025</footer>
```

Same result on screen, but the second version is cleaner, more accessible, and better for SEO. Screen readers can actually navigate it.

---

## The Main Structural Tags

### `<header>` — Top of the Page or Section

```html
<header>
    <h1>My Portfolio</h1>
    <p>Java Full Stack Developer</p>
</header>
```

- Not the same as `<head>` (which holds metadata). `<header>` is visible content.
- You can have multiple headers — one for the page, one for each section or article.

### `<nav>` — Navigation Links

```html
<nav>
    <a href="/">Home</a>
    <a href="/projects">Projects</a>
    <a href="/contact">Contact</a>
</nav>
```

- Use for **major navigation blocks** only — not every random group of links.
- A page can have multiple `<nav>` elements (main nav, footer nav, sidebar nav).

### `<main>` — The Core Content

```html
<main>
    <h1>Welcome to My Blog</h1>
    <p>This is where all the main content lives.</p>
</main>
```

- Only **one `<main>`** per page.
- Don't nest it inside `<header>`, `<nav>`, `<footer>`, or `<aside>`.
- Everything that's unique to this page goes here.

### `<section>` — A Themed Group of Content

```html
<section>
    <h2>My Skills</h2>
    <p>HTML, CSS, JavaScript, Java, Spring Boot</p>
</section>

<section>
    <h2>My Projects</h2>
    <p>Portfolio site, blog layout, survey form...</p>
</section>
```

- Each section should generally have its own heading.
- Think of it like a chapter in a book — a thematic grouping.

### `<article>` — Independent, Self-Contained Content

```html
<article>
    <h2>How I Got Started with Web Development</h2>
    <p>It all started when I wanted to build a personal website...</p>
    <p>Published on August 28, 2025</p>
</article>
```

- An article should make sense **on its own** — if you pulled it out of the page and put it somewhere else, it should still work.
- Great for blog posts, news articles, product cards, comments, forum threads.

### `<section>` vs `<article>` — The Difference That Confused Me

| Tag | Use When |
|-----|----------|
| `<section>` | Content is a themed chunk that's part of a bigger page |
| `<article>` | Content is independent and could stand alone |

A blog page might have an `<article>` for each post, and each article might have `<section>` elements inside it for sub-topics.

### `<aside>` — Sidebar / Tangentially Related Content

```html
<aside>
    <h3>Related Articles</h3>
    <ul>
        <li><a href="#">Understanding CSS Grid</a></li>
        <li><a href="#">Getting Started with React</a></li>
    </ul>
</aside>
```

- For content that's related but not essential to the main content.
- Sidebars, pull quotes, author bios, related links, ads.

### `<footer>` — Bottom of the Page or Section

```html
<footer>
    <p>&copy; 2025 Nishanth P. All rights reserved.</p>
    <nav>
        <a href="/privacy">Privacy Policy</a>
        <a href="/terms">Terms</a>
    </nav>
</footer>
```

- Like `<header>`, you can have multiple footers (page footer, section footer, article footer).

---

## Other Semantic Tags I Found Useful

### `<figure>` and `<figcaption>`

```html
<figure>
    <img src="architecture.png" alt="Three-tier app architecture">
    <figcaption>Our application uses a standard three-tier architecture</figcaption>
</figure>
```

### `<details>` and `<summary>` — Collapsible Content (No JavaScript!)

```html
<details>
    <summary>What IDE should I use?</summary>
    <p>VS Code is great for frontend work. IntelliJ IDEA is better for Java and Spring Boot projects.</p>
</details>
```

This creates an expandable/collapsible section that works without a single line of JavaScript. Click the summary to toggle.

### `<time>` — Machine-Readable Dates

```html
<p>Published on <time datetime="2025-08-28">August 28, 2025</time></p>
```

The `datetime` attribute gives machines a standardized format while humans see a readable version.

### `<address>` — Contact Info

```html
<address>
    <p>Nishanth P</p>
    <a href="mailto:nishanth@example.com">nishanth@example.com</a><br>
    <a href="tel:+919876543210">+91 98765 43210</a>
</address>
```

### `<mark>` — Highlighted Text

```html
<p>The most important concept today was <mark>semantic HTML</mark>.</p>
```

---

## How a Semantic Page Layout Looks

```
┌─────────────────────────────────┐
│           <header>              │
│    Logo    <nav> Links </nav>   │
├─────────────────────────────────┤
│           <main>                │
│  ┌──────────────────┐ ┌──────┐ │
│  │   <article>      │ │<aside│ │
│  │   <section>      │ │      │ │
│  │   <section>      │ │      │ │
│  └──────────────────┘ └──────┘ │
├─────────────────────────────────┤
│           <footer>              │
│   Copyright   <nav> Links      │
└─────────────────────────────────┘
```

---

## All Semantic Elements at a Glance

| Element | What It Represents |
|---------|-------------------|
| `<header>` | Introductory content for the page or a section |
| `<nav>` | A group of navigation links |
| `<main>` | The primary content of the page (one per page) |
| `<section>` | A thematic grouping of content |
| `<article>` | Self-contained, independent content |
| `<aside>` | Content tangentially related to the main content |
| `<footer>` | Closing content for the page or a section |
| `<figure>` | An image, diagram, or code snippet with its caption |
| `<figcaption>` | Caption for a figure |
| `<details>` | Expandable/collapsible content |
| `<summary>` | The clickable heading for a details block |
| `<time>` | A date or time value |
| `<address>` | Contact information |
| `<mark>` | Highlighted or marked text |

---

## Things I Remind Myself

- Use semantic tags instead of `<div>` whenever a specific tag exists for the purpose.
- Only one `<main>` per page.
- `<section>` for themes, `<article>` for standalone content.
- Always give sections a heading.
- Use `<nav>` for important navigation, not every list of links.
- `<details>` + `<summary>` = free collapsible content without JavaScript.

---

## Questions I Used to Test Myself

1. What's wrong with wrapping everything in `<div>` tags?
2. How is `<header>` different from `<head>`?
3. When would you use `<article>` vs `<section>`?
4. Can you have more than one `<main>` on a page?
5. What does `<aside>` represent?
6. How does `<details>` work without JavaScript?
7. Why does semantic HTML help with SEO?

---

## Up Next

➡️ Meta Tags — charset, viewport, SEO tags, Open Graph for social media.
