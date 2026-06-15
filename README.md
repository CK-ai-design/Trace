# Trace — Kickstarter Landing Page

Campaign landing page for **Trace**, a smart photo display device. A single `index.html` file with embedded CSS and JavaScript — no build step required.

## Preview

Open `index.html` directly in a browser, or for more accurate testing (absolute paths, resource timing):

```
python -m http.server 8080
```

Then open [http://localhost:8080](http://localhost:8080).

## Products

| Name | Category | Phase |
|------|----------|-------|
| Trace Nær | Keychain Display | Phase 1 |
| Trace Ro | Desktop Display | Phase 2 |
| Trace Vid | Wall Display | Phase 3 |

## Project structure

```
index.html          — entire site (markup, CSS, JS)
CHANGELOG.md        — all changes with dates and categories
DEV_LOG.md          — design decisions and reasoning
CLAUDE.md           — guidance for Claude Code sessions
.claude/
  settings.json     — PostToolUse hook: auto-formats index.html with Prettier
  skills/
    serve/          — /serve: starts local HTTP server
    check-page/     — /check-page: audits HTML for common issues
```

## Design system

Warm neutral palette with amber as the primary accent. All colors are CSS custom properties — see `CLAUDE.md` for the full token reference.

Fonts loaded via Google Fonts CDN:
- **Cormorant Garamond** — headlines (italic, 300–400 weight)
- **DM Mono** — labels and UI text (monospace, uppercase)
- **Jost** — body copy (sans-serif, 300 weight)
