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

**Content** (`content/`) uses HTML files with YAML frontmatter. All pages use the custom `simple_custom` layout (`layout: "simple_custom"`). Content is written as HTML, not Markdown, to allow fine-grained styling. The homepage is `content/_index.md` — its `.Content` renders inside the Blowfish `background` layout hero section.

**Customizations** over the base Blowfish theme:
- `layouts/_default/simple_custom.html` — custom article layout with hero image, breadcrumbs, TOC, and sharing links
- `layouts/partials/extend-head.html` — injects FontAwesome v5.12.1, custom CSS, and SEO meta keywords
- `layouts/partials/extend-footer.html` — currently empty; reserved for site-wide footer injections
- `layouts/partials/home/background.html` — overrides the Blowfish homepage hero partial; adds `padding-top: 28vh` (inline style) to push the name/headline to mid-page. Inline style is required because Blowfish's Tailwind CSS purges arbitrary utility classes not present at theme build time.
- `static/css/custom.css` — site-specific styles

**CSS caching caveat**: `custom.css` is served with aggressive browser caching in local dev. When adding new CSS rules, embed them in an inline `<style>` block directly in the relevant content HTML file as well — this ensures they take effect immediately without a cache-bust.

**Theme** is a git submodule at `themes/blowfish/`. After cloning, run `git submodule update --init` if the theme directory is empty.

**Static assets**: papers (PDFs) in `static/papers/`, talk slides in `static/talks/`, downloadable CV at `static/resume.pdf`, profile images in `static/img/` and `assets/img/` (the latter go through Hugo's asset pipeline for optimization).

**Custom RSS/Sitemap**: `layouts/_default/rss.xml` and `layouts/_default/sitemap.xml` override the Blowfish defaults.

**Mastodon/ActivityPub verification**: `static/.well-known/webfinger` — serves the WebFinger JSON for Mastodon identity verification (`@herr_dr@hachyderm.io`). Do not delete or move this file.

## Alternate pages (retro & terminal)

Both pages follow the same pattern: self-contained single HTML files under `static/`, served verbatim by Hugo at their respective paths. No templating or theme processing applies. All CSS and JavaScript are inline.

### `static/retro/index.html` → `fiadino.org/retro`
90s-style alternate version with a dark cosmic palette. Contains a parallel copy of the career history, bio, skills, education, and publications. **Must be updated manually** when main content changes.

Things to keep in sync:
- Current role title and company (header tagline, About section, Experience timeline, 88×31 badge row)
- Employment dates and job descriptions (Experience timeline)
- Bio text (About section)
- Copyright year (footer `© 1997–YYYY`)
- The header comment and Konami easter egg alert both reference the current year

Notable features: animated starfield canvas background, 56k modem photo-loading effect (IntersectionObserver + `clip-path` reveal with glowing scan line), skill bars animated on scroll, visitor counter via `localStorage`, Konami code easter egg.

### `static/terminal/index.html` → `fiadino.org/terminal`
Modern terminal-themed version using the Dracula palette on pure black, styled after powerlevel10k/oh-my-posh. Contains a parallel copy of the same content.

Things to keep in sync with the main site:
- Current role (neofetch info block, btop process table)
- Employment history (btop process table — each job is a process row)
- Education (systemd daemon status blocks)
- Bio / uptime (neofetch — uptime is calculated from birth date June 1987)
- Publications (BibTeX-style listing)

Notable features: macOS-style title bar with a `← fiadino.org` back link, powerlevel10k two-line prompt (`╭─`/`╰─❯`), neofetch block with rainbow ASCII logo, btop-style experience table (`grid-template-columns: 54px 36px 172px 82px 112px 1fr 80px`), systemd education blocks, interactive JS terminal (commands: `help`, `about`, `ls`, `contact`, `cv`, `hire piero`, `fortune`, `uname -a`, `clear`, `exit`), Konami code easter egg.

### Theme-aware logos (jobs page)
Company logos in `content/jobs.html` use a two-`<img>` pattern toggled by CSS:
```css
.logo-dark { display: none; }
.dark .logo-dark { display: inline; }
.dark .logo-light { display: none; }
```
Both the `custom.css` entry and an inline `<style>` block in `jobs.html` carry these rules (the inline block bypasses browser caching in local dev).
