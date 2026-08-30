# HTML Forms

Forms are probably the most interactive part of HTML on its own. Every login page, registration form, search bar, contact form, and checkout page uses `<form>` at its core. Getting comfortable with forms and their many input types saved me a lot of time later when I started working with JavaScript.

---

## The `<form>` Tag

Everything goes inside a `<form>` wrapper:

```html
<form action="/register" method="POST">
    <!-- form fields go here -->
</form>
```

| Attribute | What It Does |
|-----------|-------------|
| `action` | The URL where the form data gets sent when submitted |
| `method` | How the data is sent — either `GET` or `POST` |

### GET vs POST — When to Use Which

| Aspect | GET | POST |
|--------|-----|------|
| Data location | Appended to the URL as query params | Hidden in the request body |
| Visibility | Visible in the address bar | Not visible |
| Data limit | URL length limit (~2000 chars) | No practical limit |
| Security | Less secure (data in URL) | More secure |
| Bookmarkable | Yes | No |
| Use for | Search forms, filters, non-sensitive data | Login, registration, file uploads |

Rule of thumb: if the form involves passwords or personal info, use POST.

---

## Labels — Don't Skip These

Every input needs a label. Not just for looks — labels are crucial for accessibility.

```html
<label for="email">Email Address:</label>
<input type="email" id="email" name="email">
```

The `for` attribute must match the `id` of the input. When it does:
- Clicking the label focuses the input field
- Screen readers announce the label when the user reaches the input
- On mobile, the tap target becomes bigger (the whole label is clickable)

I always pair `<label>` with every input. No exceptions.

---

## Input Types

The `<input>` tag is incredibly versatile — it changes behavior completely based on the `type` attribute.

### Text-Based Inputs

```html
<input type="text" name="fullname" placeholder="Your full name">
<input type="password" name="pwd" placeholder="Choose a password">
<input type="email" name="email" placeholder="you@example.com">
<input type="url" name="site" placeholder="https://your-site.com">
<input type="tel" name="phone" placeholder="9876543210">
<input type="search" name="q" placeholder="Search...">
```

Each type triggers different behavior — `email` validates for @ symbol, `tel` opens the numeric keyboard on phones, `password` masks the input.

### Number and Date Inputs

```html
<input type="number" name="age" min="13" max="100" step="1">
<input type="date" name="dob">
<input type="time" name="meeting">
<input type="datetime-local" name="appointment">
<input type="month" name="start-month">
```

The browser renders native pickers for dates and times — no JavaScript needed.

### Choice Inputs

```html
<!-- Checkboxes — pick multiple -->
<input type="checkbox" id="java" name="skills" value="java">
<label for="java">Java</label>

<input type="checkbox" id="html-skill" name="skills" value="html">
<label for="html-skill">HTML</label>

<!-- Radio buttons — pick one from a group -->
<input type="radio" id="fresher" name="experience" value="fresher">
<label for="fresher">Fresher</label>

<input type="radio" id="experienced" name="experience" value="experienced">
<label for="experienced">Experienced</label>
```

Radio buttons sharing the same `name` form a group — only one can be selected at a time.

### Other Handy Types

```html
<input type="color" name="theme" value="#3498db">
<input type="range" name="rating" min="1" max="10" step="1">
<input type="file" name="resume" accept=".pdf,.docx">
<input type="hidden" name="userId" value="42">
```

---

## All Input Types at a Glance

| Type | What It Does |
|------|-------------|
| `text` | Basic single-line text |
| `password` | Masked text entry |
| `email` | Email with basic validation |
| `url` | URL with basic validation |
| `tel` | Phone number (numeric keyboard on mobile) |
| `search` | Search field with clear button |
| `number` | Numeric value with up/down arrows |
| `range` | Slider control |
| `date` | Calendar date picker |
| `time` | Time picker |
| `datetime-local` | Combined date and time |
| `month` | Month and year picker |
| `color` | Color picker |
| `checkbox` | Toggle for multiple selections |
| `radio` | Single selection from a group |
| `file` | File upload |
| `hidden` | Invisible data sent with the form |

---

## `<textarea>` — Multi-Line Text

```html
<label for="bio">Tell us about yourself:</label>
<textarea id="bio" name="bio" rows="5" cols="40" placeholder="Write something..."></textarea>
```

Unlike `<input>`, `<textarea>` can hold multiple lines. `rows` controls height, `cols` controls width.

---

## `<select>` — Dropdown Menus

```html
<label for="branch">Branch:</label>
<select id="branch" name="branch">
    <option value="">-- Pick a branch --</option>
    <option value="cse">Computer Science</option>
    <option value="ece">Electronics</option>
    <option value="mech">Mechanical</option>
</select>
```

### Grouping Options

```html
<select name="language">
    <optgroup label="Frontend">
        <option value="js">JavaScript</option>
        <option value="ts">TypeScript</option>
    </optgroup>
    <optgroup label="Backend">
        <option value="java">Java</option>
        <option value="python">Python</option>
    </optgroup>
</select>
```

