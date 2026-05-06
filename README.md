# AI and the University Service — marketing site

Static marketing site for the University of Michigan professional development
course *AI and the University Service: Designing Responsibly in a Changing
Institution.*

## Structure

```
index.html                  Home
curriculum/index.html       10-week curriculum
who-its-for/index.html      Role-by-role audience page
apply/index.html            Apply CTA + FAQ + award conditions
404.html                    GitHub Pages serves this on unmatched paths
assets/
  css/site.css              All styles, hand-written
  img/logo.png              U-M logo (block M on blue)
  img/favicon.svg           Site favicon
robots.txt                  Allow all
```

No build step. Open `index.html` directly in a browser to preview.

## Deployment

Deploys to **GitHub Pages** as a **project site** under this repo. The live
URL is `https://<user>.github.io/genai/` (served from a subpath, not the
root).

To enable Pages after pushing:

1. Go to the repo's **Settings → Pages**.
2. Under **Source**, select **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Save.
4. Pages will build and serve within a minute or two.

### Path conventions

Because the site is served at a subpath (`/genai/`), paths are written as
**relative paths** from each HTML file:

- `index.html` (at repo root) → `assets/...`, `curriculum/`, etc.
- `curriculum/index.html`, `who-its-for/index.html`, `apply/index.html`
  (one level deep) → `../assets/...`, `../curriculum/`, etc.
- `404.html` is the one exception: GitHub Pages serves it on unmatched
  URLs, so the browser's address bar may be anything under `/genai/`.
  Relative paths from the 404 would resolve incorrectly, so 404.html uses
  absolute paths that include the repo subpath (`/genai/...`).

If you rename the repo from `genai`, update `404.html` to match.

## Things to swap in when you have them

Search for `TODO`, `placeholder`, or these specific strings:

- **Application URL** — the `Apply` button on `apply/index.html` links to
  `#application-placeholder`. Replace with the real form URL (Google Form,
  Qualtrics, Airtable, etc.).
- **Cohort dates** — the string `Dates TBA` / `Cohort dates TBA` / `Cohort
  dates coming soon` appears in the hero on every page and in the final
  CTAs. Swap in real dates once they're set.
- **Open Graph image** — no OG image is specified yet. When you have one,
  add a 1200×630 PNG at `assets/img/og.png` and reference it on every page
  with `<meta property="og:image" content="assets/img/og.png">` (root page)
  or `<meta property="og:image" content="../assets/img/og.png">` (subpages).
  For OG images, GitHub actually requires absolute URLs, so prefer
  `https://<user>.github.io/genai/assets/img/og.png`.
- **Imagery** — currently no photography on the site. If/when you add it,
  check U-M's own photo library at
  [photography.umich.edu](https://photography.umich.edu/) before going to
  paid stock. Avoid AI-generated imagery — the course's values rule it out.

## Accessibility

The site meets WCAG 2.1 AA:

- Semantic landmarks on every page (`header`, `nav`, `main`, `footer`).
- Skip link on every page.
- `:focus-visible` outline is Maize (#FFCB05) at 3px / 2px offset.
- Body text is `#1A1A1A` on white (16.8:1, AAA).
- All interactive elements are ≥44×44px.
- `@media (prefers-reduced-motion)` disables transitions and smooth scroll.
- See the header comment block in `assets/css/site.css` for the full list of
  color combinations and their computed contrast ratios.

Before shipping a change, run axe DevTools (or similar) on each page and fix
warnings before errors.

## Editing

Each HTML file has a duplicated `<header>` and `<footer>` block. If you add a
nav link or change the footer, edit all five files:

- `index.html`
- `curriculum/index.html`
- `who-its-for/index.html`
- `apply/index.html`
- `404.html`

This was a deliberate trade-off to keep the site build-step-free. If it
outgrows that, consider moving to Jekyll (which GitHub Pages supports
zero-config) or Eleventy.

## Tone guidelines for new copy

The course explicitly rejects hype language. When writing new copy:

- **Avoid:** *revolutionary, transformational, 10x, unlock, empower, harness,
  leverage, cutting-edge, game-changing, AI-powered*.
- **Favor:** *changing, shaping, real, honest, responsible, consequential,
  shared, forward-looking, ambitious*.
- When naming roles, always include **both** technical (developers, IT leads,
  data stewards) **and** non-technical (service managers, business analysts,
  operations leads) examples in the same sentence — not separate paragraphs.
  The cohort mix is the point.
- Use cohort language frequently: "you and ~31 colleagues," "the cohort,"
  "peers across U-M."

## Contact

General course questions: `its-ai-cohort@umich.edu`
