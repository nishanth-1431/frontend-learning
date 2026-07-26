# HTML Basic Structure

## Introduction

Every HTML document follows a standard structure known as the **HTML Boilerplate**. This structure helps web browsers understand how to interpret and display the content of a webpage.

Although browsers can display simple HTML without the complete structure, writing a proper HTML document is considered a best practice and is followed by all professional web developers.

Every webpage you create should begin with this basic structure.

---

## HTML Boilerplate

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>My First Webpage</title>
</head>

<body>

    <h1>Hello, World!</h1>

    <p>Welcome to HTML.</p>

</body>

</html>
```

---

# Understanding Each Part

## 1. `<!DOCTYPE html>`

```html
<!DOCTYPE html>
```

The `<!DOCTYPE html>` declaration tells the browser that the document is written using **HTML5**, which is the latest version of HTML.

It is **not an HTML tag**, but an instruction to the browser.

This declaration should always be the first line of every HTML document.

### Why is it important?

Without the DOCTYPE declaration, browsers may switch to **Quirks Mode**, where they try to render the page using older browser rules. This can cause webpages to behave differently across browsers.

---

## 2. `<html>`

```html
<html lang="en">
```

The `<html>` tag is called the **root element** because it contains every other element in the webpage.

Everything that appears on a webpage must be placed inside this tag.

### The `lang` Attribute

```html
<html lang="en">
```

The `lang` attribute specifies the language of the webpage.

In this example:

- `en` represents English.
- `fr` represents French.
- `ta` represents Tamil.
- `hi` represents Hindi.

### Why do we use it?

- Helps search engines understand the webpage language.
- Improves accessibility for screen readers.
- Assists browsers with language-specific features such as translation.

---

## 3. `<head>`

```html
<head>

</head>
```

The `<head>` section stores information **about the webpage**, not the visible content.

Anything placed inside `<head>` is generally **not displayed** on the webpage itself.

Common elements inside the `<head>` section include:

- Page title
- Character encoding
- CSS files
- JavaScript files
- Meta information
- Favicon

Think of the `<head>` section as the webpage's configuration area.

---

## 4. `<meta charset="UTF-8">`

```html
<meta charset="UTF-8">
```

This tag specifies the character encoding used by the webpage.

Using **UTF-8** allows the webpage to display letters, numbers, symbols, and characters from many languages correctly.

For example, UTF-8 supports:

- English
- Tamil
- Hindi
- Japanese
- Arabic
- Emoji 😊

Without UTF-8, some characters may appear as unreadable symbols.

---

## 5. `<title>`

```html
<title>My First Webpage</title>
```

The `<title>` tag defines the title of the webpage.

This title appears:

- In the browser tab.
- In bookmarks.
- In search engine results.

The title **does not appear inside the webpage**.

### Example

Browser Tab:

```
My First Webpage
```

Webpage:

```
Hello, World!

Welcome to HTML.
```

---

## 6. `<body>`

```html
<body>

</body>
```

The `<body>` element contains everything that users can see on the webpage.

Examples include:

- Headings
- Paragraphs
- Images
- Links
- Lists
- Tables
- Forms
- Videos

Whenever you create visible content, it belongs inside the `<body>` tag.

---

# HTML Document Structure

The structure of an HTML document can be represented as a tree.

```
HTML Document
│
├── <!DOCTYPE html>
│
└── <html>
     │
     ├── <head>
     │      │
     │      ├── <meta>
     │      └── <title>
     │
     └── <body>
            │
            ├── <h1>
            └── <p>
```

Each element is nested inside another element, forming a parent-child relationship.

---

# How Browsers Read HTML

When an HTML file is opened, the browser performs the following steps:

```
HTML File
      │
      ▼
Browser Reads HTML Code
      │
      ▼
Interprets HTML Elements
      │
      ▼
Builds the Webpage Structure
      │
      ▼
Displays the Webpage
```

The browser reads the HTML from top to bottom and displays the content inside the `<body>` section.

---

# Best Practices

- Always begin with `<!DOCTYPE html>`.
- Use the `lang` attribute in the `<html>` tag.
- Add `<meta charset="UTF-8">` to support all characters.
- Provide a meaningful title for every webpage.
- Place only visible content inside the `<body>` section.
- Indent your HTML code properly for better readability.

---

# Key Differences

| Element | Purpose |
|----------|---------|
| `<!DOCTYPE html>` | Declares the document as HTML5 |
| `<html>` | Root element containing the entire webpage |
| `<head>` | Stores webpage information and metadata |
| `<meta charset="UTF-8">` | Specifies character encoding |
| `<title>` | Sets the browser tab title |
| `<body>` | Contains all visible webpage content |

---

# Summary

- Every HTML document follows a standard structure called the HTML Boilerplate.
- `<!DOCTYPE html>` tells the browser to use HTML5.
- The `<html>` element contains the entire webpage.
- The `<head>` section stores metadata and webpage information.
- The `<title>` element defines the browser tab title.
- The `<body>` section contains everything visible to the user.
- Following the standard HTML structure ensures better compatibility, readability, and maintainability.

---