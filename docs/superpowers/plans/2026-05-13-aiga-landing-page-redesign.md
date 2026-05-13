# AIGA Landing Page Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Update index.html to fix stale status labels, lead with a founder-story hero, add a first-class AI Workflow Consulting section, and ground the manifesto in Tui's real credentials.

**Architecture:** All five changes land in one file — `index.html`. No new files, no build tools, no dependencies. CSS additions go in the existing `<style>` block. The new consulting section reuses existing CSS classes (`.ct-opt`, `.ct-h2`, `.ct-sub`, `.ct-label`, `.ct-email`, `.section-rule`) so no design system changes are needed beyond one new pill class and one new layout class.

**Tech Stack:** Static HTML, CSS custom properties, vanilla JS (no changes to JS).

---

## Files

- **Modify:** `index.html` — all changes

---

## Task 1: Add `pill-license` CSS and fix status labels

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add `pill-license` CSS rule**

In the `<style>` block, find the `.pill-dev` rule (around line 475). Add immediately after it:

```css
.pill-license {
    color: var(--aigacp);
    border-color: rgba(109,184,142,0.3);
    background: rgba(109,184,142,0.05);
}
.pill-license::before { background: var(--aigacp); }
```

- [ ] **Step 2: Fix BedrockOS platform pill**

Find (around line 846):
```html
<span class="pill pill-dev">In Dev</span>
```
Replace with:
```html
<span class="pill pill-license">Available to License</span>
```

- [ ] **Step 3: Fix Offload platform pill**

Find (around line 905):
```html
<span class="pill pill-dev">Coming Soon</span>
```
Replace with:
```html
<span class="pill pill-dev">Beta</span>
```

- [ ] **Step 4: Fix marquee — first pass**

Find (around lines 767–770):
```html
<span class="marquee-item"><span class="m-dot"></span>BedrockOS — In Development</span>
<span class="marquee-item"><span class="m-dot"></span>Offload — Coming Soon</span>
```
Replace with:
```html
<span class="marquee-item"><span class="m-dot"></span>BedrockOS — Available to License</span>
<span class="marquee-item"><span class="m-dot"></span>Offload — Beta</span>
```

- [ ] **Step 5: Fix marquee — second pass (duplicate set)**

Find (around lines 771–774 — the repeated marquee items):
```html
<span class="marquee-item"><span class="m-dot"></span>BedrockOS — In Development</span>
<span class="marquee-item"><span class="m-dot"></span>Offload — Coming Soon</span>
```
Replace with:
```html
<span class="marquee-item"><span class="m-dot"></span>BedrockOS — Available to License</span>
<span class="marquee-item"><span class="m-dot"></span>Offload — Beta</span>
```

- [ ] **Step 6: Verify in browser**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B screenshot /tmp/task1-labels.png
```
Read `/tmp/task1-labels.png`. Confirm: BedrockOS row shows a green-tinted "Available to License" pill; Offload row shows muted "Beta" pill. Marquee scrolls the updated text.

- [ ] **Step 7: Commit**

```bash
cd /Users/tui/Desktop/aiga-website
git add index.html
git commit -m "fix: update BedrockOS and Offload status labels"
```

---

## Task 2: Rewrite hero copy and add Consulting nav link

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update nav — add Consulting link**

Find the nav block (around line 791):
```html
<nav id="mainNav">
    <a href="#platforms">Platforms</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
    <a href="#contact" class="nav-cta">Build With Us</a>
</nav>
```
Replace with:
```html
<nav id="mainNav">
    <a href="#platforms">Platforms</a>
    <a href="#consulting">Consulting</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
    <a href="#contact" class="nav-cta">Build With Us</a>
</nav>
```

- [ ] **Step 2: Update hero H1**

Find (around line 817):
```html
<h1 class="hero-h1">We build software<br>that <em>thinks.</em></h1>
```
Replace with:
```html
<h1 class="hero-h1">Built from inside<br>the <em>industry.</em></h1>
```

- [ ] **Step 3: Update hero sub-paragraph**

Find (around line 818):
```html
<p class="hero-sub">AIGA is a platform studio. We build AI-powered vertical platforms for construction, finance, education, and cognition — and we only build in domains we've worked in. Every product is built from the inside out.</p>
```
Replace with:
```html
<p class="hero-sub">AIGA is a platform studio and AI advisory run by a 20-year civil superintendent. Our flagship, BedrockOS, is a modular construction OS built by someone who's run the job — available to license today. We also help organizations find where AI fits in their operations and build the tools to act on it.</p>
```

- [ ] **Step 4: Update hero CTAs**

Find (around lines 820–823):
```html
<a href="#platforms" class="btn btn-solid">See Our Platforms</a>
<a href="#contact" class="btn btn-ghost">Build With Us</a>
```
Replace with:
```html
<a href="#platforms" class="btn btn-solid">License BedrockOS</a>
<a href="#consulting" class="btn btn-ghost">Explore AI Consulting</a>
```

- [ ] **Step 5: Verify in browser**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B screenshot /tmp/task2-hero.png
```
Read `/tmp/task2-hero.png`. Confirm: H1 reads "Built from inside the industry." with "industry." in muted italic; sub-paragraph mentions BedrockOS and AI advisory; buttons read "License BedrockOS" and "Explore AI Consulting"; nav includes "Consulting" between Platforms and About.

