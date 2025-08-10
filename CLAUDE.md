# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an academic personal website built using the **al-folio** Jekyll theme, hosted on GitHub Pages. The site showcases academic work including publications, CV, teaching, and research activities for Esteban Carisimo, a PhD student at Northwestern University.

## Development Commands

### Local Development (Recommended: Docker)

```bash
# Pull and run with Docker (recommended)
docker compose pull
docker compose up

# Slim version (smaller image)
docker compose up -f docker-compose-slim.yml

# Build custom docker image
docker compose up --build
```

### Local Development (Legacy)

```bash
# Install dependencies
bundle install
pip install jupyter

# Serve locally with live reload
bundle exec jekyll serve --lsi
```

### Code Quality

```bash
# Format code with Prettier
npx prettier . --check
npx prettier . --write

# Install Prettier dependencies
npm install --save-dev --save-exact prettier @shopify/prettier-plugin-liquid
```

## Architecture & Key Components

### Jekyll Structure

- `_config.yml` - Main site configuration including personal info, social links, and theme settings
- `_pages/` - Main pages (about, CV, publications, teaching, etc.)
- `_data/` - YAML data files (cv.yml, repositories.yml, venues.yml, coauthors.yml)
- `_bibliography/` - BibTeX files for publications (papers.bib, students.bib, talks.bib)
- `_includes/` - Reusable Liquid templates and components
- `_layouts/` - Page layout templates
- `_sass/` - Stylesheet files
- `assets/` - Static assets (images, PDFs, CSS, JS)

### Content Management

- **Publications**: Managed through BibTeX files in `_bibliography/`. Supports additional fields like `pdf`, `slides`, `poster`, `code`, etc.
- **CV**: Two options - JSON resume format (`assets/json/resume.json`) or YAML format (`_data/cv.yml`)
- **News**: Individual markdown files in `_news/`
- **Projects**: Individual markdown files in `_projects/`

### Key Configuration Areas

- Personal information and social links: `_config.yml` (lines 5-100)
- Publication settings: `_config.yml` Jekyll Scholar section
- Theme colors: `_sass/_themes.scss` and `_sass/_variables.scss`

## Content Locations

### Academic Content

- **Papers PDFs**: `assets/pdf/papers/`
- **Posters**: `assets/pdf/posters/`
- **Slides**: `assets/pdf/slides/`
- **CV PDF**: `assets/pdf/CV.pdf`
- **Job Market Materials**: `assets/pdf/job-market-2024/`

### Media Assets

- **Profile Images**: `assets/img/` (main profile pic: `EC.jpg`)
- **Publication Previews**: `assets/img/publication_preview/`

## New Features (from al-folio v0.14.x)

### Search Functionality
- **Search enabled**: Full-text search across publications, news, and pages
- **Bib search**: Searchable bibliography with keyword filtering
- **Social search**: Search integration with social media profiles
- Configuration: `search_enabled: true`, `bib_search: true`, `socials_in_search: true`

### Enhanced Social Media Integration
- **New platforms**: Bluesky, IEEE, ACM, Inspire HEP, Flickr support
- **Academic profiles**: Enhanced Google Scholar, ResearchGate, ORCID integration
- **Professional networks**: LinkedIn, Discord, Telegram support

### Publication Enhancements
- **Google Scholar badges**: Automatic citation count display
- **Inspire HEP badges**: High-energy physics citation metrics
- **Award annotations**: Support for `award` and `award_name` fields in bibtex
- **Additional metadata**: Support for `google_scholar_id`, `inspirehep_id` fields

### Visualization Tools
- **Chart.js**: Interactive charts and graphs
- **ECharts**: Advanced data visualization
- **Plotly.js**: Scientific plotting support
- **Vega-lite**: Grammar of interactive graphics
- **Advanced image viewers**: Enhanced image display capabilities

### Code Quality & Development
- **Jekyll-tabs**: Tabbed content support
- **Jekyll-regex-replace**: Text processing enhancements
- **CSS parser**: Improved stylesheet processing
- **Enhanced Prettier**: Better Liquid template formatting

### Analytics & Monitoring
- **Pirsch Analytics**: Privacy-focused analytics option
- **Enhanced Lighthouse**: Better performance monitoring
- **Improved GitHub Actions**: More reliable CI/CD pipeline

## Development Notes

### Deployment

- Automatic deployment via GitHub Actions on push to master/main branch
- Site builds and deploys to `gh-pages` branch
- Live site: https://estcarisimo.github.io

### Dependencies

- **Jekyll** with multiple plugins (scholar, archives, feed, tabs, regex-replace, etc.)
- **Ruby/Bundler** for gem management
- **Node.js/npm** for Prettier formatting
- **Python/pip** for Jupyter notebook support

### Code Quality Tools

- **Prettier** for code formatting (includes Liquid template support)
- **GitHub Actions** workflows for CI/CD, formatting checks, and broken link detection
- **Lighthouse** for performance monitoring
- **Search functionality** with JavaScript-based indexing

## Customization Patterns

- Social media links configured in `_config.yml` with expanded platform support
- Color themes in `_sass/_themes.scss` using CSS custom properties
- Bibliography styling controlled through Jekyll Scholar configuration
- Responsive design using Bootstrap grid system
- Search customization through `assets/js/search/` directory
- Visualization integration through CDN-hosted libraries
