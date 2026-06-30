# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal academic website for Rui Huang (PhD candidate, computational plasma physics, University of Iowa), served by GitHub Pages at https://rh19physics.github.io/. It is **plain static HTML** — there is no build system, no Jekyll/`_config.yml`, no npm, no tests. Every page is a self-contained `.html` file with inline `<style>` and `<script>`. Pushing to the default branch deploys.

To preview locally, open the file in a browser, or serve the repo root with any static server (e.g. `python3 -m http.server`).

## Layout

- `index.html` — the homepage (bio, publications, talks, contact). The largest file; all CSS/JS is inline.
- `talks/` — one page per talk/poster (e.g. `2025-agu-poster.html`), named `YYYY-venue-type.html`. Each embeds a PDF from `files/docu/`.
- `notes/` — standalone notes/puzzles/visualizations, indexed by `notes/notes-index.html`.
- `templates/talk-template.html`, `templates/notes-template.html` — **start here when creating a new talk or note page.** Copy the template, fill in the marked placeholders, then link the new page from `index.html` (and from `notes/notes-index.html` for notes).
- `files/docu/` — PDFs (CV, posters, slides). `files/img/`, `files/videos/` — media assets.

## Conventions (keep these consistent across all pages)

- **Shared design tokens.** Every page repeats the same CSS `:root` and `[data-theme="dark"]` variable blocks (`--ink`, `--paper`, `--accent`, `--muted`, `--rule`, `--highlight`, `--nav-bg`, fonts). When changing colors/fonts, update the variables in *every* page, not just one.
- **Fonts:** Libre Baskerville (serif) + DM Sans (sans), loaded from Google Fonts in each `<head>`.
- **Dark mode is the default.** The theme script reads `localStorage.getItem('theme')` and falls back to `'dark'` (line ~894 in `index.html`); dark is applied via the `data-theme="dark"` attribute on `<html>`. The toggle button swaps the attribute and persists the choice. Replicate this script when adding pages.
- **Math:** pages with equations load MathJax 3 from jsDelivr in `<head>`. The talk template includes it with a note to remove it if unused.
- New talk PDFs go in `files/docu/`; reference them with a relative path from the page (e.g. `../files/docu/...`).
