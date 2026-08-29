# HTML Images

Images make web pages come alive. Without them, the web would just be walls of text. HTML gives you several ways to add and control images, from basic embedding to responsive techniques that serve different images based on screen size.

---

## The `<img>` Tag

This is the bread and butter of images in HTML. It's a self-closing tag — no `</img>` needed.

```html
<img src="profile-photo.jpg" alt="Nishanth smiling at the camera">
```

Two attributes are considered essential:

- **`src`** — the file path or URL of the image
- **`alt`** — a text description of the image (more on why this matters below)

---

## Why `alt` Text is Non-Negotiable

I used to skip `alt` text thinking it was optional. Then I learned how important it actually is:

| Reason | What Happens |
|--------|-------------|
| **Accessibility** | Screen readers read the alt text aloud to blind users. Without it, the image is invisible to them. |
| **Broken images** | If the image fails to load (bad URL, slow network), the alt text shows up in its place. |
| **SEO** | Search engines can't "see" images. They rely on alt text to understand what the image contains. |

### Writing Good Alt Text

The key is to describe what the image *communicates*, not just what it literally shows.

```html
<!-- Informative image — describe the content -->
<img src="team-meeting.jpg" alt="Five developers discussing a project around a whiteboard">

<!-- Decorative image — use empty alt so screen readers skip it -->
<img src="decorative-border.png" alt="">

<!-- Image acting as a link — describe the destination -->
<a href="/dashboard">
    <img src="dashboard-icon.png" alt="Go to the admin dashboard">
</a>
```

If an image is purely decorative (a background pattern, a divider line), use `alt=""` — not `alt="image"` or `alt="decoration"`.

---

## Setting Dimensions

```html
<img src="photo.jpg" alt="Sunset from Marina Beach" width="500" height="350">
```

Setting `width` and `height` is actually important for performance — it lets the browser **reserve space** for the image before it loads. Without these, the page layout jumps around as images pop in. That jumping is called **Cumulative Layout Shift**, and it's a bad user experience.

---

## Lazy Loading

If you have lots of images on a page, loading all of them at once slows things down. Lazy loading tells the browser: "don't load this image until the user scrolls near it."

```html
<img src="photo.jpg" alt="Beach sunset" width="500" height="350" loading="lazy">
```

| Value | What Happens |
|-------|-------------|
| `eager` | Load immediately (default behavior) |
| `lazy` | Load only when the image is about to come into view |

I use `loading="lazy"` on every image that isn't visible when the page first loads.

---

## Image Paths

Just like links, images can use relative or absolute paths:

```html
<!-- Same folder as the HTML file -->
<img src="photo.jpg" alt="Photo">

<!-- Inside a subfolder -->
<img src="images/photo.jpg" alt="Photo">

<!-- Up one directory level -->
<img src="../photo.jpg" alt="Photo">

<!-- Full URL (external image) -->
<img src="https://example.com/images/banner.jpg" alt="Banner">
```

For your own project images, always use relative paths.

---

## `<figure>` and `<figcaption>`

If you want to pair an image with a caption, wrap them in `<figure>`:

```html
<figure>
    <img src="architecture-diagram.png" alt="Three-tier architecture showing frontend, backend, and database layers">
    <figcaption>Our application architecture — a standard three-tier setup</figcaption>
</figure>
```

This creates a semantic connection between the image and its caption. Screen readers and search engines understand they belong together. Without `<figure>`, a caption is just a random paragraph sitting near an image.

---

## Responsive Images with `<picture>`

Different screen sizes need different images. A massive desktop banner looks terrible squeezed onto a phone screen. The `<picture>` element lets you serve different images based on viewport width.

```html
<picture>
    <source media="(min-width: 900px)" srcset="banner-large.jpg">
    <source media="(min-width: 500px)" srcset="banner-medium.jpg">
    <img src="banner-small.jpg" alt="Welcome banner for the portfolio site">
</picture>
```

The browser checks each `<source>` from top to bottom. The first one whose `media` query matches gets used. If none match, the `<img>` tag acts as a fallback.

---

## `srcset` for Resolution Switching

If you have the same image in different resolutions (for retina vs regular screens), use `srcset` on the `<img>` tag itself:

```html
<img
    src="photo-small.jpg"
    srcset="photo-small.jpg 480w, photo-medium.jpg 960w, photo-large.jpg 1440w"
    sizes="(max-width: 600px) 480px, (max-width: 1000px) 960px, 1440px"
    alt="Chennai skyline at dusk"
>
```

The `srcset` tells the browser which files are available and how wide each one is. The `sizes` tells it what display size to target at each viewport width. The browser picks the best match automatically.

---

## Image Formats — Which One to Use

| Format | Best For | Supports Transparency | Supports Animation |
|--------|----------|----------------------|-------------------|
| JPEG | Photographs, complex images | No | No |
| PNG | Screenshots, graphics with transparency | Yes | No |
| GIF | Simple animations, tiny icons | Yes (limited) | Yes |
| SVG | Icons, logos, illustrations (scales perfectly) | Yes | Yes (via CSS/JS) |
| WebP | Modern replacement for JPEG and PNG (smaller files) | Yes | Yes |

My go-to choices:
- **Photos** → JPEG (or WebP if browser support isn't a concern)
- **Logos and icons** → SVG
- **Screenshots** → PNG
- **Anything that needs transparency** → PNG or WebP

---

## Things I Remind Myself

- Never skip the `alt` attribute. For decorative images, use `alt=""`.
- Set `width` and `height` to prevent layout shift.
- Use `loading="lazy"` for images below the fold.
- Use `<figure>` + `<figcaption>` when an image needs a caption.
- Choose the right format — SVG for icons, JPEG for photos, PNG for screenshots.
- Use `<picture>` or `srcset` when you need responsive images.
- Keep image file sizes small — compress before uploading.

---

## What I Took Away

- The `<img>` tag needs `src` and `alt` at minimum.
- Alt text is crucial for accessibility, SEO, and handling broken images.
- `<figure>` semantically pairs an image with its caption.
- `<picture>` serves different images based on screen size.
- `srcset` handles resolution switching for the same image.
- Choosing the right image format matters for performance.

---

## Questions I Used to Test Myself

1. Why is `alt` text important? When would you leave it empty?
2. What's the benefit of setting `width` and `height` on images?
3. How does `loading="lazy"` improve performance?
4. What's the difference between `<figure>` and a plain `<img>`?
5. When would you use `<picture>` instead of a regular `<img>`?
6. Which image format would you pick for a logo? For a photo?

---

## Up Next

➡️ Tables — rows, columns, spanning, and making tables accessible.
