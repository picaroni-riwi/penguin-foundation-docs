# Semantic HTML and SEO

Search engines and screen readers understand a page through its HTML structure.
Correct tags help the site appear in search results and help everyone navigate it.

## Page skeleton

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Donate | Penguin Foundation</title>
    <meta name="description" content="Support Penguin Foundation with a donation. Every contribution helps protect penguins." />
    <link rel="stylesheet" href="dist/output.css" />
  </head>
  <body>
    <!-- Blocks are written here, between their markers -->
  </body>
</html>
```

## Core rules

1. **`lang="en"`** on the `<html>` tag.
2. **One `<h1>` per page.** It describes the page topic.
3. **Headings in order.** `h1` → `h2` → `h3`. Do not skip levels to get a size. Use Tailwind classes for size.
4. **Use landmarks.** `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`.
5. **Unique `<title>`** on every page, under about 60 characters.
6. **`<meta name="description">`** on every page, under about 160 characters.
7. **Every image has `alt` text.** Describe the content. Use `alt=""` only for decorative images.
8. **Descriptive links.** Avoid "click here".
9. **Real links and buttons.** `<a href>` navigates; `<button>` performs an action.

## Bad vs good

### Divs for everything

```html
<!-- Bad -->
<div class="top">
  <div class="logo">Penguin Foundation</div>
  <div class="menu">...</div>
</div>

<!-- Good -->
<header>
  <a href="index.html">Penguin Foundation</a>
  <nav>...</nav>
</header>
```

### Headings chosen for size

```html
<!-- Bad: skips h2 because it looks smaller -->
<h1>Donate</h1>
<h4>Why donate?</h4>

<!-- Good -->
<h1 class="text-4xl font-bold">Donate</h1>
<h2 class="text-2xl font-bold">Why donate?</h2>
```

### Images

```html
<!-- Bad -->
<img src="assets/images/penguin.jpg" />

<!-- Good -->
<img src="assets/images/penguin.jpg" alt="Emperor penguin standing on Antarctic ice" />

<!-- Good, decorative only -->
<img src="assets/images/wave-divider.svg" alt="" />
```

### Vague links

```html
<!-- Bad -->
<a href="partners.html">Click here</a>

<!-- Good -->
<a href="partners.html">Meet our partners</a>
```

### Clickable div instead of a link

```html
<!-- Bad -->
<div onclick="location.href='donate.html'">Donate</div>

<!-- Good -->
<a href="donate.html">Donate</a>
```

## Meta tags per page

| Page | Title | Description |
|------|-------|-------------|
| `index.html` | Penguin Foundation \| Protecting penguins | Learn about our work and how to get involved. |
| `pages/about.html` | About Us \| Penguin Foundation | Meet the mission, history and team behind the foundation. |
| `pages/donate.html` | Donate \| Penguin Foundation | Support our work with a donation. |
| `pages/partners.html` | Partners \| Penguin Foundation | See the organizations that work with us. |

## Before you open a PR

- [ ] `<html lang="en">` is set.
- [ ] The page has exactly one `<h1>`.
- [ ] Headings follow h1 → h2 → h3.
- [ ] Every image has `alt` text.
- [ ] Links use descriptive text.
- [ ] The PR is in English.