### Allowing Multiple Selections

```html
<select name="hobbies" multiple>
    <option value="coding">Coding</option>
    <option value="gaming">Gaming</option>
    <option value="reading">Reading</option>
    <option value="music">Music</option>
</select>
```

Users hold Ctrl (or Cmd on Mac) to select multiple items.

---

## `<datalist>` — Suggestions While Typing

This gives the user a dropdown of suggestions as they type, but still lets them enter something custom.

```html
<label for="framework">Preferred Framework:</label>
<input type="text" id="framework" name="framework" list="frameworks">
<datalist id="frameworks">
    <option value="React">
    <option value="Angular">
    <option value="Vue.js">
    <option value="Svelte">
    <option value="Spring Boot">
</datalist>
```

It's like a combo of a text input and a dropdown — flexible and useful.

---

## Buttons

```html
<button type="submit">Register</button>
<button type="reset">Clear Everything</button>
<button type="button">Do Something with JS</button>
```

| Type | Behavior |
|------|----------|
| `submit` | Sends the form (default if no type is specified) |
| `reset` | Clears all fields back to their defaults |
| `button` | Does nothing by itself — you hook it up with JavaScript |

---

## Grouping Fields with `<fieldset>` and `<legend>`

For longer forms, grouping related fields makes them easier to scan and understand.

```html
<fieldset>
    <legend>Personal Details</legend>

    <label for="fname">First Name:</label>
    <input type="text" id="fname" name="fname">

    <label for="lname">Last Name:</label>
    <input type="text" id="lname" name="lname">
</fieldset>

<fieldset>
    <legend>Account Setup</legend>

    <label for="uname">Username:</label>
    <input type="text" id="uname" name="uname">

    <label for="pass">Password:</label>
    <input type="password" id="pass" name="pass">
</fieldset>
```

Screen readers announce the legend before reading the fields inside, which gives users context.

---

## Built-in Validation

HTML can validate input without a single line of JavaScript. Here are the attributes I use most:

| Attribute | What It Does | Example |
|-----------|-------------|---------|
| `required` | Field can't be empty | `<input required>` |
| `placeholder` | Hint text inside the field | `placeholder="Enter name"` |
| `minlength` | Minimum characters | `minlength="3"` |
| `maxlength` | Maximum characters | `maxlength="50"` |
| `min` | Minimum numeric value | `min="18"` |
| `max` | Maximum numeric value | `max="100"` |
| `step` | Increment for numbers/ranges | `step="5"` |
| `pattern` | Regex the input must match | `pattern="[A-Za-z]+"` |
| `readonly` | Visible but not editable | `<input readonly>` |
| `disabled` | Grayed out and not submittable | `<input disabled>` |
| `autofocus` | Automatically focused when page loads | `<input autofocus>` |

### Example — A Registration Form with Validation

```html
<form action="/register" method="POST">
    <label for="user">Username:</label>
    <input type="text" id="user" name="user" minlength="3" maxlength="20" pattern="[a-zA-Z0-9_]+" required
           placeholder="Letters, numbers, underscore">

    <label for="mail">Email:</label>
    <input type="email" id="mail" name="mail" required placeholder="you@example.com">

    <label for="yob">Year of Birth:</label>
    <input type="number" id="yob" name="yob" min="1950" max="2010" required>

    <button type="submit">Create Account</button>
</form>
```

If any validation fails, the browser blocks submission and shows a built-in error message. No JavaScript required.

---

## Things I Remind Myself

- Always pair a `<label>` with every input using `for` and `id`.
- Use the most specific `type` for each input — `email`, `date`, `number`, etc. — so browsers can validate and optimize keyboard input.
- `placeholder` is a hint, not a replacement for labels. Screen readers may not read placeholders.
- Every input needs a `name` attribute — without it, the data won't be included in the submission.
- Group related fields with `<fieldset>` and `<legend>`.
- Use POST for sensitive data, GET for search and filtering.
- Take advantage of HTML validation attributes before reaching for JavaScript.

---

## What I Took Away

- `<form>` wraps all form elements and sends data via `action` and `method`.
- `<input>` covers 15+ types of user input.
- Labels are mandatory for accessibility.
- `<textarea>`, `<select>`, and `<datalist>` cover multi-line text, dropdowns, and auto-suggestions.
- `<fieldset>` + `<legend>` group related fields for better readability and accessibility.
- HTML validation attributes handle common checks without JavaScript.

---

## Questions I Used to Test Myself

1. When should you use POST instead of GET?
2. Why must every input have a `<label>`?
3. How do radio buttons form a group?
4. What's the difference between `<select>` and `<datalist>`?
5. What does `<fieldset>` do, and when would you use it?
6. How does the `pattern` attribute work?
7. What happens if an input has no `name` attribute?

---

## Up Next

➡️ Multimedia — audio, video, embedding content with `<iframe>`.
