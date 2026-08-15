# goodstuffstudio

The site for **Goodstuff Studio**. Plain static HTML — no build step, no
dependencies, no framework. Served by GitHub Pages from `main` at the repo root.

## Pages

| Path            | File                      |
| --------------- | ------------------------- |
| `/`             | `index.html`              |
| `/privacy`      | `privacy/index.html`      |
| `/privacy/lilt` | `privacy/lilt/index.html` |
| `/support`      | `support/index.html`      |
| 404             | `404.html`                |

Shared styles live in `assets/styles.css`. `.nojekyll` tells Pages to serve
files as-is instead of running them through Jekyll.

## Where this is served from

The repo is named `goodstuffstudio`, not `goodstuffstudio.github.io`, so
GitHub Pages treats it as a **project site** and serves it under a path
prefix:

```
https://goodstuffstudio.github.io/goodstuffstudio/privacy/lilt/
```

All four content pages use **relative** links, so they work correctly whether
the site is served from that prefix or from the root of a custom domain. Three
things do hardcode the full URL and must be updated if a custom domain is
attached:

- `404.html` — Pages serves it for any missing path at any depth, so its links
  have to be absolute. Change the `/goodstuffstudio/` prefixes to `/`.
- `sitemap.xml` — the four `<loc>` values.
- `robots.txt` — the `Sitemap:` line.

To attach a custom domain, add a `CNAME` file containing the bare domain and
point DNS at GitHub.

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Relative paths mean you can also open the
files directly over `file://` if you prefer.

## Enabling GitHub Pages

Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
branch `main`, folder `/ (root)`.

## Editing the Lilt privacy policy

`privacy/lilt/index.html` is the policy linked from Lilt's App Store listing.
Its wording is supplied by the studio — when it changes, update the
`Last updated` date near the top of the page in the same commit.
