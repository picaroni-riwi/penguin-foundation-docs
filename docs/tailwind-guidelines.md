# Tailwind CSS Guidelines

The site is built with plain **HTML** and **Tailwind CSS v4**, compiled with the Tailwind CLI.
We do not write custom CSS files. Styling is done with **utility classes** in the HTML.

## How the CSS is built

- Source file: `src/input.css`. It holds the Tailwind import and the theme.
- Output file: `dist/output.css`. Every HTML page links to it.
- Run `npm run dev` while you work. It rebuilds `dist/output.css` on every save.

## The theme

Colors are defined once, in `src/input.css`:

```css
@theme {
  --color-primary: #000000;
  --color-secondary: #fdc425;
  --color-brand: #2563eb;
}
```

Use them in HTML as `bg-primary`, `text-secondary`, `bg-brand`, and so on.

**Do not change the theme or the global body style inside a block of `index.html`.** Ask the lead first.

## Core rules

1. **Utility classes only.** No `style="..."` attributes.
2. **Mobile first.** Write the base classes for small screens, then add `md:` and `lg:`.
3. **Use the standard scale.** Do not invent values such as `p-[13px]`. Arbitrary values are only allowed if the lead approves them.
4. **Keep class lists readable.** Break long lists across several lines.
5. **Every image needs `alt` text** (see [html-semantic-seo.md](html-semantic-seo.md)).
6. **Do not repeat the global body style.** It is already set in `src/input.css`.

## Bad vs good

### Inline styles

```html
<!-- Bad -->
<div style="background-color: #1e40af; padding: 16px; color: white;">
  Donate today
</div>

<!-- Good -->
<div class="bg-brand p-4 text-white">
  Donate today
</div>
```

### Arbitrary values

```html
<!-- Bad -->
<p class="mt-[13px] text-[17px]">Thank you for your support.</p>

<!-- Good -->
<p class="mt-3 text-lg">Thank you for your support.</p>
```

### Repeated global styles

```html
<!-- Bad: the body already has these in input.css -->
<body class="bg-gray-50 text-gray-900 antialiased">

<!-- Good -->
<body>
```

## Breakpoints

| Prefix | Screen width | Typical device |
|--------|--------------|----------------|
| (none) | All sizes | Phones (base style) |
| `sm:` | 640px and up | Large phones |
| `md:` | 768px and up | Tablets |
| `lg:` | 1024px and up | Laptops |

```html
<section class="flex flex-col gap-6 md:flex-row">
  <div class="md:w-1/2">Text</div>
  <div class="md:w-1/2">Image</div>
</section>
```

## Suggested order of classes

1. Layout: `flex`, `grid`, `block`, `hidden`
2. Position: `relative`, `absolute`, `top-0`
3. Size: `w-full`, `h-64`, `max-w-md`
4. Spacing: `p-4`, `m-2`, `gap-6`
5. Typography: `text-lg`, `font-bold`, `text-center`
6. Colors: `bg-brand`, `text-white`, `border-gray-200`
7. Effects and states: `shadow`, `rounded-lg`, `hover:bg-blue-700`

```html
<button class="flex w-full justify-center rounded-lg bg-brand p-3 font-bold text-white hover:bg-blue-700">
  Donate
</button>
```

## Common components

### Button

```html
<a href="donate.html"
   class="inline-block rounded-lg bg-brand px-6 py-3 font-bold text-white hover:bg-blue-700">
  Donate now
</a>
```

### Card

```html
<article class="rounded-lg bg-white p-6 shadow-md">
  <img src="assets/images/partner.png" alt="Partner logo" class="mb-4 h-24 w-full object-contain" />
  <h3 class="text-lg font-bold">Partner name</h3>
  <p class="text-gray-600">Short description of the partner.</p>
</article>
```

## Things to avoid

- `!important` or `!` prefixes on classes.
- Text inside images. Put text in HTML.
- `<br>` for spacing. Use `mt-` or `mb-`.
- Editing `dist/output.css` by hand. It is generated.

## Before you open a PR

- [ ] The page looks correct on a phone-sized window and on desktop.
- [ ] No `style="..."` attributes were added.
- [ ] No arbitrary values such as `[13px]` were added.
- [ ] Every image has `alt` text.
- [ ] You only changed your own block.
- [ ] The commit messages follow [commit-conventions.md](commit-conventions.md).
- [ ] The PR base is `develop` and the PR is in English.