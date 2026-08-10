# Hilton Hatitye Chisora — Portfolio

A single-page personal portfolio built from Hilton's résumé. No build step, no
dependencies — three files that run anywhere.

```
index.html    markup + content
styles.css    design tokens, layout, responsive rules
script.js     theme toggle, mobile nav, scroll reveals, counters
```

## Run locally

Open `index.html` directly in a browser, or serve it:

```bash
python -m http.server 8000
# → http://localhost:8000
```

## Features

- **Light / dark theme** — follows the OS preference, remembers your choice in `localStorage`
- **Fully responsive** — three breakpoints (1040px, 860px, 480px), mobile nav drawer
- **Scroll reveals + animated stat counters**, both disabled under `prefers-reduced-motion`
- **Active-section nav highlighting** via `IntersectionObserver`
- **Accessible** — skip link, focus-visible rings, ARIA on the menu toggle, semantic landmarks
- **Print stylesheet** — the page prints cleanly as a document

## Before publishing

Two placeholders need your real values:

1. **LinkedIn URL** — in [index.html](index.html), the contact section links to
   `https://www.linkedin.com/`. Replace with your profile URL.
2. **Résumé PDF** — the hero has a download button pointing at
   `Hilton-Chisora-Resume.pdf`. Drop the PDF in this folder under that exact
   filename, or remove the button.

Optionally add a real favicon (currently an inline emoji SVG) and an
`og:image` for link previews.

## Deploy

Any static host works. Drag the folder onto [Netlify Drop](https://app.netlify.com/drop),
or push to GitHub and enable Pages (Settings → Pages → deploy from branch, root).

## Editing content

All copy lives in `index.html` in labelled sections — Hero, About, Experience,
Projects, Skills, Education, Contact. Colours and spacing are CSS custom
properties at the top of `styles.css`; change `--accent` to reskin the whole site.
