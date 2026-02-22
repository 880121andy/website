# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A personal website introducing the owner and their academic research. Planned sections (from `plan.md`): Research, Interests, Fun Facts, FAQ, Email/Contact.

## Repository & Deployment

- **GitHub repo:** https://github.com/880121andy/website.git
- **GitHub Pages URL:** https://880121andy.github.io/website
- Deploy by pushing to the `main` branch; enable Pages in repo Settings → Pages → Source: main / root.

## Tech Stack

- **HTML** – semantic, single-page or multi-page static site
- **Tailwind CSS** – utility-first styling (use CDN for simplicity, or CLI if a build step is added)
- **JavaScript** – vanilla JS for interactivity (no framework chosen yet)
- **Figma** – UI/UX design source; implement designs from Figma specs/exports

## Development

This is a static site with no build system yet. Open HTML files directly in a browser, or use a local dev server:

```bash
# Quick local server (Python)
python -m http.server 8080

# Or with Node
npx serve .
```

If Tailwind CLI is added later, the build command will be:

```bash
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch
```

## Architecture

Single-page `index.html` with smooth-scroll section anchors. All styles live in a `<style>` block inside `index.html`; Tailwind utility classes supplement custom CSS. JS is inline at the bottom of `index.html`.

**Animation system** (`index.html` `<style>` + `<script>`):
- Elements get class `reveal` (fade + lift) or `reveal fade-only` (fade only).
- Stagger via `.delay-1` through `.delay-5` utility classes.
- An `IntersectionObserver` adds `.visible` when elements enter the viewport (fires once, then unobserves).
- Nav gets class `scrolled` (frosted glass) after scrolling 40 px.
- FAQ uses a CSS `max-height` accordion toggled by JS click handlers.

**Sections in order:** Hero → About → Research (3-card grid) → Pull Quote → Interests (4-image grid) → Fun Facts → FAQ → Contact (dark bg).

## Assets

Place all images in `assets/`. Expected filenames:
- `photo1.jpg`, `photo2.jpg` – hero photos
- `research1–3.jpg` – research card images
- `interest1–4.jpg` – interest grid images
- `cv.pdf` – linked from About section

Images degrade gracefully (placeholder bg colour shown if file is missing).

## Placeholder text

All user-specific content is marked with `[brackets]` in `index.html`. Replace before publishing:
- Name, title, university, email
- Research descriptions and paper links
- Interests labels and images
- Fun facts and FAQ answers
- Social / academic profile URLs
