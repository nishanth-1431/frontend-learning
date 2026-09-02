# HTML Accessibility

Accessibility (often shortened to **a11y** — the "11" is the number of letters between "a" and "y") is about making websites usable by everyone, including people who are blind, deaf, have limited mobility, or have cognitive differences.

I'll be honest — I didn't think much about accessibility at first. But then I learned that roughly 15% of the world's population has some form of disability, and in many countries, web accessibility is a legal requirement. More importantly, accessible websites are just better-designed websites.

---

## Who Benefits from Accessibility?

| Type of Disability | Examples | How We Help |
|-------------------|----------|-------------|
| Visual | Blindness, low vision, color blindness | Screen readers, alt text, high contrast |
| Auditory | Deafness, hearing difficulty | Captions, transcripts |
| Motor | Limited hand movement, tremors, paralysis | Keyboard navigation, large click targets |
| Cognitive | Dyslexia, ADHD, memory issues | Simple language, clear layout, consistent navigation |

The thing is, accessibility improvements help everyone — keyboard navigation is useful for power users, captions help people in noisy environments, and clear layouts benefit everyone.

---

## WCAG — The Standard

WCAG (Web Content Accessibility Guidelines) is the international standard. It's built on four principles, remembered as **POUR**:

| Principle | What It Means |
|-----------|-------------|
| **Perceivable** | Users must be able to perceive the content (see it, hear it, or feel it) |
| **Operable** | Users must be able to interact with it (click, type, navigate) |
| **Understandable** | Content and interface must be easy to understand |
| **Robust** | Content must work with current and future assistive technologies |

WCAG has three conformance levels:
- **A** — bare minimum
- **AA** — the standard most organizations aim for
- **AAA** — the gold standard (very strict)

---

## Start with Semantic HTML

This is the single biggest thing you can do for accessibility. Screen readers rely on HTML tags to build an outline of the page.

```html
<!-- Screen reader has no idea what these are -->
<div class="header">
    <div class="nav">Menu</div>
</div>

<!-- Screen reader announces: "Banner", "Navigation" -->
<header>
    <nav>Menu</nav>
</header>
```

A screen reader user can press a keyboard shortcut to jump between headings, navigate to the nav section, skip to the main content — but only if you're using the right tags.

### What Screen Readers Announce for Semantic Tags

| Element | Announced As |
|---------|-------------|
| `<header>` | "Banner" |
| `<nav>` | "Navigation" |
| `<main>` | "Main" |
| `<footer>` | "Content info" |
| `<article>` | "Article" |
| `<aside>` | "Complementary" |
| `<h1>` to `<h6>` | "Heading level 1" through "Heading level 6" |

---

## Alt Text for Images

I covered this in the Images section, but it's worth repeating since it's critical for accessibility.

```html
<!-- Informative — describe what the image communicates -->
<img src="team.jpg" alt="Four developers collaborating around a whiteboard during a sprint planning session">

<!-- Decorative — empty alt so screen readers skip it -->
<img src="squiggly-line.png" alt="">

<!-- Image that's a link — describe the destination -->
<a href="/dashboard">
    <img src="dashboard-icon.png" alt="Go to the admin dashboard">
</a>
```

Never use `alt="image"` or `alt="photo"` — that tells the user nothing.

---

## Making Forms Accessible

### Always Use Labels

```html
<!-- Bad — screen reader just says "edit text" with no context -->
<input type="text" placeholder="Name">

<!-- Good — screen reader says "Name: edit text" -->
<label for="name">Name:</label>
<input type="text" id="name" name="name">
```

### Group Related Fields

```html
<fieldset>
    <legend>Shipping Address</legend>
    <label for="street">Street:</label>
    <input type="text" id="street" name="street">

    <label for="city">City:</label>
    <input type="text" id="city" name="city">
</fieldset>
```

The `<legend>` gives screen reader users context about what the group of fields is for.

### Describing Errors

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email" aria-describedby="email-error" required>
<span id="email-error" role="alert">Please enter a valid email address.</span>
```

`aria-describedby` links the input to its error message, so the screen reader reads both the label and the error.

---

## ARIA — When HTML Isn't Enough

ARIA (Accessible Rich Internet Applications) attributes fill in the gaps when semantic HTML alone can't communicate what an element does.

**The golden rule of ARIA:** Don't use ARIA if a native HTML element already does the job. A `<button>` is always better than a `<div role="button">`.

### The Most Useful ARIA Attributes

| Attribute | What It Does | Example |
|-----------|-------------|---------|
| `role` | Tells screen readers what the element is | `role="navigation"` |
| `aria-label` | Gives an accessible name when there's no visible text | `aria-label="Close dialog"` |
| `aria-labelledby` | Points to another element that serves as the label | `aria-labelledby="section-heading"` |
| `aria-describedby` | Points to an element that provides additional description | `aria-describedby="help-text"` |
| `aria-hidden` | Hides an element from screen readers | `aria-hidden="true"` |
| `aria-required` | Indicates a required field | `aria-required="true"` |
| `aria-expanded` | Shows whether something is expanded or collapsed | `aria-expanded="false"` |
| `aria-live` | Announces dynamic content changes | `aria-live="polite"` |

### `aria-label` — Naming Elements Without Visible Text

```html
<button aria-label="Close this dialog">✕</button>
```

Without `aria-label`, the screen reader would just say "button, X" — confusing. With it, it says "button, Close this dialog."

```html
<nav aria-label="Main navigation">...</nav>
<nav aria-label="Footer links">...</nav>
```

When you have multiple `<nav>` elements, `aria-label` distinguishes them.

### `aria-hidden` — Hiding Decorative Stuff

```html
<span aria-hidden="true">🔍</span>
<span>Search</span>
```

The magnifying glass emoji is decorative — the word "Search" is what matters. `aria-hidden="true"` tells screen readers to skip the emoji.

### `aria-live` — Announcing Dynamic Updates

```html
<div aria-live="polite">
    <!-- When this content changes, screen readers announce it -->
    <p>You have 5 new notifications</p>
