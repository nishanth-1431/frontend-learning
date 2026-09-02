# HTML Quick Reference Cheatsheet

I made this to quickly look up tags and syntax without having to Google them every time. It covers the core structure, formatting, lists, links, forms, and semantics.

---

## 1. The Essential Boilerplate

Every HTML file I create starts with this exact structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    
    <!-- All visible content goes here -->

</body>
</html>
```

---

## 2. Text & Formatting

| Tag | What it does | Example usage |
|-----|--------------|---------------|
| `<h1>` to `<h6>` | Headings. `h1` is the main title. | `<h1>My Blog</h1>` |
| `<p>` | Standard paragraph block. | `<p>This is text.</p>` |
| `<strong>` | Semantic bold (important text). | `<strong>Warning!</strong>` |
| `<em>` | Semantic italics (emphasized text). | `I <em>really</em> mean it.` |
| `<br>` | Forced line break. | `First Line<br>Second Line` |
| `<hr>` | Thematic break (horizontal line). | `<hr>` |
| `<blockquote>` | A block-level quotation. | `<blockquote>To be or...</blockquote>` |
| `<pre>` | Pre-formatted text (keeps spaces). | `<pre>   indented   </pre>` |
| `<code>` | Inline code snippet. | `Use <code>let x = 5;</code>` |
| `<span>` | Generic inline container (for CSS). | `<span class="red">Hi</span>` |
| `<div>` | Generic block container (for layout). | `<div class="card">...</div>` |

---

## 3. Lists

**Unordered List (Bullet points)**
```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
</ul>
```

**Ordered List (Numbered)**
```html
<ol start="1" type="A">
    <li>Step One</li>
    <li>Step Two</li>
</ol>
```

**Description List (Terms and Definitions)**
```html
<dl>
    <dt>Frontend</dt>
    <dd>The part of the web the user sees.</dd>
</dl>
```

---

## 4. Links & Images

**Links (`<a>`)**
```html
<!-- External link (opens in new tab safely) -->
<a href="https://google.com" target="_blank" rel="noopener noreferrer">Google</a>

<!-- Internal link -->
<a href="/about.html">About Me</a>

<!-- Jump to section on same page -->
<a href="#footer-section">Jump to Footer</a>

<!-- Email link -->
<a href="mailto:nishanth@example.com">Email Me</a>
```

**Images (`<img>`)**
```html
<!-- Always include alt text for accessibility! -->
<img src="profile.jpg" alt="A photo of Nishanth" width="300" height="300" loading="lazy">
```

---

## 5. Semantic Structure

Stop using `<div>` for everything. Use these to outline the page:

| Tag | When to use it |
|-----|----------------|
| `<header>` | Top of page/section (logo, title, nav). |
| `<nav>` | Main navigation links. |
| `<main>` | The unique, primary content of the page (only one per page). |
| `<article>` | A standalone piece of content (a blog post, a news story). |
| `<section>` | A thematic grouping of content, usually with a heading. |
| `<aside>` | Sidebars or related content that isn't the main focus. |
| `<footer>` | Bottom of page/section (copyright, links). |

---

## 6. Tables

A standard table with headers, body, and an accessible scope.

```html
<table>
    <caption>My Study Schedule</caption>
    <thead>
        <tr>
            <th scope="col">Day</th>
            <th scope="col">Topic</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Monday</td>
            <td>HTML Forms</td>
        </tr>
    </tbody>
</table>
```
*Note: Use `colspan="2"` to span across columns, and `rowspan="2"` to span across rows.*

---

## 7. Forms & Inputs

**The Form Shell**
```html
<form action="/submit-endpoint" method="POST">
    <!-- inputs go here -->
</form>
```

**Labels and Inputs (Crucial pairing)**
```html
<!-- The 'for' attribute must match the input's 'id' -->
<label for="username">Username:</label>
<input type="text" id="username" name="username" required>
```

**Common Input Types**
- `<input type="text">`: Normal text
- `<input type="email">`: Validates for '@'
- `<input type="password">`: Hides characters
- `<input type="number" min="1" max="10">`: Number spinner
- `<input type="date">`: Date picker
- `<input type="checkbox">`: Multiple choices
- `<input type="radio">`: Single choice (group them by using the same `name` attribute)

**Dropdowns (`<select>`)**
```html
<select name="branch" id="branch">
    <option value="cse">Computer Science</option>
    <option value="mech">Mechanical</option>
</select>
```

**Text Areas (Multi-line)**
```html
<textarea name="bio" rows="4" cols="50"></textarea>
```

---

## 8. Meta Tags & Head Elements

Stuff that goes inside `<head>` to control SEO, responsiveness, and links.

```html
<!-- Character encoding (fixes weird symbols) -->
<meta charset="UTF-8">

<!-- Makes the site responsive on mobile -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- SEO basics -->
<title>My Portfolio</title>
<meta name="description" content="Nishanth's dev portfolio.">

<!-- Linking external CSS -->
<link rel="stylesheet" href="style.css">
```

---

## 9. Accessibility (a11y) Quick Checks

1. **Images:** Does every `<img>` have an `alt` attribute? (Use `alt=""` if decorative).
2. **Forms:** Does every `<input>` have an associated `<label>`?
3. **Headings:** Do headings go in order? (`h1` -> `h2` -> `h3`, no skipping).
4. **Keyboard:** Can you navigate the page using only the `Tab` key?
5. **Semantics:** Did you use `<button>` instead of a clickable `<div>`?

---

*This cheatsheet acts as my quick reference. For deep dives, I check the specific topic folders.*
