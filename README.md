# benisen.com

A teaser landing page. Plain HTML and CSS — **no build step, no dependencies**.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The teaser: masthead, one-line statement, full-width wordmark |
| `404.html` | Not-found page, same composition |
| `style.css` | All styling (design tokens, light/dark, layout, wordmark fitting) |
| `fonts.css` | Generated `@font-face` rules pointing at `fonts/` |
| `fonts/*.woff2` | Self-hosted **Bricolage Grotesque** + **Geist Mono** (latin, latin-ext) |
| `favicon.svg` | The site icon — a lowercase `b` from Bricolage Grotesque, ink on paper |
| `apple-touch-icon.png` | 180×180 raster of the same icon, for the iOS home screen |
| `CNAME` | Custom domain for GitHub Pages (`benisen.com`) |
| `.nojekyll` | Tells Pages to skip Jekyll |
| `hospital/index.html` | Standalone mobile hospital guide, served at `/hospital/` |

Fonts are self-hosted on purpose: no third-party requests, works everywhere,
and it avoids depending on a font CDN being reachable.

## The wordmark

`.logotype` runs edge to edge by dividing the available width by the wordmark's
advance width in `em` (currently `2.92em` at weight 380 and `-0.055em` tracking).
If the copy, font, weight or tracking changes, re-measure that divisor:
`document.createRange()` over the `h1` gives the advance width, divide it by the
computed `font-size`.

Light and dark both follow `prefers-color-scheme`; colours are the four tokens
at the top of `style.css`.

## The icon

`favicon.svg` is a single self-contained file: a `viewBox` on a 1024 grid, two
paths, and the two site colours written literally as `fill` attributes. The `b`
outline was extracted from Bricolage Grotesque (SIL OFL) with `fontTools`.

Two constraints are worth keeping if it is ever redrawn:

- **No `<style>` block inside the SVG.** A favicon is loaded as its own
  document, so it cannot see the page's CSS — and an internal CSS rule outranks
  the `fill` attribute, which would repaint the background tile as well as the
  mark. Colours must be literal attributes.
- **Colours are the site tokens**: `#FBFBF9` paper, `#15150F` ink.

`apple-touch-icon.png` is a 180×180 raster of the same file (iOS does not accept
SVG for home-screen icons). To regenerate it, render `favicon.svg` at 180px and
screenshot without resampling.

## Deploy

The site is the **user site** of the `caparisen` account, so the repository must
be named `caparisen.github.io` (the repo name is what makes Pages serve it at the
account root). Push to the `main` branch — Pages serves the repository root.

In **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main` / `/ (root)`,
Custom domain = `benisen.com`, then tick **Enforce HTTPS** once the certificate is issued.

The repository name and the custom domain are independent: Pages serves
`caparisen.github.io` at whatever custom domain `CNAME` names.

## DNS

| Type | Name | Value |
| --- | --- | --- |
| `A` | `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `CNAME` | `www` | `caparisen.github.io` |

The apex `A` records are GitHub Pages' four addresses; `www` must point at the
`<account>.github.io` host, never back at the apex.

## Renaming history

The site has moved twice:

1. `equasen.com` / `equasen.github.io` — original placeholder.
2. `caparisen.com` — account `equasen` renamed to `caparisen`, repository renamed
   to `caparisen/caparisen.github.io`, domain and wordmark updated.
3. `benisen.com` — on 2026-11-06 the custom domain was changed (Pages commits
   `CNAME` automatically). The account and repository are still
   `caparisen/caparisen.github.io`; only the domain, wordmark and icon changed.

`equasen.com` and `caparisen.com` are no longer served. To keep an old domain
alive as a redirect, point it at a separate Pages repo whose `CNAME` is that
domain and whose `index.html` is a meta-refresh to `https://benisen.com/`.

## Editing

Everything visible is in `index.html` and `404.html`; colours, type scale and
spacing live in the token block at the top of `style.css`. The teaser is
intentionally content-free.

## Before going live for real

- Remove `<meta name="robots" content="noindex">` from `index.html` and `404.html`
  (it is there so the teaser is not what search engines index).
- Update `<meta name="description">`.
- Verify the domain in **Settings → Pages → Verified domains** so nobody else can
  claim `benisen.com` on Pages if this repo is ever deleted.

## License

Fonts: Bricolage Grotesque and Geist Mono, both SIL Open Font License 1.1.
The favicon's `b` outline is derived from Bricolage Grotesque.
