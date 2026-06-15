# Changelog

---

## [2026-06-15] — Light theme refresh: warmer website, readable waitlist

### Design
- **Removed all large dark ink backgrounds from the website.** Sections that were black/near-black are now warm off-white or paper beige:
  - `.opening` section: `var(--ink)` → `var(--paper)` (#f2ece0). The "still" watermark adjusted to faint dark-on-light.
  - Product copy panes (odd, previously ink): `var(--ink)` → `#EAE3D6` (warm stone).
  - `.final-cta` (waitlist section): `var(--ink)` → `var(--cream)` (#faf7f1).
- **Waitlist section redesigned as a premium light card.** `.final-inner` now has white background, 1px soft border, warm shadow, and 56px padding — reads as a distinct elevated card on the cream background.
- Product copy pane text (headings, body, price values) updated from cream/light to `var(--ink)` / `var(--grey)` — readable on new warm stone background.

### Interaction / Form
- **All `.wl-*` form colors flipped from light-on-dark to dark-on-light.** Every rgba of `rgba(244,236,224,...)` replaced with the dark-ink equivalent for legibility on white card.
- Email input, country dropdown, product cards, checkboxes, price buttons: now show `#FAF8F5` background, soft ink border, clear dark text.
- Dropdown `<option>` background changed from `#18140f` (black) to `#FFFFFF` — browser-native options now readable.
- Form field borders rounded (8px) to match app UI premium feel.
- Submit button, product cards, price buttons all get matching `8px` border-radius.
- Focus states updated: amber border replaces light-on-dark glow.

### Typography
- `.final-body` color: `rgba(244,236,224,0.38)` → `var(--grey)` — much higher contrast.
- `.final-label` color: `rgba(201,160,85,0.45)` → `var(--amber)` — full amber on light.
- `.final-note` and `.launch-status` colors updated from near-invisible cream to readable `rgba(24,20,15,0.3)`.
- Form field labels (`.wl-label`) updated to `rgba(24,20,15,0.45)` — clearly readable.
- Checkbox and price button text updated from barely-visible cream shades to `rgba(24,20,15,0.55)`.

### Responsive
- Mobile breakpoint padding for `.final-cta` and `.final-inner` card adjusted for small screens.

All notable changes to the Trace landing page are documented here.

Format: `[YYYY-MM-DD] Category — Description`
Categories: **Content**, **Design**, **Layout**, **Interaction**, **Tooling**

---

## [2026-06-15] — Product naming + waitlist upgrade

### Content
- **Product family renamed to official 3-product lineup:** Trace Nær (Keychain Display), Trace Ro (Desktop Display), Trace Vid (Wall Display)
- Product lineup cards: "Pocket display" → "Keychain display", "Living room display" → "Desktop display", "Statement display" → "Wall display"
- Product phase labels updated: "The Pocket Display" → "The Keychain Display", "The Living Room Display" → "The Desktop Display", "The Statement Display" → "The Wall Display"
- Reward card description: "The pocket display." → "The keychain display."
- Reward bundle description: "pocket and kitchen" → "keychain display and home display"
- Alt text updated: removed "magnetic" descriptor from Trace Hjem images; updated Trace Ro from "desk" to "desktop"
- README.md: product table updated to reflect new 3-product family with categories and phases

### Interaction
- **Waitlist form upgraded for market validation:** added 4 new fields — product interest (required), location dropdown (required), use-case checkboxes (optional), expected price range (optional)
- Product interest: styled radio cards for Trace Nær, Trace Ro, Trace Vid — single-select, required
- Location: 11-country dropdown (France, Germany, Denmark, UK, Netherlands, Belgium, Sweden, Norway, US, Canada, Other) — required
- Use case: 7 checkbox options (Family memories, Children & grandparents, Travel memories, Art & photography, Home decoration, Gifts, Other) — optional, 2-column grid
- Price range: 4 Trace Nær price tiers (Under €49, €49–69, €69–89, €89+) — optional
- All fields submit as JSON to Formspree (`https://formspree.io/f/maqzvqbw`) with keys: `email`, `product`, `location`, `use_case`, `price_range`
- Success state updated: "You're on the list." + "We'll let you know when Trace becomes available." — replaces old inline button mutation
- Form validates email, product, and location before submission; flashes red border on missing required fields

### Design
- New `.wl-*` CSS component system for the extended form: radio cards, select dropdown, checkboxes, price pills — all in TRACE visual language (dark ink background, amber accent, muted cream text, DM Mono labels, Cormorant Garamond product names)
- Mobile responsive: product cards and checkboxes collapse to single column below 520px
- Success state uses italic Cormorant Garamond headline + DM Mono label in sage — matches existing brand motion

### Tooling
- URGENT FIX (2026-06-15 earlier): Connected waitlist form to live Formspree endpoint; added `Content-Type: application/json` header

---

## [2026-05-27]

### Content
- Updated page title: removed "| Kickstarter" — page now lives on GitHub Pages, not Kickstarter platform
- Hero CTA: "Fund Now" → "Join the Waitlist" (links to `#waitlist` anchor)
- Stats bar: replaced funding progress (€136,400 / 68% / 14 days) with soft-launch status — "Open / Waitlist status", "Pre-orders opening soon / Early access", "3 / Display sizes", "2026 / Est. delivery"
- Sticky header stat: "€136,400 raised · 68% · 14 days left" → "Pre-orders opening soon · Waitlist now open"
- Sticky header CTA: "Fund Now" → "Join Waitlist" (links to `#waitlist`)

### Layout
- Added `id="waitlist"` to the final-CTA section — all CTAs now deep-link to it
- Added animated amber `.waitlist-badge` ("Pre-orders opening soon") above the waitlist headline
- Added `.launch-status` line below the email form with placeholder Gumroad / Stripe links

### Content
- Rewards section label: "Kickstarter rewards" → "Early access pricing"
- Rewards section intro: replaced Kickstarter campaign copy with pre-order waitlist framing
- All three reward CTAs: "Select this reward" → "Notify me when open" (linked to `#waitlist`)
- Waitlist section headline: "Be the first to hold Trace." → "Be among the first to live with Trace."
- Waitlist section label: "Early access" → "Join the early access waitlist"
- Waitlist section body: updated from backer count copy to pre-order framing
- Email form note: "Early bird pricing ends when the campaign closes" → "One email when pre-orders open"
- Success state: "You're in ✓" → "You're on the list ✓" with `--sage` background

### Interaction
- Email form: wired to read `data-endpoint` attribute for future Formspree integration; submits via `fetch` when endpoint is set, falls back to client-side success state
- Payment JS: added `[data-payment-url]` click handler — redirects to URL when set, no-ops when empty (ready for Gumroad or Stripe link population)
- All reward CTAs carry `data-payment-url=""` placeholder — set to activate payment on pre-order launch

### Tooling
- Applied Prettier formatting to `index.html` — normalized whitespace, indentation, and CSS property spacing across the entire 1,900-line file
- Set up auto-format-on-save hook (PostToolUse → `npx prettier --write index.html`) via `.claude/settings.json`
- Added project documentation: `CLAUDE.md` (design system reference), `README.md`, `CHANGELOG.md`, `DEV_LOG.md`
- Added Claude Code skills: `/serve` (local HTTP preview), `/check-page` (HTML audit)
