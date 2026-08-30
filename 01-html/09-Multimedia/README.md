# HTML Multimedia

Before HTML5, if you wanted audio or video on a page, you needed third-party plugins like Flash. Now HTML handles it natively with `<audio>`, `<video>`, and `<iframe>` — no plugins, no dependencies.

---

## `<audio>` — Playing Sound

The `<audio>` tag lets you embed audio directly into a page.

```html
<audio controls>
    <source src="podcast-episode.mp3" type="audio/mpeg">
    <source src="podcast-episode.ogg" type="audio/ogg">
    Sorry, your browser doesn't support audio playback.
</audio>
```

Without the `controls` attribute, the audio player is invisible and the user has no way to interact with it.

### Audio Attributes I Actually Use

| Attribute | What It Does |
|-----------|-------------|
| `controls` | Shows play/pause, volume, and progress bar |
| `autoplay` | Starts playing as soon as the page loads (avoid this — it's annoying) |
| `loop` | Restarts the audio when it ends |
| `muted` | Starts the audio in muted state |
| `preload` | Tells the browser how much to load upfront (`auto`, `metadata`, or `none`) |

### Why Multiple `<source>` Tags?

Not every browser supports every audio format. By providing multiple sources, the browser picks the first one it understands.

| Format | MIME Type | Notes |
|--------|-----------|-------|
| MP3 | `audio/mpeg` | Works in all modern browsers — safest choice |
| OGG | `audio/ogg` | Good for open-source projects, not supported in Safari |
| WAV | `audio/wav` | High quality but large files, supported everywhere |

The text between the tags ("Sorry, your browser...") only shows up if the browser doesn't support `<audio>` at all — which is rare these days, but still good practice.

---

## `<video>` — Playing Video

Works almost exactly like `<audio>`, with a few extra options.

```html
<video controls width="640" height="360">
    <source src="project-demo.mp4" type="video/mp4">
    <source src="project-demo.webm" type="video/webm">
    Your browser doesn't support video playback.
</video>
```

### Video-Specific Attributes

| Attribute | What It Does |
|-----------|-------------|
| `controls` | Play/pause, volume, fullscreen button |
| `width` / `height` | Sets the player dimensions |
| `poster` | Shows a thumbnail image before the user clicks play |
| `autoplay` | Starts playing immediately (browsers often block this unless `muted` is also set) |
| `loop` | Replays when it ends |
| `muted` | Starts muted |
| `preload` | How much to load upfront |

### The `poster` Attribute

This one is underrated. Without a poster, the video shows a blank frame or whatever the first frame happens to be. With a poster, you control what the user sees before hitting play.

```html
<video controls width="640" height="360" poster="demo-thumbnail.jpg">
    <source src="project-demo.mp4" type="video/mp4">
</video>
```

### Video Formats

| Format | MIME Type | Notes |
|--------|-----------|-------|
| MP4 | `video/mp4` | Universal support — use this as your primary format |
| WebM | `video/webm` | Smaller files, supported by Chrome, Firefox, Edge |
| OGG | `video/ogg` | Limited support, not common anymore |

Always include MP4 as the first source — it's the safest bet.

### A Gotcha About Autoplay

Browsers have gotten strict about autoplay. Most of them block it unless the video is also muted. So if you absolutely need autoplay (like a background video), do this:

```html
<video autoplay muted loop>
    <source src="background-loop.mp4" type="video/mp4">
</video>
```

But honestly, I try to avoid autoplay. Let users decide when to play.

---

## `<track>` — Subtitles and Captions

You can add text tracks to audio or video elements for subtitles, captions, and descriptions.

```html
<video controls width="640" height="360">
    <source src="tutorial.mp4" type="video/mp4">
    <track src="subtitles-en.vtt" kind="subtitles" srclang="en" label="English" default>
    <track src="subtitles-ta.vtt" kind="subtitles" srclang="ta" label="Tamil">
</video>
```

The subtitle files use the WebVTT format (`.vtt` extension).

| Kind | Purpose |
|------|---------|
| `subtitles` | Translation of dialogue for different languages |
| `captions` | Includes dialogue AND sound descriptions (for deaf/hard-of-hearing users) |
| `descriptions` | Text descriptions of visual content |
| `chapters` | Chapter markers for navigation |

---

## `<iframe>` — Embedding External Content

An `<iframe>` loads another webpage inside your page. It's how YouTube embeds, Google Maps, and code playgrounds work.

### Embedding a YouTube Video

When you click "Share → Embed" on YouTube, it gives you an iframe code. It looks something like this:

```html
<iframe
    width="560"
    height="315"
    src="https://www.youtube.com/embed/dQw4w9WgXcQ"
    title="Video about web development"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
></iframe>
```

### Embedding Google Maps

Similar concept — Google Maps gives you an embed code when you click "Share → Embed a map":

```html
<iframe
    src="https://www.google.com/maps/embed?pb=!1m18!..."
    width="600"
    height="400"
    style="border: 0;"
    allowfullscreen
    loading="lazy"
    title="Map showing Chennai, Tamil Nadu"
></iframe>
```

### Attributes Worth Knowing

| Attribute | What It Does |
|-----------|-------------|
| `src` | URL of the page to embed |
| `width` / `height` | Size of the iframe |
| `title` | Accessible description (screen readers use this) |
| `allowfullscreen` | Lets the embedded content go fullscreen |
| `loading` | `lazy` delays loading until the user scrolls near it |
| `sandbox` | Restricts what the embedded page can do |

### Security with `sandbox`

If you're embedding untrusted content, `sandbox` restricts what it can do:

```html
<iframe src="https://some-third-party.com" sandbox="allow-scripts" title="Third party widget"></iframe>
```

| Sandbox Value | What It Allows |
|---------------|---------------|
| `allow-scripts` | JavaScript execution |
| `allow-same-origin` | Treats content as same origin |
| `allow-forms` | Form submissions |
| `allow-popups` | Opening new windows |

Without any values, `sandbox` blocks everything — scripts, forms, popups, the works.

---

## `<embed>` and `<object>` — Less Common Nowadays

### `<embed>` — Simple Embedding

Can embed things like PDFs, but it's bare-bones:

```html
<embed src="notes.pdf" type="application/pdf" width="600" height="400">
```

No fallback content. If the browser can't handle it, the user sees nothing.

### `<object>` — Embedding with Fallback

Similar to `<embed>`, but lets you provide fallback content:

```html
<object data="notes.pdf" type="application/pdf" width="600" height="400">
    <p>Can't display PDF. <a href="notes.pdf">Download it instead</a>.</p>
</object>
```

The fallback (the `<p>` tag inside) only shows if the browser can't render the embedded content.

### Which One to Use?

Honestly, for most things:
- Use `<audio>` and `<video>` for media
- Use `<iframe>` for external pages and embeds
- Use `<embed>` or `<object>` only for edge cases like PDF embedding

---

## Things I Remind Myself

- Always provide `controls` on `<audio>` and `<video>` — don't force the user into autoplay with no way to stop it.
- Include multiple `<source>` formats for wider browser compatibility.
- Use `poster` on videos so there's a clean preview before playback.
- Add `title` to every `<iframe>` for accessibility.
- Use `loading="lazy"` on iframes that aren't visible on the first screen.
- Don't autoplay with sound — browsers will block it anyway, and it annoys users.
- Use `<track>` for subtitles — it's required for proper accessibility.

---

## What I Took Away

- `<audio>` and `<video>` handle media natively in HTML5 — no plugins needed.
- Provide multiple `<source>` formats with MP3/MP4 as the primary choice.
- `<iframe>` embeds external content like YouTube videos and Google Maps.
- `<track>` adds subtitles and captions for accessibility.
- `sandbox` on iframes adds a security layer for untrusted content.
- `<embed>` and `<object>` exist but are mostly legacy at this point.

---

## Questions I Used to Test Myself

1. What happens if you use `<audio>` without the `controls` attribute?
2. Why should you provide multiple `<source>` formats?
3. What is the `poster` attribute on `<video>` for?
4. How do browsers handle `autoplay` without `muted`?
5. What does the `sandbox` attribute do on an iframe?
6. When would you use `<object>` over `<embed>`?
7. How do you add subtitles to a video?

---

## Up Next

➡️ Semantic HTML — meaningful tags like `<header>`, `<main>`, `<article>`, `<footer>`.
