# CLAUDE.md

Research-group website of Prof. Mahmoud Abdelgalil (UB MAE), built on al-folio v1 (Jekyll). See `README.md` for where content lives, local preview, deployment, and the open TODO list.

## How this repo is put together

- All runtime (layouts, includes, Sass, JS, Liquid tags) comes from version-pinned `al_*` gems in `Gemfile`; `theme: al_folio_core` in `_config.yml`. This repo holds config and content only.
- The one intentional local override is `_layouts/about.liquid` (title-less home page). Other local overrides should be avoided; when bumping `al_folio_core`, diff this file against the gem's `about.liquid`.
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

Deployment is automatic: pushing to `main`/`master` runs `.github/workflows/deploy.yml` (build, purge CSS with `purgecss.config.js`, publish `_site` to the `gh-pages` branch).
