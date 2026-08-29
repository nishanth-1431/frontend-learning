# HTML Lists

Lists seem simple, but they show up everywhere — navigation menus, feature highlights, step-by-step instructions, glossaries. Getting comfortable with all three types early on made my HTML much cleaner.

---

## Three Types of Lists

| Type | Tag | When to Use |
|------|-----|-------------|
| Unordered | `<ul>` | Order doesn't matter (shopping list, features, menu items) |
| Ordered | `<ol>` | Sequence matters (steps, rankings, instructions) |
| Description | `<dl>` | Pairing terms with definitions (glossary, FAQ, specs) |

---

## Unordered Lists

Items show up with bullet points. I use these for things where the order is irrelevant.

```html
<ul>
    <li>Learn HTML</li>
    <li>Learn CSS</li>
    <li>Learn JavaScript</li>
    <li>Build projects</li>
</ul>
```

You can change the bullet style with the `type` attribute, though CSS is the better way to do it:

```html
<ul type="disc">Item</ul>      <!-- filled circle (default) -->
<ul type="circle">Item</ul>    <!-- empty circle -->
<ul type="square">Item</ul>    <!-- filled square -->
```

---

## Ordered Lists

These number your items automatically. Perfect for anything with a sequence.

```html
<ol>
    <li>Set up the development environment</li>
    <li>Create the project structure</li>
    <li>Write the HTML skeleton</li>
    <li>Add content and test in the browser</li>
</ol>
```

### Useful Attributes

You can control the numbering style, starting point, and direction:

| Attribute | What It Does | Example |
|-----------|-------------|---------|
| `type` | Changes the numbering format | `type="A"` gives A, B, C |
| `start` | Begins counting from a specific number | `start="5"` starts at 5 |
| `reversed` | Counts backwards | `<ol reversed>` gives 3, 2, 1 |

```html
<!-- Roman numerals starting from 3 -->
<ol type="I" start="3">
    <li>Third chapter</li>
    <li>Fourth chapter</li>
</ol>

<!-- Countdown style -->
<ol reversed>
    <li>Bronze</li>
    <li>Silver</li>
    <li>Gold</li>
</ol>
```

The reversed one is pretty cool — it numbers them 3, 2, 1 automatically.

---

## Description Lists

These pair a **term** with its **definition**. I didn't know about these until I needed a glossary section.

```html
<dl>
    <dt>JDK</dt>
    <dd>Java Development Kit — contains tools to compile and run Java programs.</dd>

    <dt>JRE</dt>
    <dd>Java Runtime Environment — provides the runtime to execute Java applications.</dd>

    <dt>JVM</dt>
    <dd>Java Virtual Machine — the engine that runs Java bytecode.</dd>
</dl>
```

The tags are:
- `<dl>` — wraps the entire description list
- `<dt>` — the term being defined
- `<dd>` — the definition or description

A single term can have multiple definitions:

```html
<dl>
    <dt>Spring</dt>
    <dd>A season of the year.</dd>
    <dd>A popular Java framework for building web applications.</dd>
</dl>
```

---

## Nesting Lists

Lists inside lists are surprisingly common — think of a folder structure or a multi-level menu.

```html
<ul>
    <li>Frontend
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </li>
    <li>Backend
        <ul>
            <li>Java</li>
            <li>Spring Boot</li>
            <li>MySQL</li>
        </ul>
    </li>
</ul>
```

You can also nest ordered inside unordered (or vice versa):

```html
<ol>
    <li>Install tools
        <ul>
            <li>VS Code</li>
            <li>Git</li>
            <li>Chrome</li>
        </ul>
    </li>
    <li>Create your first HTML file</li>
    <li>Open it in the browser</li>
</ol>
```

---

## Things to Keep in Mind

- Only `<li>` elements belong directly inside `<ul>` or `<ol>`. Don't put random elements as direct children.
- Use `<ul>` when items have no particular order. Use `<ol>` when sequence matters.
- `<dl>` is perfect for things like glossaries, FAQs, and metadata displays.
- If you need to style bullets or numbers, CSS is the way to go (the `type` attribute works but CSS gives you way more control).
- Nested lists are great for hierarchical data, but don't go too deep — it gets unreadable.

---

## Quick Comparison

| Feature | `<ul>` | `<ol>` | `<dl>` |
|---------|--------|--------|--------|
| Marker | Bullets | Numbers/Letters | None |
| Order Matters? | No | Yes | N/A |
| Child Tags | `<li>` | `<li>` | `<dt>` + `<dd>` |
| Common Use | Menus, features | Steps, rankings | Glossary, specs |

---

## What I Took Away

- HTML has three list types, and each one has a clear purpose.
- `<ul>` and `<ol>` use `<li>` as children. `<dl>` uses `<dt>` and `<dd>`.
- Ordered lists have handy attributes like `type`, `start`, and `reversed`.
- Nesting works naturally — just put a new list inside an `<li>`.

---

## Questions I Used to Test Myself

1. When would you pick `<ol>` over `<ul>`?
2. How do you make an ordered list count backwards?
3. What are `<dt>` and `<dd>` used for?
4. How do you start an ordered list from number 5?
5. What's the right way to create a sub-list inside a list?

---

## Up Next

➡️ Links — anchor tags, internal/external linking, email and phone links.
