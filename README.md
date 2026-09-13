# Research-group website

Website of Mahmoud Abdelgalil's research group, Department of Mechanical and Aerospace Engineering, University at Buffalo (SUNY).

Built with [Jekyll](https://jekyllrb.com/) on [al-folio](https://github.com/alshedivat/al-folio) v1. In v1, layouts, styles and scripts ship as version-pinned `al_*` gems (see `Gemfile`), so this repository holds only configuration and content. Upstream documentation: <https://github.com/alshedivat/al-folio/tree/main/docs>.

## Where things live

| What                                         | File(s)                                             |
| -------------------------------------------- | --------------------------------------------------- |
| Site settings, feature flags, plugin list    | `_config.yml`                                       |
| Home page / team page / PI bio               | `_pages/about.md`, `_pages/profiles.md`, `_pages/pi.md` |
| Research thrusts                             | `_projects/*.md`                                    |
| Courses                                      | `_teachings/*.md`                                   |
| News items                                   | `_news/*.md`                                        |
| Blog posts (none yet)                        | `_posts/`                                           |
| Publications                                 | `_bibliography/papers.bib`                          |
| CV (rendered page), social links             | `_data/cv.yml`, `_data/socials.yml`                 |
| Venue badges, coauthor links                 | `_data/venues.yml`, `_data/coauthors.yml`           |
| Images and PDFs                              | `assets/img/`, `assets/pdf/`                        |
| Local override of the gem's home-page layout | `_layouts/about.liquid` (title can be hidden; social icons under the photo) |
| Local override of the gem's navbar           | `_includes/header.liquid` (name on every page, not bold) |

Plugins must be listed in **both** `Gemfile` and the `plugins:` list in `_config.yml`; a plugin in only one is silently inert. When bumping `al_folio_core`, compare `_layouts/about.liquid` against the gem's new `about.liquid`.

## Local preview

With Ruby and Bundler:

    bundle install
    bundle exec jekyll serve

Then open http://localhost:4000. Or, with Docker: `docker compose up`, then open http://localhost:8080.

## Deployment (GitHub Pages)

1. The repository is `mahmoudabdelgalil/mahmoudabdelgalil.github.io`; the site is served at the root of its custom domain, https://www.maabdelg.me/, which is why `baseurl:` is blank.
2. On every push to `main`/`master`, `.github/workflows/deploy.yml` builds the site and pushes the output to the `gh-pages` branch.
3. In the repository settings under Pages, set the source to **Deploy from a branch → `gh-pages` / root**.
4. `url:` in `_config.yml` is the canonical address (`https://www.maabdelg.me`); keep `baseurl:` blank.

### Custom domain (www.maabdelg.me)

- The `CNAME` file in the repo root holds `www.maabdelg.me`. It must stay in the repo: each deploy replaces the whole `gh-pages` branch, so a domain set only in the GitHub settings would be wiped. Keep it in sync with `url:` in `_config.yml`.
- DNS (managed at Squarespace): a `CNAME` record `www` → `mahmoudabdelgalil.github.io`, and for the apex `maabdelg.me` the GitHub Pages `A` records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (optionally `AAAA` `2606:50c0:8000::153` through `2606:50c0:8003::153`), so the apex redirects to `www`.
- In the repository settings under Pages, the custom domain is `www.maabdelg.me` with "Enforce HTTPS" on. Verifying the domain in the GitHub account settings (Pages → Add a domain, a `TXT` record) protects it from takeover.

## Remaining TODOs

- [ ] `assets/img/prof_pic.jpg`: your photo, or a lab figure, for the landing page and team page.
- [ ] `assets/pdf/cv.pdf`: your CV. The CV links are disabled until it exists; then uncomment `cv_pdf` in `_data/socials.yml` and `_pages/cv.md`, and re-add the link in `_pages/pi.md`.
- [ ] `_bibliography/papers.bib`: paste your BibTeX entries (instructions inside the file); mark a handful with `selected={true}` for the landing page.
- [ ] `_data/socials.yml`: GitHub and ORCID if desired (Scholar, LinkedIn and ResearchGate are set).
- [ ] `_projects/*.md`: review the three research-thrust drafts; add a figure to each (`img:` field).
- [ ] `_teachings/mae341-spring2027.md`: room and section times.
- [ ] `_config.yml`: optionally enable analytics.
- [ ] Lab name (deferred): when chosen, set `title:` in `_config.yml`, reinstate a title on the home page (`show_title` in `_pages/about.md`, plus a subtitle with the expansion), and adjust the footer/description/keywords.
## License

MIT, inherited from al-folio; see `LICENSE`.
