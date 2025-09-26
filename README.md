# web-dev-starter

This is a starter project for web development with no frameworks and minimal
dependencies. It is intended to be a starting point for web development projects
that are written in plain HTML, CSS, and JavaScript.

## Getting Started

To get started, clone this repository and run the following commands:

```bash
npm install
```

This will install the necessary dependencies for the project.

## Development

It is recommended to use the VSCode Live Server extension to run the project
locally. This will allow you to see changes in real-time as you make them. There
is no need to run a build process or refresh the page manually. Additionally,
you do not need to setup a local server to run the project.

## Testing

To run the tests for the project, run the following command:

```bash
npm test
```

## Accessibility Lab Answers

### Color

The original color contrast had several issues:

- The navigation background color was `ff80ff` (invalid color as it was missing the `#`) which caused it to default to a gray color, with black text, providing insufficient contrast.
- The main content areas had a background of `rgb(155, 155, 155)` (light gray) with black text, which provided somewhat low contrast.

I fixed these issues by:

- Updating the navigation to use a blue background (`#336699`) with white text for better contrast
- Changed the content areas to a lighter background (`#f0f0f0`) that maintains good contrast with the black text
- Reduced the shadow opacity on the main heading to improve readability

### Semantic HTML

When navigating with a keyboard, the original site had several issues:

- The show/hide comments "button" wasn't actually a button, so it couldn't be focused or activated with the keyboard
- There were no proper heading elements, making it hard to navigate by headings
- Form inputs lacked proper labels and associations
- The content was structured with `<br>` tags instead of proper paragraph elements

I fixed these issues by:

- Replacing `<div class="header">` with proper `<header>` element
- Replacing `<div class="nav">` with `<nav>` element
- Converting `<font size="7|6|5">` elements to proper heading elements (`<h1>`, `<h2>`, `<h3>`)
- Adding proper paragraph `<p>` elements instead of text with `<br>` tags
- Making the show/hide control a proper `<button>` with keyboard support
- Adding ARIA attributes to improve keyboard navigation

### The Images

The images were inaccessible to screen reader users because they lacked alt text. I added descriptive alt text to each image and wrapped them in `<figure>` elements with `<figcaption>` to provide additional context.

### The Audio Player

The audio player was inaccessible to:

- Hearing impaired users: I added a transcript using the `<details>` and `<summary>` elements to provide a text alternative
- Users with older browsers: The audio player already had a fallback paragraph for browsers that don't support HTML5 audio, but I kept this and enhanced it by wrapping the audio element in a `<figure>` element with a `<figcaption>` that contains the transcript.

### The Forms

I improved the forms by:

- Adding a visually hidden label for the search form input
- Properly associating labels with input fields in the comment form using the `for` attribute that matches the `id` of the inputs
- Styling the form elements to maintain the design while improving accessibility

### The Show/Hide Comment Control

I made the show/hide comment control keyboard-accessible by:

- Converting it from a `<div>` to a `<button>` element
- Adding a JavaScript keyboard event listener for Enter and Space keys
- Adding `aria-expanded` and `aria-controls` attributes to indicate the button's state
- Adding focus styles for better visual indication when the button is focused

### The Table

I improved the table accessibility by:

- Adding `<th>` elements with proper `scope` attributes to identify column and row headers
- Adding a `<caption>` element to provide a title for the table
- Using `aria-describedby` to associate the table with its description
- Ensuring proper table structure with `<thead>` and `<tbody>` elements
