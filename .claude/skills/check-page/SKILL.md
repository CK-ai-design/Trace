---
name: check-page
description: Scan index.html for common issues — broken internal references, duplicate IDs, missing alt text on images, and JavaScript patterns that would cause console errors. Run before publishing changes.
---

Audit `index.html` for the following issues. Read the file, then report findings grouped by severity.

**Check for:**

1. **Duplicate IDs** — search for `id="` values that appear more than once; duplicate IDs break anchor links and JavaScript `getElementById` calls

2. **Missing alt text** — find `<img` tags without an `alt` attribute or with `alt=""`; flag any that are content images (decorative images with `role="presentation"` or `aria-hidden="true"` are fine)

3. **Broken internal href anchors** — find all `href="#something"` links and verify a matching `id="something"` exists in the file

4. **Undefined JS references** — scan the `<script>` block for `document.getElementById(...)` and `document.querySelector(...)` calls; check that the referenced IDs/selectors exist in the HTML

5. **Missing closing tags** — look for unclosed `<div>`, `<section>`, `<ul>`, `<li>` tags by counting opens vs closes for major structural elements

6. **Hardcoded colors** — flag any hex color values (`#RRGGBB` or `#RGB`) that appear outside the `:root { }` block (they should use CSS variables instead)

7. **Font references** — confirm `Cormorant Garamond`, `DM Mono`, and `Jost` are loaded via the Google Fonts `<link>` tag; flag any `font-family` declarations using other unloaded fonts

Report each finding as: `[SEVERITY] Description — line N` where severity is ERROR (breaks functionality), WARNING (degrades quality), or INFO (minor). End with a summary count.
