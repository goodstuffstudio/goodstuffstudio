# goodstuffstudio.github.io

The site for **Goodstuff Studio**. Plain static HTML — no build step, no
dependencies, no framework. Served by GitHub Pages from `main` at the repo root.

## Pages

| Path             | File                     |
| ---------------- | ------------------------ |
| `/`              | `index.html`             |
| `/privacy`       | `privacy/index.html`     |
| `/privacy/lilt`  | `privacy/lilt/index.html`|
| `/support`       | `support/index.html`     |
| 404              | `404.html`               |

Shared styles live in `assets/styles.css`. `.nojekyll` tells Pages to serve
files as-is instead of running them through Jekyll.

## Before going live

The pages contain placeholder tokens that must be replaced:

- `{{SUPPORT_EMAIL}}` — the studio's real support address.
- `{{LILT_ONE_LINER}}` — one phrase describing what Lilt is.

Replace them everywhere at once:

```sh
grep -rl '{{SUPPORT_EMAIL}}' . --exclude-dir=.git \
  | xargs sed -i '' 's|{{SUPPORT_EMAIL}}|help@example.com|g'
```

Then delete the `.ph` spans wrapping them, and drop the `.ph` rule from
`assets/styles.css`.

`privacy/lilt/index.html` opens with an HTML comment listing every factual
claim to verify against what the app actually ships — the policy is written
assuming Lilt is fully on-device with no analytics SDKs. Check it before
publishing.

## Local preview

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Use a server rather than opening the files
directly — the pages reference `/assets/styles.css` by absolute path, which
`file://` will not resolve.

## Enabling GitHub Pages

Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
branch `main`, folder `/ (root)`. The site then serves at
<https://goodstuffstudio.github.io>. To use a custom domain later, add a `CNAME`
file containing the bare domain and point DNS at GitHub.
