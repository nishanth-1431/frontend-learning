# HTML Best Practices

After going through all the HTML topics, I wanted to write down the patterns and habits I want to make automatic. These aren't rules someone else made up — they're things I noticed make my code cleaner, faster, and easier to come back to.

---

## 1. Always Start with the Full Boilerplate

I used to skip parts of it. Don't.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meaningful Page Title</title>
</head>
<body>
    <!-- Content -->
</body>
</html>
```

Every page needs: DOCTYPE, `lang` on `<html>`, charset, viewport, and a descriptive title.

---

## 2. Semantic Tags Over Div Soup

If HTML has a tag for it, use it. `<div>` is a last resort.

```html
<!-- This tells you nothing -->
<div class="header">
    <div class="nav">...</div>
</div>

<!-- This tells you everything -->
<header>
    <nav>...</nav>
</header>
```

I now ask myself: "Is there a semantic tag for this?" before reaching for `<div>`.

---

## 3. Headings in Order — No Skipping

```html
<!-- Wrong — jumped from h1 to h4 -->
<h1>Site Title</h1>
<h4>Some section</h4>

<!-- Right — sequential order -->
<h1>Site Title</h1>
<h2>Section</h2>
<h3>Sub-section</h3>
```

Headings aren't about font size (that's CSS's job). They're about document structure. One `<h1>` per page. Go in order.

---

## 4. Alt Text on Every Image

```html
<!-- Informative image -->
<img src="team.jpg" alt="Dev team brainstorming around a whiteboard">

<!-- Purely decorative -->
<img src="fancy-divider.png" alt="">
```

If the image conveys information, describe it. If it's decorative, use empty alt so screen readers skip it. Never write `alt="image"`.

---

## 5. Descriptive Link Text

```html
<!-- Bad -->
<a href="/report">Click here</a>
<a href="/report">Read more</a>

<!-- Good -->
<a href="/report">View the Q3 sales report</a>
```

Screen readers often list all links on a page. If they all say "Click here", that's useless.

---

## 6. Every Input Gets a Label

```html
<!-- Bad — no label, screen reader says "edit text" -->
<input type="text" placeholder="Name">

<!-- Good — screen reader says "Full Name: edit text" -->
<label for="name">Full Name:</label>
<input type="text" id="name" name="name">
```

Placeholder text is not a substitute for a label. Some screen readers don't read placeholders.

---

## 7. Consistent Indentation

Pick either 2 spaces or 4 spaces and stick with it. I use 4.

```html
<div>
    <h2>Section Title</h2>
    <p>Content goes here.</p>
</div>
```

Blank lines between major sections make things scannable. Properly indented code is so much easier to debug.

---

## 8. Lowercase Tags and Attributes

HTML is case-insensitive, but the convention is lowercase. It's cleaner and consistent with XHTML rules.

```html
<!-- Avoid -->
<DIV CLASS="container">
    <P>Text</P>
</DIV>

<!-- Use -->
<div class="container">
    <p>Text</p>
</div>
```

---

## 9. Close Every Tag

Browsers are forgiving — they'll often render unclosed tags correctly. But that's like driving without a seatbelt because you haven't crashed yet.

```html
<!-- Don't do this -->
<p>First paragraph
<p>Second paragraph

<!-- Do this -->
<p>First paragraph</p>
<p>Second paragraph</p>
```

Void elements (self-closing) don't need closing tags: `<br>`, `<hr>`, `<img>`, `<input>`, `<meta>`, `<link>`.

---

## 10. Comments That Explain Why, Not What

```html
<!-- Bad — states the obvious -->
<!-- This is a paragraph -->
<p>Hello World</p>

<!-- Good — explains the reasoning -->
<!-- Visually hidden but announced by screen readers -->
<span class="sr-only">Navigation menu</span>
```

---

## 11. Keep HTML, CSS, and JavaScript Separate

| File Type | Job |
|-----------|-----|
| `.html` | Structure |
| `.css` | Presentation |
| `.js` | Behavior |

```html
<!-- Avoid inline styles and event handlers -->
<p style="color: red; font-size: 20px;" onclick="alert('hi')">Text</p>

<!-- Use external files -->
<link rel="stylesheet" href="styles.css">
<script src="app.js"></script>
```

Separation makes code reusable, cacheable, and way easier to maintain. Multiple pages can share the same CSS and JS files.

---

## 12. Performance Habits

**Lazy load images below the fold:**
```html
<img src="photo.jpg" alt="Photo" loading="lazy">
```

**Set width and height to prevent layout shift:**
```html
<img src="photo.jpg" alt="Photo" width="400" height="300">
```

**Load CSS in `<head>`, scripts before `</body>`:**
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Content -->
    <script src="app.js"></script>
</body>
```

Or use `defer` to keep scripts in `<head>` without blocking page rendering:
```html
<script src="app.js" defer></script>
```

---

## 13. Validate Your Code

The W3C Validator catches mistakes I'd never notice by eye — unclosed tags, duplicate IDs, missing alt attributes, bad nesting.

🔗 [https://validator.w3.org/](https://validator.w3.org/)

I try to run my pages through it after finishing any major section.

---

## 14. SEO Basics

| Practice | How |
|----------|-----|
| One `<h1>` per page | Makes the main topic clear to search engines |
| Descriptive `<title>` | `<title>Learn HTML — Nishanth's Notes</title>` |
| Meta description | `<meta name="description" content="...">` |
| Alt text on images | Helps image search and accessibility |
| Clean URLs | `/html-notes` is better than `/page?id=47` |
| Semantic structure | `<main>`, `<article>`, `<nav>` |
| Canonical URL | `<link rel="canonical" href="...">` |

---

## 15. File and ID Naming Conventions

**Files** — lowercase, hyphens to separate words:
```
<!-- Do -->
about-us.html
contact-form.html

<!-- Don't -->
About Us.html
contactForm.html
page_1.html
```

**IDs and Classes** — lowercase, hyphens:
```html
<!-- Do -->
<div class="project-card" id="featured-project"></div>

<!-- Don't -->
<div class="Box1" id="MainDiv_1"></div>
```

---

## My Quick Checklist

| # | Practice |
|---|----------|
| 1 | Full HTML boilerplate on every page |
| 2 | Semantic tags over `<div>` |
| 3 | Heading hierarchy — no skipping |
| 4 | Alt text on every image |
| 5 | Descriptive link text |
| 6 | Labels on every form input |
| 7 | Consistent indentation |
| 8 | Lowercase tags and attributes |
| 9 | All tags properly closed |
| 10 | Comments explain why, not what |
| 11 | HTML, CSS, JS in separate files |
| 12 | Performance: lazy loading, defer scripts |
| 13 | Validate with W3C Validator |
| 14 | Basic SEO in every page |
| 15 | Consistent naming conventions |

---

## Questions I Used to Test Myself

1. Why use semantic HTML instead of `<div>` everywhere?
2. What's wrong with `alt="image"` on an image tag?
3. Why separate HTML, CSS, and JavaScript into different files?
4. What does `loading="lazy"` do?
5. Where should scripts go — head or body?
6. What naming convention should HTML files follow?
7. How do you validate HTML?

---

## Up Next

➡️ Mini Projects — apply everything in real pages.
