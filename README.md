# Vigil Fire — marketing site

A standalone, single-file marketing site for **Vigil Fire** (the fire-equipment
register app, which lives in its own separate repo — `Fire-Equipment-Register`).

Keep this repo separate from the app: different audience, different release
cadence, and a marketing change should never be able to break the compliance
app or its offline cache.

## Structure

```
index.html      ← the whole site (inline CSS + a few lines of JS, no build step)
.nojekyll       ← lets GitHub Pages serve the files as-is
screens/        ← put real screenshots here (see placeholders in index.html)
og-image.png    ← 1200×630 social preview image (referenced in <head>)
```

## Fill in the placeholders

Search `index.html` for `TODO` and `{{ }}`:

| Placeholder | What to set |
|---|---|
| `https://app.vigilfire.co.za` | URL where the Vigil Fire app is actually deployed |
| `hello@vigilfire.co.za` / `+27 (0)00 000 0000` | Your real contact details |
| `{{FORM_ID}}` | A [Formspree](https://formspree.io) form id (free), **or** switch to Netlify Forms — see the comment above the `<form>` |
| `{{Your company (Pty) Ltd}}` | The legal entity behind Vigil Fire, in the footer |
| `screens/*.png` | Real screenshots — replace each `<div class="ph">…</div>` with `<img src="screens/name.png" alt="…">` |
| `og-image.png` | A 1200×630 preview image for social/link unfurls |
| `<link rel="canonical">` / `og:url` | Your real domain |

## Run locally

It's static — just open `index.html`, or:

```bash
python -m http.server 8000    # then visit http://localhost:8000
```

## Deploy (pick one — all free for a static site)

### GitHub Pages
1. `git init && git add -A && git commit -m "Marketing site"`
2. Create a repo (e.g. `vigil-fire-web`) and push.
3. Repo → Settings → Pages → Source: `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Add a custom domain (`vigilfire.co.za`) in the Pages settings; it writes a `CNAME` file. Point a CNAME/ALIAS DNS record at `<user>.github.io`.

### Cloudflare Pages / Netlify
Connect the repo, leave the build command empty, set the output/publish directory
to `/` (root). Add the custom domain in the dashboard.

## Suggested domains

| | Where |
|---|---|
| Marketing site (this repo) | `vigilfire.co.za` |
| The app (`Fire-Equipment-Register` repo) | `app.vigilfire.co.za` |

The "Log in" links in this site should point at the app subdomain.
