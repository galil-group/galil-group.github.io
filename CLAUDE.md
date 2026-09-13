# CLAUDE.md

Research-group website of Mahmoud Abdelgalil (UB MAE), built on al-folio v1 (Jekyll). Content lives in `_pages/`, `_projects/`, `_teachings/`, `_news/`, `_bibliography/papers.bib`, `_data/` and `assets/`; site settings are in `_config.yml`.

## How this repo is put together

- All runtime (layouts, includes, Sass, JS, Liquid tags) comes from version-pinned `al_*` gems in `Gemfile`; `theme: al_folio_core` in `_config.yml`. This repo holds config and content only.
- Two intentional local overrides of `al_folio_core` files: `_layouts/about.liquid` (lets the home page hide its title, and renders the social icons under the photo instead of at the bottom) and `_includes/header.liquid` (shows the name in the navbar on the home page too, where upstream hides it, drops upstream's bold first name, and turns the navbar into a fixed left sidebar on screens at least 992px wide, with the name on one line and the social icons under the menu links; below 992px the icons sit in the top bar (inside the collapsed menu on phones), and the home page sets `social: false` so it shows no icons under the photo; it also hides the theme's copyright footer on every page). Avoid adding others; when bumping `al_folio_core`, diff both against the gem's versions.
- Upstream docs (config reference, plugin ownership, troubleshooting): https://github.com/alshedivat/al-folio/tree/main/docs

## Things that fail silently

1. A feature renders only when its gem is in `Gemfile`, **and** it is in the `plugins:` list of `_config.yml`, **and** its flag is on. Otherwise its Liquid tag emits nothing. Add or remove plugins in both files.
2. `baseurl:` is blank because the site is served at a domain root. Do not set it to `/al-folio` (the upstream demo value).
3. Never use `%` comments in `_bibliography/papers.bib`; bibtex-ruby does not treat them as comments and the build fails. Use an `@comment{...}` block with no `@` inside.

## Commands

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
bundle exec jekyll build   # output in _site/
docker compose up          # alternative preview at http://localhost:8080
```

Deployment is automatic: pushing to `main`/`master` runs `.github/workflows/deploy.yml` (build, purge CSS with `purgecss.config.js`, publish `_site` to the `gh-pages` branch). The site is served at the custom domain https://www.maabdelg.me: the `CNAME` file must stay in the repo (each deploy replaces the whole `gh-pages` branch) and match `url:` in `_config.yml`. DNS is managed at Squarespace (`www` CNAME to `mahmoudabdelgalil.github.io`, apex A records to GitHub Pages).