- [ ] **Step 6: Commit**

```bash
cd /Users/tui/Desktop/aiga-website
git add index.html
git commit -m "feat: rewrite hero with founder story and consulting CTA"
```

---

## Task 3: Add AI Workflow Consulting section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add `.consulting-section` CSS**

In the `<style>` block, find the `/* ─── Contact ─── */` comment (around line 559). Add immediately before it:

```css
/* ─── Consulting ─── */
.consulting-section {
    padding: 100px 40px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: start;
    border-top: 1px solid var(--border);
}
```

- [ ] **Step 2: Add responsive rules for `.consulting-section`**

In the `@media (max-width: 1024px)` block (around line 719), add:
```css
.consulting-section { grid-template-columns: 1fr; gap: 48px; }
```

In the `@media (max-width: 768px)` block (around line 729), add:
```css
.consulting-section { padding: 72px 20px; }
```

- [ ] **Step 3: Insert the consulting section HTML**

Find the closing `</div>` of the platforms block followed immediately by the Stats section-rule (around lines 908–911):
```html
</div>

<!-- Stats -->
<div class="section-rule" id="about">
```
Insert the new consulting section between them:
```html
</div>

<!-- Consulting -->
<div class="section-rule" id="consulting">
    <span class="rule-label">AI Workflow Consulting</span>
    <div class="rule-line"></div>
    <span class="rule-meta">Personally Delivered</span>
</div>

<section class="consulting-section">
    <div class="rv">
        <div class="ct-label">The Offering</div>
        <h2 class="ct-h2">Where are you losing time to work that shouldn't need a human?</h2>
        <p class="ct-sub">Most organizations aren't failing at AI — they haven't mapped where it actually fits. Tui works directly with your team to find the friction, assess where AI creates real leverage, and help you act on it. Any industry.</p>
        <a href="mailto:info@aigaai.com?subject=AI Consulting" class="ct-email">Start a Conversation</a>
    </div>
    <div class="rv">
        <div class="ct-options">
            <a href="mailto:info@aigaai.com?subject=AI Consulting - Workflow Audit" class="ct-opt"><div class="ct-dot"></div><span><strong>Workflow Audit</strong> — Map where time actually goes and find the drag</span></a>
            <a href="mailto:info@aigaai.com?subject=AI Consulting - AI Fit Assessment" class="ct-opt"><div class="ct-dot"></div><span><strong>AI Fit Assessment</strong> — Identify which problems AI solves vs. which need a process fix first</span></a>
            <a href="mailto:info@aigaai.com?subject=AI Consulting - Implementation" class="ct-opt"><div class="ct-dot"></div><span><strong>Implementation</strong> — Recommend tools, guide adoption, or build something custom</span></a>
        </div>
    </div>
</section>

<!-- Stats -->
<div class="section-rule" id="about">
```

- [ ] **Step 4: Verify in browser**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B js "document.getElementById('consulting').scrollIntoView()"
$B screenshot /tmp/task3-consulting.png
```
Read `/tmp/task3-consulting.png`. Confirm: section rule reads "AI Workflow Consulting · Personally Delivered"; left column has the heading and body copy; right column shows three bordered option rows for Workflow Audit, AI Fit Assessment, Implementation; "Start a Conversation" appears as a large serif link.

- [ ] **Step 5: Verify responsive at mobile width**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B viewport 375x812
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B js "document.getElementById('consulting').scrollIntoView()"
$B screenshot /tmp/task3-consulting-mobile.png
```
Read `/tmp/task3-consulting-mobile.png`. Confirm: single column layout, no horizontal overflow.

- [ ] **Step 6: Commit**

```bash
cd /Users/tui/Desktop/aiga-website
git add index.html
git commit -m "feat: add AI Workflow Consulting section"
```

---

