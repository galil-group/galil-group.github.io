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
| Local override of the gem's home-page layout | `_layouts/about.liquid` (title-less home page)      |
| Local override of the gem's navbar           | `_includes/header.liquid` (name on every page, not bold) |

Plugins must be listed in **both** `Gemfile` and the `plugins:` list in `_config.yml`; a plugin in only one is silently inert. When bumping `al_folio_core`, compare `_layouts/about.liquid` against the gem's new `about.liquid`.

## Local preview

With Ruby and Bundler:

    bundle install
    bundle exec jekyll serve

Then open http://localhost:4000. Or, with Docker: `docker compose up`, then open http://localhost:8080.

## Deployment (GitHub Pages)

1. The repository is `mahmoudabdelgalil/mahmoudabdelgalil.github.io`. Because it is named `<owner>.github.io`, GitHub Pages serves it at the domain root (https://mahmoudabdelgalil.github.io/), which is why `baseurl:` is blank. (Under any other repository name the site is served at `/<repo>/` and needs `baseurl: /<repo>`.)
2. On every push to `main`/`master`, `.github/workflows/deploy.yml` builds the site and pushes the output to the `gh-pages` branch.
3. In the repository settings under Pages, set the source to **Deploy from a branch → `gh-pages` / root**.
4. In `_config.yml`, set `url:` to the final address and leave `baseurl:` blank.

### Custom domain

1. Register a domain (deferred until the group is named; a personal-name domain also works meanwhile).
2. In the repository settings under Pages, add the custom domain; GitHub creates a `CNAME` file.
3. At your registrar, add the four GitHub Pages A records for the apex domain and a `CNAME` record for `www`, per the GitHub Pages documentation. Enable "Enforce HTTPS".
4. Update `url:` in `_config.yml` to the custom domain.

## Remaining TODOs

- [ ] `assets/img/prof_pic.jpg`: your photo, or a lab figure, for the landing page and team page.
- [ ] `assets/pdf/cv.pdf`: your CV. The CV links are disabled until it exists; then uncomment `cv_pdf` in `_data/socials.yml` and `_pages/cv.md`, and re-add the link in `_pages/pi.md`.
- [ ] `_bibliography/papers.bib`: paste your BibTeX entries (instructions inside the file); mark a handful with `selected={true}` for the landing page.
- [ ] `_data/socials.yml`: GitHub and ORCID if desired (Scholar, LinkedIn and ResearchGate are set).
- [ ] `_projects/*.md`: review the three research-thrust drafts; add a figure to each (`img:` field).
- [ ] `_teachings/mae341-spring2027.md`: room and section times.
- [ ] `_config.yml`: final `url:`; optionally enable analytics.
- [ ] Lab name (deferred): when chosen, set `title:` in `_config.yml`, reinstate a title on the home page (`show_title` in `_pages/about.md`, plus a subtitle with the expansion), adjust the footer/description/keywords, and register the matching domain.
## License

MIT, inherited from al-folio; see `LICENSE`.
