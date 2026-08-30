# HTML Tables

Tables are for displaying data that naturally fits into rows and columns — schedules, price comparisons, grade sheets, specs. They're not for laying out a page (that's CSS's job), but for actual tabular data, nothing beats a proper `<table>`.

---

## The Basic Pieces

A table is built from these core tags:

```html
<table>
    <tr>
        <th>Name</th>
        <th>Role</th>
        <th>City</th>
    </tr>
    <tr>
        <td>Nishanth</td>
        <td>Developer</td>
        <td>Chennai</td>
    </tr>
    <tr>
        <td>Kavya</td>
        <td>Designer</td>
        <td>Bangalore</td>
    </tr>
</table>
```

| Tag | What It Does |
|-----|-------------|
| `<table>` | Wraps the entire table |
| `<tr>` | Creates a table row |
| `<th>` | Creates a header cell (bold and centered by default) |
| `<td>` | Creates a regular data cell |

---

## Organizing with Sections

For anything more than a tiny table, splitting it into `<thead>`, `<tbody>`, and `<tfoot>` makes the code way more readable — and it helps screen readers understand the structure too.

```html
<table>
    <thead>
        <tr>
            <th>Subject</th>
            <th>Internal Marks</th>
            <th>External Marks</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Data Structures</td>
            <td>38</td>
            <td>72</td>
        </tr>
        <tr>
            <td>Web Development</td>
            <td>42</td>
            <td>85</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>80</td>
            <td>157</td>
        </tr>
    </tfoot>
</table>
```

The browser can even keep the header and footer visible while scrolling through a long table body (with some CSS help).

---

## Adding a Table Title with `<caption>`

```html
<table>
    <caption>Semester 1 — Exam Results</caption>
    <thead>
        <tr>
            <th>Subject</th>
            <th>Grade</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Operating Systems</td>
            <td>A</td>
        </tr>
    </tbody>
</table>
```

The caption shows up above the table by default. It's especially helpful for accessibility — screen readers announce it before reading the table data.

---

## Merging Cells — colspan and rowspan

Sometimes you need a cell to stretch across multiple columns or rows.

### colspan — Stretching Horizontally

```html
<table>
    <tr>
        <th colspan="3">Student Performance Summary</th>
    </tr>
    <tr>
        <th>Name</th>
        <th>Subject</th>
        <th>Grade</th>
    </tr>
    <tr>
        <td>Nishanth</td>
        <td>Java</td>
        <td>A+</td>
    </tr>
</table>
```

The top header spans all three columns.

### rowspan — Stretching Vertically

```html
<table>
    <tr>
        <th>Name</th>
        <th>Subject</th>
        <th>Grade</th>
    </tr>
    <tr>
        <td rowspan="2">Nishanth</td>
        <td>Java</td>
        <td>A+</td>
    </tr>
    <tr>
        <td>HTML</td>
        <td>A</td>
    </tr>
</table>
```

"Nishanth" takes up two rows since both subjects belong to the same person.

---

## Making Tables Accessible

### The `scope` Attribute

Adding `scope` to your `<th>` tags tells screen readers whether a header applies to a column or a row.

```html
<thead>
    <tr>
        <th scope="col">Day</th>
        <th scope="col">Topic</th>
        <th scope="col">Hours</th>
    </tr>
</thead>
<tbody>
    <tr>
        <th scope="row">Monday</th>
        <td>HTML Forms</td>
        <td>3</td>
    </tr>
    <tr>
        <th scope="row">Tuesday</th>
        <td>CSS Flexbox</td>
        <td>4</td>
    </tr>
</tbody>
```

Without `scope`, screen readers have to guess which headers go with which cells. It usually guesses right for simple tables, but for anything complex, `scope` removes the guesswork.

---

## Styling Tables (CSS Preview)

By default, tables look pretty bare — no borders, no padding. Here's the minimum CSS to make them presentable:

```html
<style>
    table {
        border-collapse: collapse;  /* removes the gap between cell borders */
        width: 100%;
    }
    th, td {
        border: 1px solid #ccc;
        padding: 10px;
        text-align: left;
    }
    th {
        background-color: #f5f5f5;
    }
</style>
```

`border-collapse: collapse` is the key one — without it, each cell gets its own separate border, and the table looks like a grid with double lines everywhere.

---

## Things I Remind Myself

- Tables are for **data**, not for page layouts. Use CSS Grid or Flexbox for layout.
- Always use `<thead>`, `<tbody>`, and `<tfoot>` for structure and accessibility.
- Give tables a `<caption>` so screen readers can announce what the table is about.
- Use `scope="col"` or `scope="row"` on header cells for accessibility.
- Don't go overboard with colspan/rowspan — overly complex tables are hard to maintain and confusing for screen readers.
- Use `border-collapse: collapse` in CSS for clean-looking borders.

---

## What I Took Away

- Tables use `<table>`, `<tr>`, `<th>`, and `<td>`.
- Sections (`<thead>`, `<tbody>`, `<tfoot>`) add structure and meaning.
- `<caption>` labels the table for context.
- `colspan` merges across columns, `rowspan` merges down rows.
- `scope` on `<th>` is essential for screen reader accessibility.
- Always use CSS (not HTML attributes) for styling tables.

---

## Questions I Used to Test Myself

1. What's the difference between `<th>` and `<td>`?
2. Why split a table into `<thead>`, `<tbody>`, and `<tfoot>`?
3. How do you make a cell span two columns?
4. What does `scope="row"` do on a `<th>`?
5. What's `border-collapse: collapse` for?
6. Why shouldn't you use tables for page layout?

---

## Up Next

➡️ Forms — inputs, labels, validation, dropdowns, and fieldsets.
