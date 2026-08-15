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

## Images

| Path | Purpose |
| --- | --- |
| `assets/images/hiltonprofilepic.jpg` | Hero portrait, framed square |
| `assets/images/hiltonprofilepic1.jpg` | Social link preview (`og:image`) |
| `assets/images/badges/*.png` | Credly badge art, downloaded from `images.credly.com` and served locally |

Swapping either file in place is enough — the paths are fixed in
[index.html](index.html). If the hero image ever fails to load, the portrait
column collapses rather than showing a broken icon.

The résumé at `Hilton-Chisora-Resume.pdf` is wired to the hero download button;
replace the file in place to publish a new version.

Optionally add a real favicon; the current one is an inline emoji SVG.

## Deploy

Hosted on **Cloudflare Pages**, deployed by GitHub Actions
([.github/workflows/deploy.yml](.github/workflows/deploy.yml)).

Every push runs two checks — HTML validation (blocking) and a link check
(reporting only). A green validation on `main` deploys to production; a pull
request deploys to a preview URL instead.

### One-time setup

1. **Create an API token** at
   [dash.cloudflare.com/profile/api-tokens](https://dash.cloudflare.com/profile/api-tokens)
   → *Create Token* → *Custom token*, with the permission
   **Account → Cloudflare Pages → Edit**.

2. **Copy your account ID** from the Cloudflare dashboard sidebar
   (Workers & Pages → *Account details*).

3. **Create the Pages project** — this also verifies the token works:

   ```bash
   CLOUDFLARE_ACCOUNT_ID=<account-id> CLOUDFLARE_API_TOKEN=<token> \
     npx wrangler pages project create hilton-chisora-portfolio \
     --production-branch=main
   ```

4. **Store the credentials as repository secrets:**

   ```bash
   gh secret set CLOUDFLARE_ACCOUNT_ID
   gh secret set CLOUDFLARE_API_TOKEN
   ```

The project name is set once in the workflow's `CF_PAGES_PROJECT` env var; it
must match the name used in step 3.

### Custom domain

Cloudflare serves the site at `hilton-chisora-portfolio.pages.dev`. To use your
own domain, add it under Workers & Pages → the project → *Custom domains*.

## Editing content

All copy lives in `index.html` in labelled sections — Hero, About, Experience,
Projects, Skills, Education, Contact. Colours and spacing are CSS custom
properties at the top of `styles.css`; change `--accent` to reskin the whole site.
