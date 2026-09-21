# Working with this website

Personal website of Lukas Röseler, built with **Quarto** and deployed via **GitHub Pages**.

- Live: https://lukasroeseler.github.io/home/
- Repo: https://github.com/LukasRoeseler/home (branch `main`)
- Local copy: `...\sciebo ...\LeaRn\home`

## Project layout

- `*.qmd` — **source** files (edit these). `index.qmd`, `research.qmd`, `openscience.qmd`, `collaborate.qmd`, etc. If you add a new page, also add it to the `project.render` list in `_quarto.yml` (and to the navbar) so it gets built.
- `_quarto.yml` — site config (navbar, theme, favicon, resources).
- `custom.scss` — theming (header/nav colors).
- `_include-header.html` — injected into every page `<head>` (dark-mode toggle, favicon links).
- `docs/` — **generated** output. Do NOT hand-edit these; they are produced by `quarto render`.
- `favicon.*` — site favicon (black "LR" on blue `#03a1fc`).

## How to make a change

1. Edit the **`.qmd` source** file (never the generated `docs/*.html`).
2. Re-render locally: `quarto render`
3. Verify the result in `docs/`.
4. Commit the source `.qmd` AND the regenerated `docs/` files, then push to `main`.

```
git add -A
git commit -m "Describe the change"
git push origin main
```

5. GitHub Pages rebuilds automatically from the `main` branch `/docs` folder. It can take 1–3 minutes to go live.

## ⚠️ Deployment gotchas

- **The site is served from the `main` branch, `/docs` directory** (GitHub Pages → Deploy from a branch → `main` → `/docs`).
- **Do NOT edit `docs/*.html` by hand.** The `*.qmd` sources are the source of truth. Hand-edited HTML is overwritten by the next render and leaves the source out of sync (this caused the earlier "changes never went live" issue).
- The GitHub Actions workflow `.github/workflows/publish.yml` renders the site and publishes to the `gh-pages` branch, but **`gh-pages` is NOT the branch that serves the site**. Ignore it unless you change the Pages config.
- If you change `index.qmd` (or any source) without re-rendering, the live page will not update — `docs/` must be regenerated and committed.
- If you change a `.qmd` that references `research_data.js`, regenerate it first: `Rscript make_data.R`.

## Favicon

- Files live in the repo root: `favicon.ico`, `favicon.svg`, `favicon-16x16.png` … `favicon-256.png`.
- Referenced in `_quarto.yml` (`website.favicon: favicon.ico`) and listed under `project.resources`.
- Extra SVG/PNG links are added in `_include-header.html`.
- To change it, regenerate the assets and keep the same filenames.
