# AGENTS.md

Project documentation for LLM agents working on this repository.

## Project Overview

**Site:** 84EM.AI
**Domain:** https://84em.ai
**Purpose:** Personal AI resource site sharing AI workflows, discoveries, tool reviews, and practical applications
**Author:** Andrew Miller (also runs [84EM](https://84em.com), a WordPress development consultancy)
**Tone:** Direct, practical, no-hype. Written by a developer for developers.

## Tech Stack

- **Static Site Generator:** Hugo (no theme, custom templates)
- **CSS:** Single hand-written file, processed via Hugo Pipes
- **JavaScript:** None
- **Fonts:** System font stack (no web fonts)
- **Hosting:** Static files (deploy `public/` directory)

## Commands

```bash
# Development server with live reload
hugo server -D

# Build for production
hugo

# Create new post
hugo new content posts/my-post-slug.md
```

## Directory Structure

```
84em.ai/
├── archetypes/
│   └── default.md          # Frontmatter template for new content
├── assets/
│   └── css/
│       └── main.css        # Single stylesheet (Hugo Pipes processed)
├── content/
│   ├── about.md            # About page
│   └── posts/
│       ├── _index.md       # Posts section config
│       └── *.md            # Blog posts
├── layouts/
│   ├── _default/
│   │   ├── baseof.html     # Base template
│   │   ├── list.html       # Section/taxonomy lists
│   │   └── single.html     # Individual pages/posts
│   ├── partials/
│   │   ├── head.html       # <head> content, CSS, favicons
│   │   ├── header.html     # Site header with nav
│   │   ├── footer.html     # Site footer
│   │   ├── meta.html       # OG, Twitter, SEO meta tags
│   │   └── structured-data.html  # JSON-LD schemas
│   ├── index.html          # Homepage template
│   └── 404.html            # Error page
├── static/
│   ├── images/
│   │   └── logo.webp       # Site logo
│   ├── favicon.ico         # 32x32 favicon
│   ├── icon-192.png        # PWA icon
│   ├── icon-512.png        # PWA icon large
│   ├── apple-touch-icon.png # iOS icon
│   ├── og-image.png        # Social share image (1200x630)
│   ├── robots.txt          # Search engine + AI crawler directives
│   └── llms.txt            # LLM-specific site description
├── hugo.toml               # Site configuration
├── AGENTS.md               # This file
├── CLAUDE.md               # Pointer to AGENTS.md
└── PROMPT.md               # Original build requirements
```

## Creating New Posts

1. Run: `hugo new content posts/your-post-slug.md`
2. Edit frontmatter:

```yaml
---
title: "Your Post Title"
date: 2025-12-19
description: "Brief description for SEO and previews"
tags: ["tag1", "tag2"]
draft: false  # Set to false to publish
---
```

3. Write content in Markdown
4. Build: `hugo`

## Design System

### Brand Colors
- **Primary:** `#004C7E` (deep blue)
- **Primary Dark:** `#003a61`
- **Accent Orange:** `#b54600`
- **Accent Green:** `#4f7705`

### Layout
- **Content max-width:** 720px
- **Wide container:** 1280px (header/nav)
- **Header/Footer:** Black background (#000)

### Dark Mode
Automatic via `prefers-color-scheme`. Primary shifts to `#58a6ff` for contrast.

## Accessibility (WCAG 2.2 AA)

- Skip link to main content
- Semantic HTML landmarks
- 3px focus indicators
- 44px minimum touch targets
- `prefers-reduced-motion` support
- Print stylesheet
- Proper heading hierarchy
- ARIA labels where needed

## SEO & AESEO

### Meta Tags
- Title, description, keywords
- Open Graph (title, description, type, url, image)
- Twitter Cards (summary_large_image)
- Canonical URLs
- Article metadata (published, modified, tags)

### Structured Data (JSON-LD)
- `WebSite` schema on homepage
- `Article` schema on posts

### AI Optimization
- `robots.txt` allows all AI crawlers (GPTBot, Claude-Web, PerplexityBot, etc.)
- `llms.txt` provides site context for LLMs
- Clean semantic HTML for easy parsing

### Feeds
- RSS at `/index.xml`
- XML sitemap at `/sitemap.xml`

## Git Repository

- **Remote:** https://github.com/84emllc/84emai
- **Branch:** main
- **Ignored:** `/public/`, `/resources/_gen/`, editor files

## Configuration Reference

Key settings in `hugo.toml`:

```toml
baseURL = 'https://84em.ai/'
title = '84EM.AI'

[params]
  author = "Andrew Miller"
  description = "Practical AI workflows..."

[params.social]
  twitter = "84emcom"
```

## Deployment

1. Run `hugo` to build
2. Deploy contents of `public/` to static hosting
3. Ensure `baseURL` in `hugo.toml` matches production domain
