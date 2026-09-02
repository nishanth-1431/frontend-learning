# HTML Meta Tags

Meta tags sit inside `<head>` and are invisible to the user — but they're incredibly important behind the scenes. They tell browsers how to render the page, tell search engines what the page is about, and tell social media platforms how to display your link when someone shares it.

I initially skipped these entirely and only went back to learn them properly when I realized how much they affect SEO and mobile responsiveness.

---

## `<meta charset="UTF-8">`

```html
<meta charset="UTF-8">
```

This tells the browser what character encoding to use. **UTF-8** covers basically every character you'll ever need — English, Tamil, Hindi, Japanese, emojis, mathematical symbols, everything.

Without it, special characters might show up as garbled text or question marks. Always put this first inside `<head>`.

---

## `<meta name="viewport">` — Making Pages Work on Mobile

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This is the one that makes your site **responsive on phones and tablets**. Without it, mobile browsers render the page at desktop width and then shrink it down, making everything tiny and unreadable.

| Property | What It Does |
|----------|-------------|
| `width=device-width` | Makes the page width match the device screen width |
| `initial-scale=1.0` | Sets the starting zoom level to 100% |

If I had to pick only two meta tags to remember, it'd be charset and viewport. Everything else is optional — these two are not.

---

## SEO Meta Tags

### Page Description

```html
<meta name="description" content="Personal notes and code examples from learning HTML as part of my Java full stack journey.">
```

This is what shows up in search results below your page title. Keep it:
- Between **150-160 characters**
- Descriptive and specific to the page
- Unique for every page (don't copy-paste the same description everywhere)

### Author

```html
<meta name="author" content="Nishanth P">
```

Simply identifies who wrote the page.

### Keywords (Mostly Outdated)

```html
<meta name="keywords" content="HTML, frontend, web development, learning notes">
```

Google officially said they **don't use this for ranking** anymore. Some other search engines might still look at it, but I wouldn't stress about it.

### Robots — Controlling Search Engine Crawlers

```html
<meta name="robots" content="index, follow">
```

This tells search engines whether to include your page in results and whether to follow the links on it.

| Value | What It Means |
|-------|-------------|
| `index` | Go ahead and include this page in search results |
| `noindex` | Don't show this page in search results |
| `follow` | Follow the links on this page |
| `nofollow` | Don't follow the links |

Common combos:
```html
<!-- Normal page — show it, follow its links (this is the default) -->
<meta name="robots" content="index, follow">

<!-- Private page — hide from search results entirely -->
<meta name="robots" content="noindex, nofollow">
```

---

## Open Graph — How Your Link Looks on Social Media

When you share a URL on WhatsApp, LinkedIn, Facebook, or Discord, the preview card that shows up is controlled by Open Graph tags.

```html
<meta property="og:title" content="Learning HTML — My Notes">
<meta property="og:description" content="Personal notes from learning HTML as part of full stack development.">
<meta property="og:image" content="https://my-site.com/images/html-notes-preview.png">
<meta property="og:url" content="https://my-site.com/html-notes">
<meta property="og:type" content="website">
```

| Property | Controls |
|----------|---------|
| `og:title` | The headline on the preview card |
| `og:description` | The description text below the headline |
| `og:image` | The preview image |
| `og:url` | The canonical URL shown on the card |
| `og:type` | Type of content (`website`, `article`, `profile`, etc.) |

Without these, social platforms try to guess what to show — and they usually guess badly.

---

## Twitter Card Tags

Twitter (X) uses its own set of meta tags for link previews, though it'll fall back to Open Graph if these aren't present.

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Learning HTML — My Notes">
<meta name="twitter:description" content="Personal notes from learning HTML.">
<meta name="twitter:image" content="https://my-site.com/images/preview.png">
```

| Value for `twitter:card` | What It Shows |
|--------------------------|--------------|
| `summary` | Small card with a thumbnail |
| `summary_large_image` | Large card with a big image |

---

## `<meta http-equiv>` — Simulating HTTP Headers

### Auto-Refresh or Redirect

```html
<!-- Refresh the page every 60 seconds -->
<meta http-equiv="refresh" content="60">

<!-- Redirect to another URL after 3 seconds -->
<meta http-equiv="refresh" content="3;url=https://my-new-site.com">
```

I wouldn't use redirect this way in a real project (server-side redirects are better), but it's good to know it exists.

### IE Compatibility

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

Tells Internet Explorer to use the latest rendering engine. Mostly irrelevant now since IE is dead, but you'll still see it in older templates.

---

## Favicon — That Tiny Icon in the Browser Tab

```html
<link rel="icon" type="image/x-icon" href="/favicon.ico">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```

The favicon appears next to your page title in the browser tab, in bookmarks, and on mobile home screens. It's a small thing, but it makes your site look polished and professional.

---

## Canonical URL — Avoiding Duplicate Content

```html
<link rel="canonical" href="https://my-site.com/html-notes">
```

If the same page is accessible from multiple URLs (like `my-site.com/html-notes` and `my-site.com/html-notes?ref=twitter`), the canonical tag tells search engines which one is the "real" URL. This prevents duplicate content penalties.

---

## What a Complete `<head>` Looks Like

Here's a template I've started using for my projects:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>HTML Notes — Nishanth P</title>
    <meta name="description" content="Personal learning notes on HTML covering structure, forms, accessibility, and more.">
    <meta name="author" content="Nishanth P">
    <meta name="robots" content="index, follow">

    <meta property="og:title" content="HTML Notes — Nishanth P">
    <meta property="og:description" content="Personal learning notes on HTML.">
    <meta property="og:image" content="https://my-site.com/images/preview.png">
    <meta property="og:url" content="https://my-site.com/html-notes">
    <meta property="og:type" content="website">

    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="HTML Notes — Nishanth P">

    <link rel="icon" href="/favicon.ico">
    <link rel="canonical" href="https://my-site.com/html-notes">
    <link rel="stylesheet" href="styles.css">
</head>
```

---

## Things I Remind Myself

- Always include `charset` and `viewport` — they're non-negotiable.
- Write a unique `<title>` and `<meta description>` for every page.
- Add Open Graph tags before sharing links on social media — the preview matters.
- Use a favicon for a polished look.
- Set `<meta name="robots">` if you need to hide a page from search engines.
- Use `canonical` if the same content lives at multiple URLs.

---

## Questions I Used to Test Myself

1. What happens if you skip `<meta charset="UTF-8">`?
2. Why does the viewport meta tag matter for mobile?
3. Where does the meta description show up?
4. What are Open Graph tags used for?
5. How do you hide a page from search engine results?
6. What's a canonical URL and why does it matter?
7. What's a favicon?

---

## Up Next

➡️ Accessibility — ARIA attributes, keyboard navigation, making websites usable for everyone.
