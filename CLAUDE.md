# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a hand-coded static HTML academic portfolio website hosted on GitHub Pages. There is no build system, package manager, or framework — all pages are plain HTML files with embedded CSS and JavaScript. Changes are deployed by pushing to the `main` branch.

## No Build or Test Commands

There are no build, lint, or test commands. To preview locally, open any `.html` file directly in a browser or use a simple server:

```bash
python3 -m http.server 8000
```

## Site Structure

```
index.html              # Homepage (hero, research, publications, talks, notes, CV)
notes/notes-index.html  # Notes directory page
notes/*.html            # Individual note pages
talks/*.html            # Individual talk/poster pages
templates/              # HTML templates to copy when creating new pages
files/docu/             # PDFs (slides, CV)
files/img/              # Images
files/videos/           # Videos
```

## Architecture

**Single-file pages**: Each page is a self-contained HTML file with all CSS and JS embedded inline (no external stylesheet or script files in the repo). CDN dependencies are:
- Google Fonts (Libre Baskerville, DM Sans)
- MathJax 3 (for LaTeX rendering in notes)

**Theming**: Light/dark mode is implemented via a `data-theme="dark"` attribute on `<html>`, toggled by JS and persisted in `localStorage`. CSS custom properties drive the color scheme — `--ink`, `--paper`, `--accent`, etc.

**Templates**: When adding a new talk or note page, copy the relevant template from `templates/` and fill in the content. The notes template includes pre-wired MathJax macros (`\vb{}`, `\pd`, `\dd`, `\avg{}`), figure/theorem/proof blocks, and footnote support.

**Navigation**: There is no shared nav component — navigation links are duplicated across pages. When adding a new note or talk, also update:
1. `index.html` (the relevant talks or notes preview section)
2. `notes/notes-index.html` (if adding a note)

## Conventions

- Filenames for talks follow the pattern `YYYY-conference-type.html` (e.g., `2026-pspwg-oral.html`).
- MathJax inline math uses `\(...\)`, display math uses `\[...\]`.
- The grain texture overlay is a CSS `background-image` using an inline SVG — don't remove it; it's intentional.
