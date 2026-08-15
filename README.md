# goodstuffstudio

The site for **Goodstuff Studio**. Plain static HTML — no build step, no
dependencies, no framework. Hosted on Netlify, served from the repo root.

## Pages

| Path            | File                      |
| --------------- | ------------------------- |
| `/`             | `index.html`              |
| `/privacy`      | `privacy/index.html`      |
| `/privacy/lilt` | `privacy/lilt/index.html` |
| `/support`      | `support/index.html`      |
| not found       | `404.html`                |

Shared styles live in `assets/styles.css`. All links are root-absolute
(`/privacy/lilt/`), which is what makes them correct whether Netlify serves a
URL with or without its trailing slash.

## Deploying

`netlify.toml` sets `publish = "."` and no build command, so connecting the
repo in Netlify is the whole setup — every push to `main` deploys. Netlify
serves `404.html` for unmatched paths on its own; no redirect rule needed.

The file also sets security headers, including a Content-Security-Policy of
`default-src 'none'` with `style-src 'self'`. The pages currently load nothing
but their own stylesheet, so that is accurate — **if you ever add a script, a
web font, or an image from another origin, the CSP will block it** until you
widen it.

## Domain

The site URL appears in three places that are not derived from anything:

- `sitemap.xml` — the four `<loc>` values
- `robots.txt` — the `Sitemap:` line
- Netlify site settings

They currently assume `https://goodstuff.netlify.app`. Update all three
together if the subdomain differs or a custom domain is attached.

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Use a server rather than opening files
directly — the root-absolute paths will not resolve over `file://`.

## Editing the Lilt privacy policy

`privacy/lilt/index.html` is the policy linked from Lilt's App Store listing.
Its wording is supplied by the studio — when it changes, update the
`Last updated` date near the top of the page in the same commit.
