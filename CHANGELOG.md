# TRACE — Change Log / Work Log

Project: TRACE Campaign Landing Page
Live URL: https://ck-ai-design.github.io/Trace/
Repository: https://github.com/CK-ai-design/Trace

---

## How to use this log

Add a new entry at the **top** of the log after every work session.
Copy the template below and fill in each field.

```
---
Date: YYYY-MM-DD
Time: HH:MM (timezone)
Changed by: [Name / Claude / both]
What changed: [Short summary]
Why: [Reason or goal]
Files affected: [list files]
Status: Done / Pending / Need Review
Next action: [What needs to happen next, if anything]
---
```

---

## Work Log

---

Date: 2026-06-15
Time: Session 4
Changed by: Claude (with Cathy)
What changed: Fixed checkbox bug — "What would you use Trace for?" options were not selectable.
Why: Clicking a label wrapping a hidden checkbox fired the toggle handler twice (browser dispatches a synthetic click back to the input which bubbles up), cancelling itself out. Added e.preventDefault() to stop the double-fire.
Files affected: index.html
Status: Done
Next action: Monitor Formspree dashboard to confirm use_case values are arriving with submissions.

---

Date: 2026-06-15
Time: Session 3 (continued)
Changed by: Claude (with Cathy)
What changed: Website light theme refresh — replaced all large dark/black backgrounds with warm off-whites and paper tones. Waitlist form redesigned as a light premium card.
Why: The website felt too dark, especially the waitlist section. Dropdown and form options were almost black-on-black and unreadable. Goal was to match the warm, Scandinavian minimal mood of the companion app.
Files affected: index.html, CHANGELOG.md, DEV_LOG.md
Status: Done
Next action: Continue testing the form on mobile. Consider lightening the footer in a future session.

---

Date: 2026-06-15
Time: Session 2
Changed by: Claude (with Cathy)
What changed:
  1. Product family renamed to official 3-product lineup:
     - Trace Nær — Keychain Display (Phase 1)
     - Trace Ro — Desktop Display (Phase 2)
     - Trace Vid — Wall Display (Phase 3)
  2. Waitlist form upgraded with 4 new market validation fields:
     - Product interest (required) — radio cards
     - Location / country (required) — 11-country dropdown
     - Use case (optional) — 7 checkboxes
     - Expected price range for Trace Nær (optional) — 4 price buttons
  3. Success message updated: "You're on the list." / "We'll let you know when Trace becomes available."
  4. README.md product table updated to new 3-product family.
Why: Simplified product lineup from 4 to 3 for a clearer form-factor story. Upgraded waitlist from a single email field to a market research instrument ahead of crowdfunding — to learn which product has the most interest and in which countries, and to validate the Nær price point.
Files affected: index.html, README.md, CHANGELOG.md, DEV_LOG.md
Status: Done
Next action: Review Formspree submissions after traffic to see which product and country leads.

---

Date: 2026-06-15
Time: Session 1 (urgent fix)
Changed by: Claude (with Cathy)
What changed: Connected the waitlist form to a live Formspree endpoint. Added missing Content-Type: application/json header to the fetch request.
Why: The form was showing the success state locally but not actually sending any data anywhere — the endpoint was empty and the JSON header was missing. Real email capture required both to be set.
Files affected: index.html, CHANGELOG.md, DEV_LOG.md
Status: Done
Next action: Monitor Formspree dashboard at formspree.io/f/maqzvqbw for incoming submissions.

---

Date: 2026-05-27
Time: Session 1
Changed by: Claude (with Cathy)
What changed: Converted the page from a Kickstarter campaign format to a standalone GitHub Pages soft-launch landing page. Full content and CTA update to waitlist/pre-order framing.
  - Page title: removed "| Kickstarter"
  - Hero CTA: "Fund Now" → "Join the Waitlist"
  - Stats bar: replaced funding metrics with soft-launch status (waitlist open, 3 display sizes, 2026 delivery)
  - Rewards section: reframed from "Kickstarter rewards" to "Early access pricing"
  - All reward CTAs: "Select this reward" → "Notify me when open"
  - Waitlist headline updated to emotional pre-order framing
  - Payment JS wired to data-payment-url attribute (placeholder, not active)
  - Applied Prettier formatting across the full file
  - Added CLAUDE.md, README.md, CHANGELOG.md, DEV_LOG.md to repository
Why: Qonto bank account review is pending. Payment links are not available yet. GitHub Pages allows public link sharing and waitlist collection while payment is being set up. "Fund Now" buttons will be updated once payment links are approved.
Files affected: index.html, README.md, CHANGELOG.md, DEV_LOG.md, CLAUDE.md
Status: Done — payment CTAs still pending (placeholder links, not active)
Next action: When Qonto bank review is approved and payment links are ready, update all data-payment-url="" attributes in index.html with real Gumroad or Stripe links.

---

Date: Before 2026-05-27
Time: Initial build
Changed by: Cathy
What changed: HTML webpage designed and built as TRACE campaign landing page. File renamed to index.html and prepared for GitHub Pages publishing.
Why: Needed a public-facing page to share the TRACE product concept and collect early interest while payment and crowdfunding setup is in progress.
Files affected: index.html
Status: Done
Next action: Fund Now / payment buttons to be activated once Qonto bank review is complete and payment links (Gumroad or Stripe) are confirmed.

---

## Quick Reference

| What to update | Where |
|---|---|
| Payment / Fund Now links | index.html — search `data-payment-url=""` and add real URL |
| Formspree endpoint | index.html — `id="waitlistForm"` `data-endpoint="..."` |
| Product names | index.html + README.md |
| Page content | index.html |
| Design decisions | DEV_LOG.md |
| This log | CHANGELOG.md (this file) |

---

## Pending items

- [ ] Payment links — waiting for Qonto bank review approval. When ready: add Gumroad or Stripe URLs to all `data-payment-url=""` attributes in index.html.
- [ ] Fund Now buttons — currently show as "Notify me when open" and link to waitlist. Will be updated to real payment links when ready.
- [ ] Consider lightening the website footer to match the new warm light theme.
