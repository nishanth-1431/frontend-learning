# HTML Links

Links are the whole reason the web exists — they connect pages together. Without them, every page would be an island. The `<a>` tag (anchor tag) is how you create clickable links in HTML.

---

## Basic Link Syntax

```html
<a href="https://github.com/nishanth-1431">My GitHub Profile</a>
```

That's it. The `href` holds the destination, and the text between the tags is what the user clicks.

---

## Different Kinds of Links

### External Links

Point to a completely different website:

```html
<a href="https://github.com">GitHub</a>
<a href="https://stackoverflow.com">Stack Overflow</a>
```

### Internal Links

Point to another page in your own project:

```html
<a href="about.html">About Me</a>
<a href="projects/portfolio.html">My Portfolio</a>
```

### Bookmark Links (Jump Within the Same Page)

These jump to a specific section on the current page. You link to an `id` using `#`.

```html
<!-- The link -->
<a href="#contact-section">Jump to Contact</a>

<!-- Somewhere else on the page -->
<h2 id="contact-section">Contact Me</h2>
<p>Reach out at nishanth@example.com</p>
```

I use these all the time for table-of-contents style navigation on long pages.

### Email Links

Opens the user's email app with a pre-filled address:

```html
<a href="mailto:nishanth@example.com">Send me an email</a>
```

You can even pre-fill the subject and body:

```html
<a href="mailto:nishanth@example.com?subject=Hello&body=Hey, I saw your portfolio!">Email with subject</a>
```

### Phone Links

Lets mobile users tap to call:

```html
<a href="tel:+919876543210">Call me</a>
```

---

## Important Attributes

### `target` — Where the Link Opens

| Value | What Happens |
|-------|-------------|
| `_self` | Opens in the same tab (this is the default) |
| `_blank` | Opens in a new tab |

```html
<a href="https://github.com" target="_blank">GitHub (new tab)</a>
```

### `rel` — Security for External Links

When you use `target="_blank"`, the new page can technically access your page through `window.opener`. That's a security risk. Adding `rel="noopener noreferrer"` blocks that:

```html
<a href="https://github.com" target="_blank" rel="noopener noreferrer">GitHub</a>
```

I just made this a habit — whenever I use `target="_blank"`, I always add the `rel` attribute.

### `title` — Tooltip on Hover

```html
<a href="https://github.com" title="Go to my GitHub profile">GitHub</a>
```

Hovering over the link shows the title text as a small tooltip.

### `download` — Download Instead of Navigate

This tells the browser to download the linked file rather than opening it:

```html
<a href="resume.pdf" download>Download my resume</a>
```

You can also suggest a filename:

```html
<a href="resume.pdf" download="nishanth-resume-2025.pdf">Download Resume</a>
```

---

## Absolute vs Relative Paths

This tripped me up initially, so here's the simple version:

**Absolute** = full URL including `https://`. Used for external sites.
```html
<a href="https://stackoverflow.com/questions">Stack Overflow</a>
```

**Relative** = path relative to where the current file is. Used within your own project.
```html
<!-- Same folder -->
<a href="contact.html">Contact</a>

<!-- Subfolder -->
<a href="pages/about.html">About</a>

<!-- Go up one folder -->
<a href="../index.html">Back to Home</a>
```

My rule: external sites → absolute path. Internal pages → relative path.

---

## Using an Image as a Link

Wrap an `<img>` tag inside an `<a>` tag:

```html
<a href="https://github.com/nishanth-1431">
    <img src="github-icon.png" alt="Visit my GitHub profile">
</a>
```

Make sure the `alt` text describes where the link goes, not just what the image looks like.

---

## Link States (CSS Preview)

Browsers style links differently based on their state:

| State | Description | Default Look |
|-------|-------------|-------------|
| Unvisited | Haven't clicked yet | Blue, underlined |
| Visited | Already clicked | Purple, underlined |
| Hover | Mouse is over the link | Depends on browser |
| Active | Currently being clicked | Red (briefly) |

You can customize all of these with CSS later.

---

## Things I Remind Myself

- Write **descriptive link text**. "View the project documentation" is way better than "Click here" — it helps screen readers and SEO.
- Always add `rel="noopener noreferrer"` when using `target="_blank"`.
- Use relative paths for links within my own site, absolute for external links.
- Don't use `href="#"` as a placeholder — it scrolls to the top of the page and is confusing. Use a proper URL or a real `#id`.
- Links are keyboard-accessible by default (Tab to focus, Enter to activate). Don't break that.

---

## What I Took Away

- `<a>` with `href` creates hyperlinks — the backbone of web navigation.
- Links can go to external sites, internal pages, page sections, email apps, or phone dialers.
- `target="_blank"` opens in a new tab, but pair it with `rel="noopener noreferrer"`.
- `download` attribute triggers a file download instead of navigation.
- Descriptive link text matters for accessibility and SEO.

---

## Questions I Used to Test Myself

1. What's the difference between absolute and relative paths?
2. How do you make a link open in a new tab safely?
3. How do you create a jump-link to a section on the same page?
4. What does the `download` attribute do?
5. Why is "Click here" bad link text?

---

## Up Next

➡️ Images — the `<img>` tag, alt text, responsive images with `<picture>`.
