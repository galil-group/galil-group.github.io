# Research-group website: deployment notes

This repository is a customized [al-folio](https://github.com/alshedivat/al-folio) site.

## First deployment (GitHub Pages)

1. Create the repository under your personal account for now; a lab organization can adopt it later once the group is named.
2. Create a repository named `<owner>.github.io` (site served at the root URL) and push this
   repository's contents to its `main` branch.
3. In the repository settings, under Pages, set the source to "GitHub Actions". The included
   workflow (`.github/workflows/`) builds and deploys the site on every push to `main`.
4. Edit `_config.yml`: set `url:` to the final address and leave `baseurl:` blank.

## Custom domain (recommended)

1. Register a domain (deferred until the group is named; a personal-name domain also works meanwhile).
2. In the repository settings under Pages, add the custom domain; GitHub creates a `CNAME` file.
3. At your registrar, add the four GitHub Pages A records for the apex domain and a `CNAME`
   record for `www`, per the GitHub Pages documentation. Enable "Enforce HTTPS".
4. Update `url:` in `_config.yml` to the custom domain.

## Local preview

Requires Ruby and Bundler (or use the provided `docker-compose.yml`):

    bundle install
    bundle exec jekyll serve

Then open http://localhost:4000.

## Remaining TODOs

- [ ] `assets/img/prof_pic.jpg`: your photo, or a lab figure, for the landing page and people page.
- [ ] `assets/pdf/cv.pdf`: your CV.
- [ ] `_bibliography/papers.bib`: paste your BibTeX entries (instructions inside the file);
      mark a handful with `selected={true}` for the landing page.
- [ ] `_data/socials.yml`: Google Scholar ID, GitHub, ORCID, LinkedIn as desired.
- [ ] `_projects/*.md`: review the four research-thrust drafts; add a figure to each (`img:` field).
- [ ] `_teachings/mae341-fall2026.md`: room and second-section time.
- [ ] `_config.yml`: final `url:`; optionally enable analytics.
- [ ] Lab name (deferred): when chosen, set `title:` in `_config.yml`, reinstate a title on the
      home page (`show_title` in `_pages/about.md`, plus a subtitle with the expansion), adjust
      the footer/description/keywords, and register the matching domain.
- [ ] Verify DYNAMO publicity provisions before adding a DARPA logo; the textual funding
      acknowledgment on the landing page is standard.
