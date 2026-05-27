# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Kickstarter campaign landing page for **Trace** — a smart photo display device. Single self-contained `index.html` (~1,900 lines) with all CSS and JavaScript embedded. No build step, no package manager, no dependencies except Google Fonts (CDN).

## Preview

Open `index.html` directly in a browser, or run `/serve` to start a local HTTP server for more accurate testing. Target: modern browsers (Chrome, Safari, Firefox, Edge), desktop and mobile equally.

## Design System

CSS custom properties defined in `:root`:

| Variable   | Value     | Role                        |
|------------|-----------|-----------------------------|
| `--ink`    | `#18140f` | Primary text, darkest       |
| `--char`   | `#2e2a24` | Secondary dark              |
| `--grey`   | `#7a7268` | Muted/label text            |
| `--dust`   | `#c8bfb0` | Dividers, inactive elements |
| `--paper`  | `#f2ece0` | Section backgrounds         |
| `--cream`  | `#faf7f1` | Base page background        |
| `--amber`  | `#c9a055` | Primary accent / CTA color  |
| `--sage`   | `#6a9472` | Secondary accent (green)    |
| `--rust`   | `#a84e2a` | Tertiary accent (terracotta)|

Always use these variables — never hardcode color hex values.

## Typography

- **Headlines / display**: `'Cormorant Garamond', serif` — italic, lightweight (300–400 weight)
- **Labels / monospace UI**: `'DM Mono', monospace` — uppercase, wide letter-spacing (0.15–0.2em)
- **Body / UI text**: `'Jost', sans-serif` — font-weight 300 default

## Animations

Standard easing throughout: `cubic-bezier(0.22, 1, 0.36, 1)` (snappy out, smooth settle).

Scroll-reveal pattern: add class `reveal` (starts at `opacity:0, translateY(32px)`), then JavaScript adds `visible` when element enters viewport via `IntersectionObserver`. Stagger with `reveal-delay-1` through `reveal-delay-4` (0.1s increments).

## Product Lineup

Four product variants with specific names — use these exactly:
- **Nær** (entry, £149) — compact
- **Hjem** (mid, £229) — standard
- **Rø** (premium, £329) — large
- **Editions** (limited) — special finishes

## CSS Conventions

- Class names: kebab-case (e.g. `.hero-headline`, `.product-reveal`)
- Section wrapper pattern: `<section class="[name]-section">` wrapping `<div class="[name]-inner">`
- Alternating product layouts use `.reverse` class with `direction: rtl` grid trick
- Responsive breakpoints are embedded inline per-section (no shared breakpoint variables)

## Logging Requirements

**Every change to `index.html`** must add an entry to `CHANGELOG.md` using the format:
```
## [YYYY-MM-DD]
### Category
- Description of what changed and why
```
Categories: Content, Design, Layout, Interaction, Tooling.

**Important decisions** — any choice about architecture, naming, design system, animation, or approach that a future collaborator might question — must be logged in `DEV_LOG.md` with the decision, reasoning, and tradeoffs. When in doubt, log it.
