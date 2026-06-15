# Dev Log

Significant decisions, tradeoffs, and reasoning behind how this project is built.

---

## [2026-05-27] — Initial project setup

### Single-file HTML architecture
**Decision:** Keep everything in one `index.html` — CSS, JavaScript, and markup all embedded.

**Reasoning:** This is a campaign landing page with a finite lifespan. A build pipeline (bundler, preprocessor, node_modules) adds maintenance overhead with no real benefit at this scale. A single file is trivially deployable anywhere, loads without any toolchain, and is easy to hand off. The tradeoff is that the file gets large (~1,900 lines), but that's acceptable for a focused campaign page.

### Prettier for formatting
**Decision:** Use `npx prettier` (no local install, fetched via npx) as the sole code formatter. Runs automatically after every Claude edit via PostToolUse hook.

**Reasoning:** The file is large enough that manual formatting discipline is unreliable. Prettier's HTML+CSS+JS support handles all three concerns in one pass. Using `npx` avoids adding a `package.json` or node_modules to what is otherwise a zero-dependency project.

### CSS custom property design system
**Decision:** All colors defined as named CSS variables in `:root` — never hardcoded hex values elsewhere in the file.

**Reasoning:** The palette was carefully chosen (warm neutrals anchored by amber, sage, rust accents). Using variables makes palette-wide tweaks a single-point change and prevents inconsistencies when adding new sections.

| Token | Purpose |
|-------|---------|
| `--ink`, `--char` | Text hierarchy (dark to medium) |
| `--grey` | Labels, metadata, muted copy |
| `--dust`, `--paper`, `--cream` | Layered backgrounds (dark to light) |
| `--amber` | Primary CTA, progress bars, highlights |
| `--sage`, `--rust` | Secondary accents — use sparingly |

### Product naming convention
**Decision:** Product names are Norwegian/Nordic words: Nær, Hjem, Rø. These are intentional brand choices — do not translate, anglicize, or alter capitalization.

**Reasoning:** The names reinforce the product's positioning around warmth, home, and stillness. Nær (near), Hjem (home), Rø (calm/stillness).

---

## [2026-05-27] — Soft-launch / Platform Strategy A

### GitHub Pages as primary landing page
**Decision:** GitHub Pages is the live website. The page is no longer presented as a Kickstarter campaign; it is a standalone soft-launch landing page collecting waitlist interest.

**Reasoning:** Qonto payment approval is pending and no payment platform is connected yet. GitHub Pages is free, zero-config, and directly serves the single `index.html` without any backend. When payments are ready, reward CTAs and form actions will be populated — the page structure already supports this via `data-payment-url` attributes.

**How to apply:** Never add server-side logic or node_modules. All interactivity stays client-side JavaScript.

### Soft-launch waitlist strategy (Strategy A)
**Decision:** Implement Strategy A — GitHub Pages as landing page, email capture for waitlist, no payment yet. Placeholder `data-payment-url=""` attributes on all purchase CTAs. Placeholder `data-endpoint=""` on email form for Formspree/Mailchimp.

**Reasoning:** Payment approval (Qonto) is pending. This stage is market validation: collect real email intent, drive traffic from Instagram/TikTok, measure interest before committing to a payment platform. Gumroad or Stripe will be added when ready — the HTML is already wired to activate without structural changes.

**Tradeoff:** Waitlist emails are currently only stored client-side (success state shown, no actual submission). Before launch, populate `data-endpoint` on `#waitlistForm` with a Formspree ID.

### Product constraint: Bluetooth only, no WiFi
**Decision:** All copy confirmed Bluetooth-only. No WiFi mentions anywhere in the page copy.

**Reasoning:** Approved product spec as of 2026-05-27. This must not be reversed — do not add WiFi claims or connectivity language that implies network features.

**How to apply:** Before every copy change, check that no new WiFi, network, or cloud-sync language is introduced.

### Warm White / Beige launch direction approved
**Decision:** Warm White and Beige are the confirmed launch colorway direction for Trace. The CSS color system (`--cream`, `--paper`, `--dust` for backgrounds; `--amber` for accent) correctly reflects this.

**Reasoning:** This was explicitly approved as the launch direction. Do not shift the palette toward cooler whites, greys, or saturated tones.

**How to apply:** All new sections should use `var(--cream)` or `var(--paper)` as the base background. Never introduce pure white (`#fff`) or cool-grey backgrounds.

### Kickstarter-style storytelling approved
**Decision:** The narrative structure — opening with emotional copy, stats bar, social proof testimonials, product lineup, FAQ — follows Kickstarter campaign storytelling conventions. This direction is approved and should be maintained even though the page is not on Kickstarter.

**Reasoning:** Kickstarter storytelling has a proven structure for building conviction in a physical product: problem → product → proof → price → action. The page uses this structure deliberately.

**How to apply:** New sections should follow this narrative arc. Don't flatten the page into a generic product page.

---

## [2026-06-15] — Formspree live connection

### Waitlist form wired to real Formspree endpoint
**Decision:** Set `data-endpoint="https://formspree.io/f/maqzvqbw"` directly in the HTML on `#waitlistForm`. Added `Content-Type: application/json` alongside the existing `Accept: application/json` header in the fetch call.

**Why:** The form was previously in a fallback-only mode — `data-endpoint` was empty, so the JS showed the success state client-side but never submitted to any backend. Real email capture requires the endpoint to be set and the Content-Type header to be correct for Formspree's JSON API.

**How to apply:** The form is now live. Any future endpoint changes (e.g. switching providers) only require updating `data-endpoint` on `#waitlistForm` — no JS changes needed.

---

### Animation standard
**Decision:** All transitions and animations use `cubic-bezier(0.22, 1, 0.36, 1)` — no linear or ease-in-out.

**Reasoning:** This curve feels physical: fast start, long gentle settle. Consistent across scroll reveals, header slide-in, and interactive elements so the page has a unified motion character.
