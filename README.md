# zsazsa-project website

The public website for the open-source [zsazsa](https://github.com/cudeso/zsazsa/) CTI program management platform.

It is a **static, dependency-free site**: plain HTML and one CSS file. There is no build step. Styling mirrors the zsazsa application's *UiBeta* theme (MISP-style light surfaces, `#0066cc` accent, Inter typography, the shield brand glyph).

## Structure

```
index.html            Home / hero + overview
features.html         Feature tour (from the repo + README)
documentation.html    Install / run / deploy / config (from the README)
download.html         Points to GitHub
news.html             Blog posts (published on the MISP project site)
contact.html          GitHub + info@zsazsa-project.org
assets/css/site.css   Theme + layout
assets/img/           Screenshots (copied from the zsazsa docs/ folder)
CNAME                 Custom domain for GitHub Pages
.nojekyll             Serve files as-is (skip Jekyll processing)
robots.txt, sitemap.xml
```

## Preview locally

No tooling needed. Either open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Hosting on GitHub Pages (recommended)

Static HTML on GitHub Pages is the simplest fit: free, no build step, and it supports the `zsazsa-project.org` custom domain.

1. Create a repository (for example `cudeso/zsazsa-project`) and push these files to the `main` branch.
2. In **Settings → Pages**, set *Source* to **Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The included `CNAME` file sets the custom domain to `zsazsa-project.org`. At your DNS provider, add either:
   - an `ALIAS`/`ANINAME` (or apex `A`) record pointing at GitHub Pages' IPs, and
   - a `CNAME` for `www` → `<user>.github.io`.
   GitHub's docs list the current Pages IP addresses. Once DNS resolves, tick **Enforce HTTPS**.
4. If you do **not** want a custom domain, delete `CNAME` and the site will serve from `https://<user>.github.io/<repo>/`. In that case, because the pages use root-relative-free *relative* links, they work from a subpath as-is.

> A dedicated `zsazsa-project` repo keeps the website history separate from the application repo. Alternatively, a `gh-pages` branch in the main repo also works.

### Other options

- **Cloudflare Pages or Netlify**: drag-and-drop or git-connected, also free for static sites, with the custom domain managed in their dashboard. Same files, no changes needed (remove `CNAME` and `.nojekyll`, which are GitHub-specific).

## Updating content

- **Features / docs** are hand-maintained from the zsazsa `README.md`. When the README changes materially, mirror the relevant edits here.
- **Screenshots** live in `assets/img/` and were copied from the application's `docs/` folder. Replace them there to refresh.
- **News** entries are added by editing `news.html`.
