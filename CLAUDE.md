# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Personal website for Pierdomenico Fiadino — a Hugo static site using the [Blowfish](https://github.com/nunocoracao/blowfish) theme, deployed to GitHub Pages at https://www.fiadino.org/.

## Commands

```bash
# Local development server with live reload
hugo server

# Build for production
hugo --minify --baseURL "https://www.fiadino.org/"
```

Deployment is fully automated: push to `master` triggers GitHub Actions (`.github/workflows/hugo.yml`) which builds and deploys to GitHub Pages.

## Architecture

**Configuration** lives in `config/_default/` as TOML files:
- `config.toml` — base URL, theme, pagination, taxonomies
- `params.toml` — Blowfish theme parameters (dark theme, layouts, analytics)
- `languages.en.toml` — site title, author metadata, social links
- `menus.en.toml` — navigation structure (Home, About me, Experience, Education, Publications)
- `markup.toml` — Goldmark with unsafe HTML enabled (required for inline HTML in content)

**Content** (`content/`) uses HTML files with YAML frontmatter. All pages use the custom `simple_custom` layout (`layout: "simple_custom"`). Content is written as HTML, not Markdown, to allow fine-grained styling.

**Customizations** over the base Blowfish theme:
- `layouts/_default/simple_custom.html` — custom article layout with hero image, breadcrumbs, TOC, and sharing links
- `layouts/partials/extend-head.html` — injects LinkedIn badge script, FontAwesome v5.12.1, and custom CSS
- `static/css/custom.css` — site-specific styles

**Theme** is a git submodule at `themes/blowfish/`. After cloning, run `git submodule update --init` if the theme directory is empty.

**Static assets**: papers (PDFs) in `static/papers/`, profile images in `static/img/` and `assets/img/` (the latter go through Hugo's asset pipeline for optimization).
