# CLAUDE.md — Project Context for Claude Code

## Overview
Personal academic website for **Shashank Singh** (shashanksinghnain.github.io).
Built with **Jekyll** using the **al-folio** theme, deployed via **GitHub Pages**.

## Tech Stack
- **Generator:** Jekyll 4.x (Ruby)
- **Theme:** al-folio (academic portfolio)
- **Styling:** SCSS (Bootstrap 5 + custom), CSS variables for theming
- **Font:** Lora serif (Google Fonts)
- **JS:** jQuery 3.6, Bootstrap 5, MathJax 3.2, Medium Zoom, Giscus comments
- **Package manager:** Bundler (Gemfile)
- **Deploy:** GitHub Actions → GitHub Pages (branch: master)

## Project Structure
```
_config.yml          # Main Jekyll config (site metadata, plugins, layout)
_sass/
  _variables.scss    # Color palette definitions
  _themes.scss       # Light/dark CSS variable mappings
  _base.scss         # Base element styles
  _layout.scss       # Layout styles
  _cv.scss           # CV page styles
_layouts/            # Page templates (default, about, page, post, cv, bib)
_includes/           # Partials (header, footer, head, social, scripts/)
_pages/              # Content pages (about.md, cv.md, publications.md, projects.md)
_posts/              # Blog posts
_projects/           # Project showcase pages (numbered: 1_project.md, etc.)
_news/               # News/announcement items
_bibliography/
  papers.bib         # BibTeX publication database
_data/               # YAML data (cv.yml, coauthors.yml, venues.yml, repositories.yml)
_plugins/            # Custom Ruby plugins (cache-bust, details, external-posts, etc.)
assets/
  css/               # Compiled/vendor CSS (main.scss entry point)
  js/                # JS files (dark_mode.js, theme.js, common.js, etc.)
  img/               # Images (organized in subdirs)
  pdf/               # PDFs (CV, papers)
  fonts/             # Web fonts
```

## Color Palette & Theme

### Light mode (warm paper + bronze-gold)
| Variable            | Value     | Description        |
|---------------------|-----------|--------------------|
| `$warm-paper`       | `#F5F0E1` | Background         |
| `$warm-text-ink`    | `#2B2A26` | Text               |
| `$bronze-gold`      | `#7A5A10` | Primary/links      |
| `$berkeley-blue`    | `#003262` | Accent             |
| `$warm-muted-light` | `#6B665C` | Muted/subtitle     |

### Dark mode (greyish black + Berkeley blue)
| Variable            | Value     | Description        |
|---------------------|-----------|--------------------|
| `$dark-bg`          | `#1C1C1E` | Background         |
| text                | `#FFFFFF` | White text         |
| `$dark-link`        | `#3B7EA1` | Links (Founders Rock blue) |
| `$dark-card`        | `#2C2C2E` | Card backgrounds   |
| `$dark-muted`       | `#A0A0A0` | Muted/subtitle     |

Variables defined in `_sass/_variables.scss`, mapped to CSS vars in `_sass/_themes.scss`.

## Common Commands
```bash
# Install dependencies
bundle install

# Local dev server (with live reload)
bundle exec jekyll serve --watch

# Build for production
bundle exec jekyll build --lsi

# Docker alternative
docker-compose up
```

## Key Conventions
- **Pages:** Add to `_pages/`, use front matter with `layout`, `title`, `permalink`
- **Navigation:** Set `nav: true` and `nav_order: N` in page front matter
- **Projects:** Numbered files in `_projects/` (e.g., `1_project.md`), use `importance` for ordering
- **Publications:** Managed via BibTeX in `_bibliography/papers.bib`, rendered by jekyll-scholar
- **Blog posts:** `_posts/YYYY-MM-DD-title.md`
- **News items:** `_news/announcement_N.md`
- **Dark mode:** Controlled via `data-theme` attribute on `<html>`, toggled by `assets/js/dark_mode.js`

## Important Notes
- The site uses Berkeley-inspired branding (favicon is `berkeley_logo.png`)
- PurgeCSS runs in CI to strip unused CSS — if adding new classes, check they survive purging
- Image optimization is configured (ImageMagick plugin generates 480/800/1400px responsive sizes)
- `max-width: 800px` is set in `_config.yml` for content width
- Jekyll Scholar manages bibliography with Altmetric/Dimensions badges
- MathJax is available for math rendering in posts/pages
