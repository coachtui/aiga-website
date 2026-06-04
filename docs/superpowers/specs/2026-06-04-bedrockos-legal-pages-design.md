# BedrockOS Legal Pages — Design Spec

**Date:** 2026-06-04
**Scope:** BedrockOS Privacy Policy page, Terms of Service page, and BedrockOS footer update.

---

## Overview

Add two new legal pages for the BedrockOS platform (`/bedrockos/privacy.html` and `/bedrockos/tos.html`) and update the BedrockOS landing page footer to link to both. The existing `/privacy.html` (AIGA LLC general policy for the marketing site) is left unchanged.

---

## Pages to Create

### `/bedrockos/privacy.html` — BedrockOS Privacy Policy

- **Audience:** BedrockOS platform subscribers and users
- **Content:** Provided policy covering account/org data, operational data, usage data, sharing, retention, security, user rights, cookies, children's privacy, changes, and contact. Effective date: June 1, 2026.
- **Layout:** Clones `/privacy.html` structure — floating nav, scrollable document body, footer.
- **Nav:** Same as `bedrockos/index.html` — AIGA mark (links to `/`), "BedrockOS" product label, section links back to `bedrockos/index.html` anchors (`#modules`, `#connected`, `#platform`), "Get Access" CTA.
- **Footer:** Same as `bedrockos/index.html` — AIGA mark, links to AIGA Home / Privacy / Terms.

### `/bedrockos/tos.html` — BedrockOS Terms of Service

- **Audience:** BedrockOS platform subscribers
- **Content:** Provided ToS covering eligibility, subscription/payment, acceptable use, customer data, IP, confidentiality, warranties/disclaimer, liability, indemnification, termination, modifications, governing law (California/JAMS arbitration), and contact. Effective date: June 1, 2026.
- **Layout:** Same as privacy page.
- **Nav:** Same as privacy page.
- **Footer:** Same as privacy page.

---

## Footer Update — `bedrockos/index.html`

Current footer links: `AIGA Home | Modules | Get Access | Privacy`

Updated footer links: `AIGA Home | Modules | Get Access | Privacy | Terms`

- `Privacy` → `/bedrockos/privacy.html`
- `Terms` → `/bedrockos/tos.html`

---

## Design System

Both pages use the existing BedrockOS design system (self-contained inline styles):

- **Colors:** Same CSS custom properties as `bedrockos/index.html` (`--bg`, `--surface`, `--border2`, `--text`, `--muted`, `--accent #3DBA6E`, etc.)
- **Typography:** Space Grotesk (headings), Inter (body), IBM Plex Mono (mono)
- **Nav:** Floating glassmorphism header, identical to all other pages
- **Document layout:** Centered content column (~680px max-width), generous vertical padding, section headings in Space Grotesk, body text in Inter, horizontal rules between sections
- **No new components** — follows the exact same document pattern as `/privacy.html`

---

## Out of Scope

- No changes to `/privacy.html` (AIGA general policy stays as-is)
- No changes to BedrockOS page content or UX (confirmed correct)
- No changes to main site footer
- No ToS for the AIGA marketing site (not needed at this time)

---

## File Checklist

- [ ] `/bedrockos/privacy.html` — created
- [ ] `/bedrockos/tos.html` — created
- [ ] `bedrockos/index.html` — footer updated (Privacy link + Terms link)