## Task 4: Rewrite manifesto copy and attribution

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Update manifesto quote**

Find (around lines 941–944):
```html
<p class="mf-quote rv">
    AIGA doesn't take briefs from the outside. We operate <em>within the domains</em> we build for — which means our products reflect how work actually happens, not how it looks on a whiteboard.
</p>
```
Replace with:
```html
<p class="mf-quote rv">
    I'm a civil superintendent with 20 years in the field, currently managing a $500M+ infrastructure job. Every product AIGA has built started as a problem I couldn't solve with what existed. We don't consult from the outside — we're <em>already inside it.</em>
</p>
```

- [ ] **Step 2: Update manifesto attribution**

Find (around lines 945–948):
```html
<div class="mf-attr rv">
    <div class="mf-line"></div>
    <span class="mf-text">Inside the problem. Every time.</span>
</div>
```
Replace with:
```html
<div class="mf-attr rv">
    <div class="mf-line"></div>
    <span class="mf-text">Tui Alailima — Civil Superintendent, Founder</span>
</div>
```

- [ ] **Step 3: Verify in browser**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B viewport 1280x720
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B js "document.querySelector('.manifesto').scrollIntoView()"
$B screenshot /tmp/task4-manifesto.png
```
Read `/tmp/task4-manifesto.png`. Confirm: large serif quote reads the new copy ending with italic "already inside it."; attribution line reads "Tui Alailima — Civil Superintendent, Founder".

- [ ] **Step 4: Commit**

```bash
cd /Users/tui/Desktop/aiga-website
git add index.html
git commit -m "feat: update manifesto with founder credentials"
```

---

## Task 5: Add consulting to contact section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add consulting option row**

Find the `ct-options` div in the contact section (around lines 957–962):
```html
<div class="ct-options">
    <a href="mailto:info@aigaai.com?subject=Deploy AIGA Platform" class="ct-opt"><div class="ct-dot"></div>Deploy a platform in your organization</a>
    <a href="mailto:info@aigaai.com?subject=Product Partnership" class="ct-opt"><div class="ct-dot"></div>Partner on a new product idea</a>
    <a href="mailto:info@aigaai.com?subject=Investment Inquiry" class="ct-opt"><div class="ct-dot"></div>Invest in what we're building</a>
</div>
```
Replace with:
```html
<div class="ct-options">
    <a href="mailto:info@aigaai.com?subject=AI Consulting" class="ct-opt"><div class="ct-dot"></div>Explore AI workflow consulting</a>
    <a href="mailto:info@aigaai.com?subject=Deploy AIGA Platform" class="ct-opt"><div class="ct-dot"></div>Deploy a platform in your organization</a>
    <a href="mailto:info@aigaai.com?subject=Product Partnership" class="ct-opt"><div class="ct-dot"></div>Partner on a new product idea</a>
    <a href="mailto:info@aigaai.com?subject=Investment Inquiry" class="ct-opt"><div class="ct-dot"></div>Invest in what we're building</a>
</div>
```

- [ ] **Step 2: Add consulting option to select dropdown**

Find the select dropdown options (around lines 980–989). Find the Offload option:
```html
<option value="offload">Offload — Cognitive Inbox</option>
<option value="build">I have an idea I want to build</option>
```
Insert the consulting option between them:
```html
<option value="offload">Offload — Cognitive Inbox</option>
<option value="consulting">AI Workflow Consulting</option>
<option value="build">I have an idea I want to build</option>
```

- [ ] **Step 3: Verify in browser**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B viewport 1280x720
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B js "document.getElementById('contact').scrollIntoView()"
$B screenshot /tmp/task5-contact.png
```
Read `/tmp/task5-contact.png`. Confirm: "Explore AI workflow consulting" appears as the first option row in the contact left column; the select dropdown includes "AI Workflow Consulting" as an option.

- [ ] **Step 4: Full page smoke check**

```bash
export PATH="$HOME/.bun/bin:$PATH"
B="$HOME/.claude/skills/gstack/browse/dist/browse"
$B viewport 1280x720
$B goto file:///Users/tui/Desktop/aiga-website/index.html
$B responsive /tmp/final-check
```
Read `/tmp/final-check-mobile.png`, `/tmp/final-check-tablet.png`, `/tmp/final-check-desktop.png`. Confirm no layout breaks at any viewport. Confirm the page flows: marquee → nav → hero → platforms → consulting → stats → manifesto → contact → footer.

- [ ] **Step 5: Commit**

```bash
cd /Users/tui/Desktop/aiga-website
git add index.html
git commit -m "feat: add AI consulting to contact section"
```
