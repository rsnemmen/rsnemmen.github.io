# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Jekyll-based academic portfolio site built on the [al-folio theme](https://github.com/alshedivat/al-folio), deployed to GitHub Pages. It belongs to Rodrigo Nemmen (astrophysicist/ML researcher at USP).

## Build & Development Commands

**Preferred: Docker (recommended)**
```bash
docker compose pull && docker compose up
# Visit http://localhost:8080
```

**Without Docker:**
```bash
bundle install
pip install jupyter
bundle exec jekyll serve
# Visit http://localhost:4000
```

**Production build (mirrors CI):**
```bash
bundle exec jekyll build
npm install -g purgecss
purgecss -c purgecss.config.js
```

**Code formatting:**
```bash
npx prettier --write .   # Formats HTML/Liquid files
```

## Architecture

### Content Organization

- `_pages/` — Standalone pages (about, blog, publications, research, teaching, llm-ranking, etc.)
- `_projects/` — Portfolio items with `importance` (sort order) and `category` (`work` or `fun`) front matter
- `_posts/` — Blog posts; external posts also pulled via RSS (see `_plugins/external-posts.rb`)
- `_news/` — Short announcements shown on the home page
- `_bibliography/papers.bib` — All publications in BibTeX; Jekyll Scholar auto-generates publication pages
- `_data/` — Structured data: `cv.yml`, `coauthors.yml`, `socials.yml`, `repositories.yml`, `venues.yml`

### Key Configuration

`_config.yml` controls everything: site metadata, theme colors, feature flags (dark mode, MathJax, progressbar), analytics (Google Analytics `G-F50ZY4YMNF`), Jekyll Scholar settings, external RSS feed URLs, and CDN links for third-party libraries.

### Custom Plugins (`_plugins/`)

| Plugin | Purpose |
|--------|---------|
| `external-posts.rb` | Fetches posts from Bear blog RSS feeds |
| `google-scholar-citations.rb` | Pulls citation counts |
| `inspirehep-citations.rb` | Inspire HEP integration |
| `cache-bust.rb` | Asset cache busting |
| `details.rb` | Collapsible `<details>` sections in Markdown |

### Navigation & Pages

Navbar items are controlled by front matter in `_pages/`:
```yaml
nav: true
nav_order: 3
dropdown: true        # optional
children:             # optional dropdown items
  - title: Sub Item
    permalink: /sub/
```

### Publications

Publications live in `_bibliography/papers.bib`. Jekyll Scholar renders them with Altmetric, Dimensions, Google Scholar, and Inspire HEP badges. The `_data/coauthors.yml` file maps co-author names to their profile links.

### Images

All images are auto-converted to WebP at multiple widths (480, 800, 1400px) by `jekyll-imagemagick`. ImageMagick must be installed locally for this to work during local builds.

## Deployment

GitHub Actions (`.github/workflows/deploy.yml`) builds and deploys on push to `main`. The workflow uses Ruby 3.3.5, Python 3.13, installs ImageMagick, runs `bundle exec jekyll build` with `JEKYLL_ENV=production`, purges unused CSS with PurgeCSS, then deploys to GitHub Pages.

Other active workflows: Prettier formatting checks, broken link detection (lychee), Lighthouse performance scoring, Docker image builds.
