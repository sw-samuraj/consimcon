# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Source code for the **Czech Consim Con (C3)** website — a bilingual (Czech/English) conference website for historical and war games enthusiasts. Built with Hugo (static site generator). Deployed at https://consimcon.cz.

## Commands

```bash
hugo server   # Start local development server with live reload
hugo          # Build static site to public/
```

**Prerequisites:** [Hugo](https://gohugo.io/) must be installed. Theme is a git submodule (`themes/hugo-blog-awesome`); run `git submodule update --init` if missing.

## Architecture

Hugo static site with bilingual content. Config is `hugo.toml`. The theme (`themes/hugo-blog-awesome`) is a git submodule — do not modify it directly.

**Content is mirrored in two language trees:**
- `content/cs/` — Czech (default language, weight 1)
- `content/en/` — English (weight 2)

Every content change must be applied to both language versions.

**Content structure:**
- `_index.md` — homepage/landing page for a section
- `pages/informace.md` / `pages/information.md` — venue, schedule, fees, guests
- `pages/registrace.md` / `pages/registration.md` — registration info
- `archiv/` / `archive/` — past event pages, one subdirectory per year (e.g., `archiv/2024/`)

**Menu navigation** is defined in `hugo.toml` under `[Languages.cs.menus]` and `[Languages.en.menus]`, not in content frontmatter.

## Content Conventions

- Frontmatter: YAML with `title`, `description`, `date`, `image`, `toc`
- Images: stored in `static/img/`, referenced as `/img/filename.jpg`; use Hugo `figure` shortcode: `{{< figure src="..." link="..." alt="..." caption="..." >}}`
- External links use protocol-relative URLs: `//maps.app.goo.gl/...`
- Guests link to BoardGameGeek profiles; playtested games link to BGG, GMT Games, or Rally the Troops
- New drafts created via `hugo new` start with `draft: true` (TOML archetype); switch to YAML frontmatter to match existing pages
