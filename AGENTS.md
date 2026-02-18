# Agent Instructions for rsnemmen.github.io

This is a Jekyll-based personal website using the [al-folio](https://github.com/alshedivat/al-folio) theme.

## Build Commands

### Local Development
```bash
# Using Docker (recommended)
docker compose pull
docker compose up

# Using Docker slim image (beta, <100MB)
docker compose -f docker-compose-slim.yml up

# Build your own docker image
docker compose up --build
```

### Jekyll Commands
```bash
# Install dependencies
bundle install

# Serve locally (legacy, requires Ruby/Bundler)
bundle exec jekyll serve

# Build site
bundle exec jekyll build

# Build with specific destination
bundle exec jekyll build --destination <path>
```

### CSS Purging
```bash
# Remove unused CSS classes after build
purgecss -c purgecss.config.js
```

## Lint/Format Commands

### Prettier (Required for all PRs)
```bash
# Install dependencies
npm install

# Check formatting
npx prettier . --check

# Fix formatting issues
npx prettier . --write
```

### Pre-commit Hooks
```bash
# Install pre-commit hooks
pre-commit install

# Run all hooks
pre-commit run --all-files
```

## Code Style Guidelines

### Formatting (Prettier)
- All code must pass Prettier checks before PR acceptance
- Print width: 150 characters
- Trailing commas: ES5 compatible
- Plugins: `@shopify/prettier-plugin-liquid` for Liquid templates
- Configuration: `.prettierrc`

### Liquid Templates
- Use `.liquid` extension for all templates
- Indent with 2 spaces
- Use `{{-` and `-}}` for whitespace control when needed
- Follow existing naming: `_layouts/`, `_includes/`

### SCSS/CSS
- Located in `_sass/` directory
- Main entry: `assets/css/main.scss`
- Variables defined in `_sass/_variables.scss`
- Themes in `_sass/_themes.scss`
- Use compressed style in production

### Jekyll Configuration
- Main config: `_config.yml`
- Use YAML front matter for page metadata
- Collections: `news`, `projects`, `books`
- Exclude build files and docs from site generation

### Naming Conventions
- Layouts: lowercase with hyphens (e.g., `book-review.liquid`)
- Includes: descriptive names (e.g., `latest_posts.liquid`)
- Sass partials: underscore prefix (e.g., `_base.scss`)
- Data files: YAML or JSON in `_data/`

### Content Guidelines
- Posts: Markdown in `_posts/` with date prefix (`YYYY-MM-DD-title.md`)
- Pages: Markdown in `_pages/`
- Projects: Markdown in `_projects/`
- Bibliography: BibTeX in `_bibliography/papers.bib`
- Images: `assets/img/`
- PDFs: `assets/pdf/`

### Front Matter Standards
```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD HH:MM:SS +/-TTTT
description: Brief description for previews
tags: [tag1, tag2]
categories: category-name
---
```

### Link Handling
- External links: automatically get `rel="external nofollow noopener" target="_blank"`
- Internal links: use relative paths
- Check for broken links with `lychee`

### Git Workflow
1. Create feature branch from `main`
2. Make changes
3. Run `npx prettier . --write` to format
4. Commit and push
5. Create PR to `main`
6. GitHub Actions auto-deploys to `gh-pages` branch

### Security
- Never commit secrets or API keys
- Use GitHub secrets for sensitive data in Actions
- Google Analytics ID is public in `_config.yml`

### Accessibility
- Run Axe checks manually for accessibility testing
- Ensure proper alt text for images
- Maintain semantic HTML structure

## Testing

### Link Checking
- Automated via GitHub Actions using `lychee`
- Configured in `.github/workflows/broken-links.yml`

### Accessibility Testing
- Manual Axe testing recommended
- Workflow in `.github/workflows/axe.yml`

## Project Structure
```
├── _bibliography/    # BibTeX references
├── _books/           # Book review posts
├── _data/            # YAML/JSON data files
├── _includes/        # Liquid include templates
├── _layouts/         # Page layouts
├── _news/            # News items
├── _pages/           # Static pages
├── _plugins/         # Jekyll plugins
├── _posts/           # Blog posts
├── _projects/        # Project showcases
├── _sass/            # SCSS stylesheets
├── assets/           # Images, CSS, JS, JSON
└── .github/          # GitHub Actions workflows
```

## Important Notes
- **Never edit `gh-pages` branch directly** - it's auto-generated
- Site deploys automatically on push to `main`
- Docker setup is the recommended local development method
- Prettier formatting is enforced in CI/CD