</div>
```

| Value | When It Announces |
|-------|------------------|
| `polite` | Waits until the user is idle |
| `assertive` | Announces immediately, interrupting whatever the user is doing |
| `off` | Doesn't announce |

---

## Keyboard Navigation

A lot of users can't use a mouse — they navigate entirely with the keyboard. This includes blind users, users with motor disabilities, and power users who just prefer the keyboard.

### Default Keyboard Behavior

| Key | What It Does |
|-----|-------------|
| `Tab` | Moves to the next interactive element (link, button, input) |
| `Shift + Tab` | Moves to the previous interactive element |
| `Enter` | Activates a link or button |
| `Space` | Toggles a checkbox or activates a button |
| Arrow keys | Navigates within components (radio groups, menus) |

By default, only interactive elements (`<a>`, `<button>`, `<input>`, `<select>`, `<textarea>`) are focusable.

### Making Other Elements Focusable

```html
<div tabindex="0">This div can now receive keyboard focus</div>
```

| tabindex Value | Behavior |
|---------------|----------|
| `0` | Focusable in the normal tab order |
| `-1` | Focusable via JavaScript, but not via Tab key |
| Positive numbers | Custom tab order (avoid this — it breaks the natural flow) |

---

## Skip Links

When a keyboard user lands on a page, they have to Tab through the entire navigation before reaching the main content. A skip link lets them jump straight there.

```html
<a href="#main-content" class="skip-link">Skip to main content</a>

<nav>
    <!-- Long navigation menu -->
</nav>

<main id="main-content">
    <!-- Content starts here -->
</main>
```

The CSS hides the skip link until it's focused:

```css
.skip-link {
    position: absolute;
    top: -50px;
    left: 10px;
    background: #000;
    color: #fff;
    padding: 10px;
    z-index: 1000;
}
.skip-link:focus {
    top: 0;
}
```

Press Tab when you first load a page — if a "Skip to main content" link appears, that's a sign the developers thought about accessibility.

---

## Color Contrast

Text needs enough contrast against its background to be readable. WCAG defines minimum ratios:

| Level | Normal Text | Large Text (18px+ or 14px+ bold) |
|-------|-------------|----------------------------------|
| AA | 4.5:1 | 3:1 |
| AAA | 7:1 | 4.5:1 |

Also important: **never use color alone to convey information**. If an error message is just red text with no other indicator, color-blind users won't notice it. Add an icon, bold text, or a text prefix like "Error:" alongside the color.

---

## Focus Styles

Never remove focus outlines without providing a replacement. The outline is how keyboard users know which element is currently active.

```css
/* Bad — removes focus indicator entirely */
*:focus {
    outline: none;
}

/* Good — custom focus style that's visible */
*:focus {
    outline: 2px solid #3498db;
    outline-offset: 2px;
}
```

---

## My Accessibility Checklist

| Area | What to Check |
|------|--------------|
| Images | Every `<img>` has meaningful `alt` (or `alt=""` for decorative) |
| Headings | Proper hierarchy — `h1` → `h2` → `h3`, no skipping |
| Forms | Every input has an associated `<label>` |
| Links | Descriptive text (not "click here") |
| Keyboard | Everything works without a mouse |
| Color | 4.5:1 contrast ratio, info not conveyed by color alone |
| ARIA | Used only when semantic HTML isn't enough |
| Focus | Visible focus styles on all interactive elements |
| Skip Links | Skip link available for keyboard users |
| Language | `lang` attribute set on `<html>` |

---

## Things I Remind Myself

- Semantic HTML is the foundation — get that right first, then add ARIA only where needed.
- Every image needs alt text. Decorative images get `alt=""`.
- Every form input needs a label.
- Test with the keyboard — can I navigate, interact with, and use every feature without touching the mouse?
- Test with a screen reader if possible (NVDA on Windows, VoiceOver on Mac).
- Use Lighthouse in Chrome DevTools to audit accessibility.
- Color contrast matters. Use a contrast checker tool.
- Never remove focus styles without adding a visible alternative.

---

## Questions I Used to Test Myself

1. What does a11y stand for?
2. What are the four WCAG principles?
3. Why is semantic HTML the foundation of accessibility?
4. When should you use ARIA attributes?
5. What's the golden rule of ARIA?
6. How do skip links help keyboard users?
7. What's the minimum contrast ratio for WCAG AA?
8. How do you make a `<div>` focusable with the keyboard?

---

## Up Next

➡️ Best Practices — clean code, performance, validation, and SEO tips.
