# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static site hosted via GitHub Pages at `arietetechsolutions.github.io` (repo: `arietetechsolutions/arietetechsolutions.github.io`). It serves as a directory of links to Ariete Capital's internal, self-hosted, and client-facing tools.

There is no build step, no package manager, no test suite, no framework. Deployment is just `git push` to `main` — GitHub Pages serves `index.html` directly.

## Architecture

Everything lives in `index.html`:
- Inline `<style>` block with the full design system (CSS variables under `:root` define the Ariete brand palette — navy/gold/rust/ivory)
- Inline `<script>` at the bottom (currently only sets the footer year)
- Tool entries are static `<li>` items in `.links` lists, grouped into three `<section>`s: **Tools**, **Self-hosted**, **Client Tools**

`logo.PNG` is the only other asset. The favicon is hot-linked from `arietecapital.com`.

## Adding or editing a tool link

Copy an existing `<li>` inside the appropriate `<section>` and update `href`, `.link__name`, and `.link__host`. Use the `link--soon` variant (with a `<span>` instead of `<a>` and a `tag` "Coming soon" badge) for unreleased tools, and the `tag--mvp` inline badge for MVP-stage tools — both patterns already exist in the file.

## Local preview

Open `index.html` directly in a browser, or serve the directory (e.g. `python3 -m http.server`) if you need to test relative paths or fetches.
