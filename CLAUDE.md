# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Brendan Meade's academic homepage (https://brendanjmeade.github.io), built on the
[al-folio](https://github.com/alshedivat/al-folio) Jekyll theme. The `README.md` is the
upstream theme README, not documentation for this site. Content lives in `_pages/`,
`_bibliography/papers.bib`, `_data/pubimg.yaml`, and `assets/`; almost everything else is
theme scaffolding.

## Commands

There is no test suite or linter. The build is the check.

```bash
bundle install                 # first time; needs Ruby 3.x (CI uses 3.2.2) and ImageMagick
bundle exec jekyll serve       # local preview at http://localhost:4000
bundle exec jekyll build       # static output to _site/ (what CI runs, see bin/cibuild)
```

The system Ruby on this Mac is 2.6 and `jekyll` is not on the PATH, so a local build
needs a newer Ruby (e.g. via rbenv) before `bundle install` will work. `Gemfile.lock` is
gitignored; CI resolves gems fresh.

## Deployment

Pushing to `master` triggers `.github/workflows/deploy.yml`, which runs `bin/deploy`.
That script builds the site and force-pushes the contents of `_site/` to the `gh-pages`
branch, which GitHub Pages serves. Pull requests run the same build with `--no-push`.
Never commit to `gh-pages` by hand. Never run `bin/deploy` locally unless you intend to
overwrite the live site.

The workflow installs ImageMagick because `_config.yml` enables `jekyll-imagemagick`,
which generates WebP variants for images under `assets/img/`.

## Publications pipeline (the main thing that changes)

Publications are rendered by jekyll-scholar from `_bibliography/papers.bib` through the
custom `_layouts/bib.html`. Adding a paper touches three places, and the recent git history
shows this exact pattern:

1. Append a `@article` entry to `_bibliography/papers.bib`. Every entry carries
   `abbr`, `abstract`, `bibtex_show = {true}`, `html`, and usually `doi`.
2. Add a line `<abbr>: <abbr>.png` to `_data/pubimg.yaml`.
3. Drop the thumbnail at `assets/pubimg/<abbr>.png`.

The `abbr` field is repurposed: in stock al-folio it is a journal badge, but here
`_layouts/bib.html` uses it as the lookup key into `site.data.pubimg` to find the
thumbnail image. `abbr` is usually identical to the BibTeX key.

`_pages/publications.md` groups entries by a hard-coded `years:` list in its front matter.
A paper with a year not in that list will not appear, so add the year when adding the
first paper of a new year.

Quirks to know about before "fixing" them:

- `_config.yml` still has `scholar.last_name: Einstein` from the theme. This means the
  author self-highlighting in `bib.html` never fires for Meade. `_data/coauthors.yml` is
  likewise theme placeholder data.

## Site structure

- `_pages/`: about (root `/`), people, publications, software, teaching. A page appears
  in the navbar when its front matter has `nav: true`; the navbar sorts pages by title.
- `_pages/about.md` sets `news: false` and `selected_papers: false`, so `_news/` and the
  `selected=true` bib query are inert. `_projects/` is unused theme sample content, and
  the blog is disabled (`blog_name` is blank in `_config.yml`).
- `_data/pubimg.yaml` maps publication keys to thumbnail filenames (see above).
- `_plugins/`: theme-provided minify/beautify filters and an external-posts generator,
  all effectively off (`minify: false`, no `external_sources`).
- `_sass/`, `_layouts/`, `_includes/`: theme files. The known local customization is the
  `pubimg` thumbnail lookup in `_layouts/bib.html`.
