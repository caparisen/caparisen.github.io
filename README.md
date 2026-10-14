# caparisen.com

A placeholder site. Plain HTML and CSS — **no build step, no dependencies**.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The single page |
| `404.html` | Not-found page |
| `style.css` | All styling (design tokens, light/dark, layout) |
| `fonts.css` | Generated `@font-face` rules pointing at `fonts/` |
| `fonts/*.woff2` | Self-hosted **Bricolage Grotesque** + **Geist Mono** (latin, latin-ext) |
| `CNAME` | Custom domain for GitHub Pages (`caparisen.com`) |
| `.nojekyll` | Tells Pages to skip Jekyll |

Fonts are self-hosted on purpose: no third-party requests, works everywhere,
and it avoids depending on a font CDN being reachable.

## Deploy

The site is the **user site** of the `caparisen` account, so the repository must be
named `caparisen.github.io` (the repo name is what makes Pages serve it at the
account root). Push to the `main` branch — Pages serves the repository root.

In **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main` / `/ (root)`,
Custom domain = `caparisen.com`, then tick **Enforce HTTPS** once the certificate is issued.

## DNS

Registered at Dynadot, nameservers `ns1.dyna-ns.net` / `ns2.dyna-ns.net`. Records in place:

| Type | Name | Value |
| --- | --- | --- |
| `A` | `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| `CNAME` | `www` | `caparisen.github.io` |

The apex `A` records are GitHub Pages' four addresses; `www` must point at the
`<account>.github.io` host, never back at the apex.

## Renaming history

The site was originally `equasen.com` / `equasen.github.io`. On the rename to caparisen:

1. GitHub account `equasen` → `caparisen` (GitHub redirects old account URLs).
2. Repository `caparisen/equasen.github.io` → `caparisen/caparisen.github.io`.
3. Local clone: `git remote set-url origin https://github.com/caparisen/caparisen.github.io.git`
   and the local `user.name` / `user.email` in this repo.
4. `CNAME`, page titles, the `<h1>` and the favicon monogram (`e` → `c`) all follow the new name.

`equasen.com` is no longer served. The old DNS records can be deleted; to keep the
old domain alive as a redirect, point it at a separate Pages repo whose `CNAME` is
`equasen.com` and whose `index.html` is a meta-refresh to `https://caparisen.com/`.

## Editing

Everything visible is in `index.html`. Colours, type scale and spacing live in the
token block at the top of `style.css`.

## Before going live for real

- Remove `<meta name="robots" content="noindex">` from `index.html` and `404.html`
  (it is there so the placeholder is not what search engines index).
- Update `<meta name="description">` and `<title>`.
- Verify the domain in **Settings → Pages → Verified domains** so nobody else can
  claim `caparisen.com` on Pages if this repo is ever deleted.

## License

Fonts: Bricolage Grotesque and Geist Mono, both SIL Open Font License 1.1.
