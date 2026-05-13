# AIGA Landing Page Redesign
**Date:** 2026-05-13
**Approach:** B — Add consulting section + targeted copy updates

---

## Context

AIGA LLC is the umbrella company for a set of AI-native products built by Tui Alailima, a civil superintendent with 20 years of field experience currently managing a $500M+ infrastructure job. The landing page (`index.html`) was built when the flagship product was called AIGACP; it has since been renamed BedrockOS and is now available to license. A new offering — AI Workflow Consulting, personally delivered by Tui — is being added as a first-class service. Offload has moved from "Coming Soon" to Beta.

The existing design system (dark green palette, Cormorant Garamond + IBM Plex Mono, grid aesthetic) remains unchanged. This is a static HTML/CSS/JS site with no build tools.

---

## Scope

Five discrete changes to `index.html`. No new files. No design system changes.

---

## 1. Status Label Fixes

Four string replacements across the marquee bar and platform rows.

| Element | Current | New |
|---|---|---|
| BedrockOS platform pill | `In Dev` | `Available to License` |
| Offload platform pill | `Coming Soon` | `Beta` |
| Marquee item | `BedrockOS — In Development` | `BedrockOS — Available to License` |
| Marquee item | `Offload — Coming Soon` | `Offload — Beta` |

The BedrockOS pill CSS class changes from `pill-dev` to a new `pill-license` class. Add to stylesheet:

```css
.pill-license {
    color: var(--aigacp);
    border-color: rgba(109,184,142,0.3);
    background: rgba(109,184,142,0.05);
}
.pill-license::before { background: var(--aigacp); }
```

This distinguishes it from `pill-live` (animated green pulse) and `pill-dev` (muted/dim).

---

## 2. Hero Rewrite

Eyebrow, H1, sub-paragraph, and CTAs are updated. The layout (two-column grid, left logo panel, right copy panel) is unchanged.

**Eyebrow:** Applied Intelligence Group *(no change)*

**H1:**
```
Built from inside
the industry.
```

**Sub-paragraph:**
```
AIGA is a platform studio and AI advisory run by a 20-year civil superintendent.
Our flagship, BedrockOS, is a modular construction OS built by someone who's run
the job — available to license today. We also help organizations find where AI fits
in their operations and build the tools to act on it.
```

**CTA buttons:**
- Primary (solid): `License BedrockOS` → `#platforms`
- Secondary (ghost): `Explore AI Consulting` → `#consulting`

**Nav:** Add `Consulting` link between `Platforms` and `About`, pointing to `#consulting`.

---

## 3. AI Workflow Consulting Section

New section inserted between the Platforms block and the Stats block. Anchored at `id="consulting"`.

### Section Rule
```
Label: AI Workflow Consulting
Meta:  Personally Delivered
```

### Layout
Two-column grid matching the contact section (`grid-template-columns: 1fr 1fr`, `gap: 80px`). Responsive: collapses to single column at ≤1024px.

### Left Column — Description + CTA

**Label (small caps):** The Offering

**Heading (serif, light weight):**
```
Where are you losing time to work that shouldn't need a human?
```

**Body:**
```
Most organizations aren't failing at AI — they haven't mapped where it actually
fits. Tui works directly with your team to find the friction, assess where AI
creates real leverage, and help you act on it. Any industry.
```

**CTA link:** `Start a Conversation` → `mailto:info@aigaai.com?subject=AI Consulting`

### Right Column — Service Rows

Three rows styled as `ct-opt` anchor elements (matching the contact section option rows). Each has a dot indicator and label + description inline.

| Label | Description |
|---|---|
| Workflow Audit | Map where time actually goes and find the drag |
| AI Fit Assessment | Identify which problems AI solves vs. which need a process fix first |
| Implementation | Recommend tools, guide adoption, or build something custom |

All three link to `mailto:info@aigaai.com?subject=AI Consulting`.

---

## 4. Manifesto Rewrite

The manifesto section structure is unchanged (label, large serif quote, attribution line). Only the copy changes.

**Label:** The Approach *(no change)*

**Quote:**
```
I'm a civil superintendent with 20 years in the field, currently managing a
$500M+ infrastructure job. Every product AIGA has built started as a problem
I couldn't solve with what existed. We don't consult from the outside —
we're already inside it.
```

**Attribution:**
```
Tui Alailima — Civil Superintendent, Founder
```
*(Previously "Inside the problem. Every time.")*

---

## 5. Contact Section Updates

Two additions to the existing contact section. Layout and form structure unchanged.

**Clickable option rows — add:**
```
Explore AI workflow consulting
```
Links to `mailto:info@aigaai.com?subject=AI Consulting`.

**Select dropdown — add option:**
```html
<option value="consulting">AI Workflow Consulting</option>
```
Inserted after the Offload option and before "I have an idea I want to build".

---

## Out of Scope

- No changes to `privacy.html`
- No changes to `bedrockos/index.html`
- No new CSS files or JS files
- No changes to fonts, color tokens, or layout grid
- No form backend changes (Formspree endpoint unchanged)
- Pricing, case studies, and social proof deferred to a future iteration

---

## File Changed

- `index.html` — all changes land in one file
