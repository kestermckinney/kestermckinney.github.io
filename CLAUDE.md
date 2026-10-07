# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Developing and Previewing

No build step. Open any `.html` file directly in a browser, or serve the root with:

```
python3 -m http.server 8080
```

Then visit `http://localhost:8080`. Serving from a local server (rather than `file://`) is important because root-relative paths like `/styles.css` and `/images/...` won't resolve from `file://`.

## Publishing

Push to `main` on the `gitlab` remote. GitLab CI publishes the static site using the `pages` job in `.gitlab-ci.yml`.

## Architecture

This is a zero-dependency static site — no npm, no Jekyll, no build pipeline. All styling lives in a single file (`styles.css`) with a shared design token set in `:root`. JavaScript is inlined at the bottom of each HTML file.

**Page types:**

- `index.html` — personal landing page with `#about`, `#projects`, `#approach`, `#connect` anchor sections
- `projects/projectnotes.html`, `projects/sqlitesyncpro.html` — product detail pages with `.project-hero` layout and screenshot galleries
- `404.html` — minimal fallback page

**CSS layout conventions:**

- `.section` + `.section-alt` (alternating background) for full-width bands
- `.section-inner` constrains content to `--max: 980px`
- Section headings use the pattern: `<span class="eyebrow">`, then `<h2>`
- `.card-grid` is two-column; `.card-grid.single-row` is three-column
- Two responsive breakpoints: `940px` (stacks most grids to one column) and `640px` (mobile polish)

**Screenshot cards (project pages only):**

- Wrap each item in `.gallery-item-wrapper` with `data-lightbox-src` and `data-lightbox-caption` attributes to wire it into the lightbox
- Use `.screenshot-frame.desktop-frame` (16:9) or `.screenshot-frame.phone-frame` (portrait, sized automatically) inside a `.screenshot-card`
- `.dark-frame` adds a dark background for screenshots taken in dark mode

**Scroll reveal animations:**

- Add class `reveal` to any element to fade/slide it in on scroll
- Use `reveal-delay-1` through `reveal-delay-4` for staggered entrance within a group
- The `IntersectionObserver` wiring is inlined in the `<script>` block at the bottom of each page that uses it

**Inline JavaScript pattern:**

Each page that needs interactivity (lightbox, reveal) has a single IIFE at the bottom of `<body>`. When adding a new project page, copy this script block from `projects/projectnotes.html`.
