# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A GitHub Pages site (repo: `arietetechsolutions/arietetechsolutions.github.io`) that hosts internal Ariete Capital tools as static sub-apps. Each sub-app lives in its own folder at the repo root and is reachable at `arietetechsolutions.github.io/<folder>/`.

Currently the only sub-app is **Ariete Tools Cockpit** at `tools-cockpit/`, served from `arietetechsolutions.github.io/tools-cockpit/`. The repo root has no `index.html`, so the bare domain returns 404 by design.

There is no build step, no package manager, no test suite, no framework. Deployment is just `git push` to `main` — GitHub Pages serves files directly.

## Architecture

### Tools Cockpit (`tools-cockpit/`)

Everything for the cockpit lives in `tools-cockpit/index.html`:
- Inline `<style>` block with the full design system (CSS variables under `:root` define the Ariete brand palette — navy/gold/rust/ivory)
- Inline `<script>` at the bottom (currently only sets the footer year)
- Tool entries are static `<li>` items in `.links` lists, grouped into three `<section>`s: **Tools**, **Self-hosted**, **Client Tools**

`tools-cockpit/logo.PNG` is the only other asset for that page. The favicon is hot-linked from `arietecapital.com`. Asset paths inside the HTML are relative to the folder, so the cockpit is fully self-contained — to add another sub-app, create a sibling folder with its own `index.html` and assets.

## Adding or editing a tool link in the cockpit

In `tools-cockpit/index.html`, copy an existing `<li>` inside the appropriate `<section>` and update `href`, `.link__name`, and `.link__host`. Use the `link--soon` variant (with a `<span>` instead of `<a>` and a `tag` "Coming soon" badge) for unreleased tools, and the `tag--mvp` inline badge for MVP-stage tools — both patterns already exist in the file.

## Local preview

Open `tools-cockpit/index.html` directly in a browser, or serve the repo root (e.g. `python3 -m http.server`) and visit `http://localhost:8000/tools-cockpit/` — this matches how GitHub Pages will serve it.
