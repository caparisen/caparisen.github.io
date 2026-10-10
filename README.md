# equasen.com

A placeholder site. Plain HTML and CSS — **no build step, no dependencies**.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The single page |
| `404.html` | Not-found page |
| `style.css` | All styling (design tokens, light/dark, layout) |
| `fonts.css` | Generated `@font-face` rules pointing at `fonts/` |
| `fonts/*.woff2` | Self-hosted **Bricolage Grotesque** + **Geist Mono** (latin, latin-ext) |
| `CNAME` | Custom domain for GitHub Pages |
| `.nojekyll` | Tells Pages to skip Jekyll |

Fonts are self-hosted on purpose: no third-party requests, works everywhere,
and it avoids depending on a font CDN being reachable.

## Deploy

Push to the `main` branch. GitHub Pages serves the repository root.

In **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main` / `/ (root)`,
Custom domain = `equasen.com`, then tick **Enforce HTTPS** once the certificate is issued.

## Editing

Everything visible is in `index.html`. Colours, type scale and spacing live in the
token block at the top of `style.css`.

## Before going live for real

- Remove `<meta name="robots" content="noindex">` from `index.html` and `404.html`
  (it is there so the placeholder is not what search engines index).
- Update `<meta name="description">` and `<title>`.

## License

Fonts: Bricolage Grotesque and Geist Mono, both SIL Open Font License 1.1.
