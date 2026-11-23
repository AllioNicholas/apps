# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static site of landing and support pages for the owner's iOS apps, served by GitHub Pages at https://allionicholas.github.io/apps/. Plain HTML + one shared CSS file. There is no build step, package manager, linter, or test suite. `.nojekyll` turns off Jekyll processing, so files are served exactly as committed.

Preview locally with `python3 -m http.server` from the repo root, then open http://localhost:8000/.

## Structure and conventions

- `index.html`: the apps index, a `<ul class="apps">` with one card (icon, name, one-line pitch) per app.
- `<AppName>/index.html`: the app's landing page. The folder name is the URL path and is case-sensitive.
- `<AppName>/support/index.html`: the app's support page (contact plus FAQ).
- `<AppName>/icon.png`: the app icon, used as the page header image, favicon, and apple-touch-icon, and on the root index card.
- `style.css`: the single stylesheet for every page. It uses CSS variables in `:root`, with a `prefers-color-scheme: dark` override. The `--up`/`--down`/`--random` colors and the `.modes` grid are specific to SpeedyEye's game modes.

**All links must be relative (no leading `/`)** so the site works both under `/apps/` on GitHub Pages and on a custom domain at the root. That means depth-dependent paths: `style.css` at the root, `../style.css` on a landing page, `../../style.css` on a support page.

To add an app: create its folder with `index.html`, `support/index.html`, and `icon.png`, add a card to the root `index.html`, and add a row to the table in `README.md`.

Page patterns to copy from `SpeedyEye/`:
- Landing pages have a `<header>` (icon, `h1`, `.tagline`, App Store `.button`), content sections as `h2`, and a footer linking to `support/` and `../` ("More apps"). They include `<meta name="apple-itunes-app" content="app-id=...">` for the Safari Smart App Banner.
- On the support page, the "Contact support" button opens a prefilled GitHub issue in `AllioNicholas/apps`, with the title prefixed `<AppName>: ` and the label set to the app name.
- Copy follows Apple's terminology (Game Center, VoiceOver, Dynamic Type, Home Screen quick actions) and should match what the app actually does.
