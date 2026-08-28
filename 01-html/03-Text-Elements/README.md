# Text Elements in HTML

When I started working with HTML, I quickly realized that structuring text properly is a huge deal. Browsers don't care about how many spaces or line breaks you put in your code — they collapse everything. So you need specific tags to tell the browser how your text should be organized.

Here's everything I've learned about text elements.

---

## Headings

HTML gives you six heading levels. Think of them like a book outline — `<h1>` is the title of the book, `<h2>` is a chapter, `<h3>` is a sub-chapter, and so on.

```html
<h1>My Learning Journey</h1>
<h2>Frontend Development</h2>
<h3>HTML Basics</h3>
<h4>Working with Text</h4>
<h5>Formatting Details</h5>
<h6>Tiny Detail Level</h6>
```

A few things I learned the hard way:

- Only use **one `<h1>`** on a page. It's like the main title — having two messes up SEO and confuses screen readers.
- Don't jump from `<h1>` straight to `<h4>`. Go in order. It's not about how the text looks (that's CSS's job), it's about **meaning and structure**.
- Search engines scan headings to figure out what a page is about, so they actually matter.

---

## Paragraphs

The `<p>` tag wraps a block of text into a paragraph. The browser automatically puts some vertical space between consecutive paragraphs.

```html
<p>I started learning HTML as part of my full stack development journey.</p>
<p>It turned out to be simpler than I expected, but there's more depth to it than most people think.</p>
```

One thing that caught me off guard — the browser **collapses whitespace**. So even if you write:

```html
<p>This     has      lots     of     spaces.</p>
```

The browser shows: `This has lots of spaces.` — all squeezed into single spaces.

---

## Line Breaks and Horizontal Rules

Sometimes you need a line break without starting a whole new paragraph. That's what `<br>` does.

```html
<p>
    Nishanth P<br>
    Chennai, India<br>
    Java Full Stack Developer
</p>
```

And `<hr>` draws a horizontal line across the page. It's not just decorative — it represents a **thematic break** between sections.

```html
<p>End of one topic.</p>
<hr>
<p>Start of a completely different topic.</p>
```

Both `<br>` and `<hr>` are **self-closing tags** — they don't have a `</br>` or `</hr>`.

---

## Making Text Bold

There are two tags for bold text, and the difference matters:

**`<strong>`** — Use this when the text is genuinely important. Screen readers actually change their tone for this.

```html
<p><strong>Warning:</strong> Do not close the browser during installation.</p>
```

**`<b>`** — Use this when you just want the text to look bold visually, but it doesn't carry any special importance.

```html
<p>Today's special: <b>Masala Dosa</b></p>
```

My rule of thumb: if removing the boldness would lose meaning, use `<strong>`. Otherwise, `<b>` is fine.

---

## Making Text Italic

Same idea here — two tags, two different meanings:

**`<em>`** — Emphasis. Screen readers stress this word differently.

```html
<p>You <em>must</em> submit the assignment before Friday.</p>
```

**`<i>`** — Just visually italic. Used for foreign words, technical terms, or thoughts.

```html
<p>The word <i>namaste</i> means a respectful greeting in Hindi.</p>
```

---

## Underline, Strikethrough, and More

**Underline (`<u>`)** — Be careful with this one. People associate underlined text with links, so using it for regular text can confuse visitors.

```html
<p>The word <u>recieve</u> is misspelled.</p>
```

**Deleted text (`<del>`)** — Shows text that's been removed. The browser draws a line through it.

```html
<p>Original price: <del>₹2000</del> Now: ₹1500</p>
```

**No longer accurate (`<s>`)** — Similar to `<del>`, but for info that's outdated rather than deleted.

```html
<p><s>Registrations open</s> — Registrations are now closed.</p>
```

---

## Subscript and Superscript

These come up more often than you'd think — chemical formulas, math expressions, footnote references.

```html
<p>Water is H<sub>2</sub>O</p>
<p>The area of a circle is πr<sup>2</sup></p>
<p>See reference<sup>[1]</sup></p>
```

`<sub>` pushes text **below** the baseline, `<sup>` pushes it **above**.

---

## A Few More Useful Text Tags

**`<mark>`** — Highlights text like a yellow marker.
```html
<p>The exam will cover <mark>chapters 3 through 7</mark>.</p>
```

**`<small>`** — For fine print and side notes.
```html
<p><small>Terms and conditions apply.</small></p>
```

**`<abbr>`** — Wraps an abbreviation and shows the full form on hover.
```html
<p>I'm learning <abbr title="HyperText Markup Language">HTML</abbr> right now.</p>
```

**`<code>`** — For showing code snippets inline with text. Renders in a monospace font.
```html
<p>Use <code>System.out.println()</code> to print output in Java.</p>
```

**`<pre>`** — Preserves all whitespace and line breaks exactly as you typed them. Great for code blocks.
```html
<pre>
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
</pre>
```

**`<blockquote>`** — For quoting a paragraph from another source.
```html
<blockquote>
    The best error message is the one that never shows up.
</blockquote>
```

**`<q>`** — For short inline quotes. The browser automatically wraps it in quotation marks.
```html
<p>My mentor always says, <q>build something every day</q>.</p>
```

**`<cite>`** — References the title of a book, movie, or creative work.
```html
<p>I recently read <cite>Clean Code</cite> by Robert C. Martin.</p>
```

---

## Block vs Inline — This Confused Me At First

Every HTML element is either a **block element** or an **inline element**. Understanding this cleared up a lot of layout confusion for me.

**Block elements**:
- Always start on a new line
- Stretch to fill the full width available
- Examples: `<h1>`, `<p>`, `<blockquote>`, `<pre>`, `<hr>`, `<div>`

**Inline elements**:
- Sit within the flow of text — they don't break onto a new line
- Only take up as much width as their content needs
- Examples: `<strong>`, `<em>`, `<a>`, `<code>`, `<span>`, `<mark>`

```html
<p>This paragraph is a <strong>block element</strong> containing <em>inline elements</em>.</p>
```

The `<p>` takes the full width. The `<strong>` and `<em>` just sit within the text flow.

---

## Generic Containers: `<span>` and `<div>`

When no semantic tag fits, you use these generic containers:

**`<span>`** — Inline container. Wrap some text to style it or target it with JavaScript.
```html
<p>My favorite language is <span style="color: orange;">Java</span>.</p>
```

**`<div>`** — Block container. Group elements together for layout purposes.
```html
<div>
    <h2>Frontend Skills</h2>
    <p>HTML, CSS, JavaScript, React</p>
</div>
```

Neither `<span>` nor `<div>` carries any semantic meaning — they're just wrappers.

---

## What I Took Away

- Use the right tag for the job — `<strong>` for importance, `<em>` for emphasis, not just for making things look bold or italic.
- Don't skip heading levels. Structure matters more than appearance.
- Understand block vs inline — it'll save you headaches when you get to CSS.
- `<pre>` is your friend when displaying code snippets.
- `<span>` and `<div>` are generic containers — use them only when no semantic tag fits.

---

## Questions I Used to Test Myself

1. When would you pick `<strong>` over `<b>`?
2. What happens to extra spaces inside a `<p>` tag?
3. Why is skipping heading levels a bad idea?
4. What's the difference between `<del>` and `<s>`?
5. Name three block elements and three inline elements.
6. When would you use `<pre>` instead of `<p>`?
7. What does `<abbr>` do, and how does the tooltip work?

---

## Up Next

➡️ Lists — ordered, unordered, description lists, and nesting.
