# CFD Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the Centennial Family Dentistry redesign pitch — a lean brand MD system extracted from the live site, plus a 3-page Astro site deployed to GitHub Pages.

**Architecture:** Two phases in one repo. Phase 1 extracts evidence from https://www.cfdentistrysnohomish.com/ into dated immutable sources and drafts the 8-file brand system. Phase 2 builds an Astro static site (`site/`) against those brand files and deploys via GitHub Actions to `https://deliciousllc.github.io/cfd-website/`.

**Tech Stack:** Astro ^5 (static output, no integrations), plain CSS, GitHub Actions + Pages, Firecrawl CLI for scraping, Claude browser tools for screenshots/computed styles.

**Spec:** `architecture/specs/2026-07-22-cfd-website-design.md` — the spec wins on any conflict with this plan.

## Global Constraints

- Every fact (prices, hours, names, address, phone) is verbatim from the current site; every fact in `brand/products.md` cites source URL + capture date. Never improvise facts.
- Brand-file claims are tagged `[OBSERVED]` (evidenced on site) or `[INFERRED]` (analytical read); inferred items also get `[PROPOSED]` in decisions files.
- Primary CTA everywhere is **Call**: `tel:360-568-6017`. No forms, no booking.
- No fabricated testimonials, no stock-photo padding, no invented practice copy.
- Accessibility contract: WCAG AA contrast; meaningful alt text (empty alt for decorative); semantic landmarks + heading hierarchy (one `h1`/page, no skipped levels); full keyboard nav with visible focus; skip-to-content link; usable at 200% zoom without horizontal scroll.
- All internal links/assets respect the `/cfd-website` base path.
- Mobile-first, plain CSS, no UI framework, no client-side JS unless a component demands it (none is expected to).
- `brand/_sources/` files are dated and immutable once committed — new research = new dated file.
- Commit at the end of every task. **Every commit message ends with the trailer `Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>` — the example `git commit` commands in this plan omit it for brevity; the implementer MUST append it to each one.**
- Known facts already captured (from 2026-07-22 homepage scrape, re-verify in Task 1): doctors are Dr. Eve Rutherford DDS, Dr. Rachel Greene DDS, Dr. Samiksha Gulrajani DMD; address 133 Maple Ave Snohomish WA 98290; phone 360-568-6017; email info@cfdentistrysnohomish.com; Instagram @cfdentistrysnoho; Facebook /CFDsnohomish; bill pay https://bestcardteam.com/Payments/?Profile=centennialfamPAY.

---

### Task 1: Evidence gathering

**Files:**
- Create: `brand/_sources/2026-07-22/` (scrapes as `.md`/`.json`, screenshots as `.png`, `capture-log.md`)
- Create: `brand/_sources/2026-07-22/assets/` (logo + practice photos)
- Create: `.gitignore`

**Interfaces:**
- Produces: dated raw evidence that Tasks 2–6 cite by filename; `capture-log.md` lists every capture with URL + date + method.

- [ ] **Step 1: Create `.gitignore` and the evidence directories**

```gitignore
node_modules/
dist/
.astro/
.DS_Store
```

```bash
mkdir -p brand/_sources/2026-07-22/assets
```

- [ ] **Step 2: Scrape key pages with Firecrawl CLI**

Run (from repo root; one command per page, may run concurrently):

```bash
firecrawl scrape "https://www.cfdentistrysnohomish.com/about-us" --only-main-content -o brand/_sources/2026-07-22/about-us.md
firecrawl scrape "https://www.cfdentistrysnohomish.com/services-and-pricing" --only-main-content -o brand/_sources/2026-07-22/services-and-pricing.md
firecrawl scrape "https://www.cfdentistrysnohomish.com/financing" --only-main-content -o brand/_sources/2026-07-22/financing.md
firecrawl scrape "https://www.cfdentistrysnohomish.com/about-me" --only-main-content -o brand/_sources/2026-07-22/reviews.md
firecrawl scrape "https://www.cfdentistrysnohomish.com/routine-cleanings-and-exams" --only-main-content -o brand/_sources/2026-07-22/routine-cleanings-and-exams.md
firecrawl scrape "https://www.cfdentistrysnohomish.com/laser" --only-main-content -o brand/_sources/2026-07-22/laser.md
firecrawl scrape "https://www.cfdentistrysnohomish.com/3d-printing" --only-main-content -o brand/_sources/2026-07-22/3d-printing.md
```

Also capture the homepage:

```bash
firecrawl scrape "https://www.cfdentistrysnohomish.com/" --format markdown,links -o brand/_sources/2026-07-22/home.json
```

Expected: each file non-empty; verify with `wc -l brand/_sources/2026-07-22/*.md`.

- [ ] **Step 3: Screenshots at desktop and mobile widths**

Using browser tools: navigate to the homepage, `resize_window` to desktop preset (1280×800), take `screenshot`, save/export to `brand/_sources/2026-07-22/home-desktop.png`. Repeat with mobile preset (375×812) → `home-mobile.png`. Repeat both widths for `/services-and-pricing` → `services-desktop.png`, `services-mobile.png`.

Fallback if the browser pane cannot export PNG files: for each page,

```bash
firecrawl scrape "<url>" --format screenshot -o /tmp/shot.json
```

then extract the screenshot URL from the JSON (`python3 -c "import json;print(json.load(open('/tmp/shot.json'))['screenshot'])"` — adjust the key to what the JSON actually contains) and download it: `curl -sL "<screenshot-url>" -o brand/_sources/2026-07-22/<name>.png`. Verify each PNG is non-empty and actually opens (`file *.png`). Note in `capture-log.md` that fallback screenshots are desktop-width only, if so.

- [ ] **Step 4: Extract computed styles from the rendered homepage**

With the homepage open in the browser, run via `javascript_tool`:

```js
(() => {
  const pick = (el) => {
    if (!el) return null;
    const s = getComputedStyle(el);
    return { fontFamily: s.fontFamily, fontSize: s.fontSize, fontWeight: s.fontWeight, color: s.color, background: s.backgroundColor };
  };
  return JSON.stringify({
    body: pick(document.body),
    h1: pick(document.querySelector('h1')),
    h2: pick(document.querySelector('h2')),
    nav: pick(document.querySelector('nav')),
    link: pick(document.querySelector('main a, a')),
    button: pick(document.querySelector('button, [role="button"]'))
  }, null, 2);
})()
```

Save output to `brand/_sources/2026-07-22/computed-styles.json`. Rule: fonts are identified from computed style only — never from grepping CSS.

- [ ] **Step 5: Download logo and key practice photos**

```bash
curl -sL "https://static.wixstatic.com/media/856d6c_eee4de226298462ab906c7094949a442~mv2.jpg" -o brand/_sources/2026-07-22/assets/logo.jpg
curl -sL "https://static.wixstatic.com/media/856d6c_78084747d26b4b9ebb102e8e5f1e7070~mv2.jpg" -o brand/_sources/2026-07-22/assets/building.jpg
```

From the Task 1 scrapes, identify doctor/team photos on `about-us` and download each the same way (strip Wix transform params — everything from `/v1/` onward — to get the original). Sample the logo's dominant colors (e.g., ImageMagick: `magick brand/_sources/2026-07-22/assets/logo.jpg -resize 1x1 txt:-` for average, and `-colors 5 -unique-colors txt:-` for a palette) and save the hex values into `capture-log.md`.

- [ ] **Step 6: Write `brand/_sources/2026-07-22/capture-log.md`**

A table: filename · source URL · capture date (2026-07-22) · method (firecrawl/browser/curl). Include the logo color-sample hexes. Note any page that failed to scrape and how it was handled.

- [ ] **Step 7: Commit**

```bash
git add -A && git commit -m "Add dated brand evidence sources from live site"
```

---

### Task 2: Service inventory map

**Files:**
- Create: `brand/_sources/2026-07-22/service-inventory.md`

**Interfaces:**
- Consumes: Task 1 scrapes (nav link list in `home.json`).
- Produces: the authoritative source-page → destination-section map used by Tasks 3 and 10–12. No ad-hoc grouping decisions later.

- [ ] **Step 1: Enumerate every nav item from the homepage scrape AND the rendered nav**

From `home.json` links, list all ~20 nav items with their URLs, including duplicates (Sleep apnea appears twice) and junk slugs (`blank-page`, `blank-page-1`, `copy-of-*`). Then cross-check against the rendered site: open the live homepage in the browser, `read_page`, and enumerate the nav menu (including anything under "More") — the link dump alone may include footer/incidental links or miss client-rendered entries. The **union** of both lists, deduplicated by URL, is the inventory. Note any discrepancy between the two sources in the inventory file.

- [ ] **Step 2: Map each item to exactly one destination**

Table columns: source item · source URL · destination (page + section) · notes. Required destinations (from spec): Services & Pricing groups with **these locked names and anchor IDs** (Tasks 10–11 use them verbatim):

| Group name | Anchor ID | Members |
|---|---|---|
| Routine care | `#routine-care` | Routine Cleanings and Exams |
| Restorative | `#restorative` | Fillings and Crowns |
| Cosmetic | `#cosmetic` | Cosmetic Dentistry, Teeth Whitening, Invisalign, Botox and Fillers/Botox (merge the two Botox entries) |
| Sleep & TMJ | `#sleep-tmj` | Sleep Apnea (×2, merged), TMJ |
| Technology & extras | `#technology-extras` | Laser Dentistry, 3D Printing, Willo Toothbrush, Kids' Days |
| Financing | `#financing` | Financing page content |

(The spec's shorthand for the last group was "extras"; "Technology & extras" is the display name — recorded here as the authoritative rename.) About Us + Reviews → About page (reviews also excerpted on Home). Blog → omitted, reason: out of scope per spec. Duplicate/junk slugs → merged/omitted with reason. Every source item must appear exactly once as mapped or omitted-with-reason.

- [ ] **Step 3: Scrape any mapped source page not yet captured**

Compare the inventory's mapped URLs against `brand/_sources/2026-07-22/`. For every mapped service page not scraped in Task 1 (e.g., fillings-and-crowns, cosmetic-dentistry, the sleep apnea pages, TMJ, Invisalign, teeth whitening, Willo, Kids' Days, Botox), run:

```bash
firecrawl scrape "<url>" --only-main-content -o brand/_sources/2026-07-22/<slug>.md
```

Add each to `capture-log.md`. Task 3's "every service and price verbatim" contract depends on this being complete — a mapped page with no scrape is a plan violation.

- [ ] **Step 4: Commit**

```bash
git add -A && git commit -m "Add service inventory map and complete source-page scrapes"
```

---

### Task 3: products.md — verbatim facts

**Files:**
- Create: `brand/products.md`

**Interfaces:**
- Consumes: Task 1 scrapes, Task 2 map.
- Produces: the single source of truth for all facts on the site. Tasks 10–12 pull facts ONLY from here.

- [ ] **Step 1: Draft `brand/products.md`**

Structure (fill every section from scrapes; each fact line ends with `(source: <URL>, captured 2026-07-22)`):

```markdown
# Products & Facts — Centennial Family Dentistry

## Locked Terminology & Fact Gotchas

**Never improvise practice facts.** If a fact isn't in this file, ask — do not fill
the gap from general knowledge. When a correction happens, it becomes a numbered
rule here the same session.

1. (grows from corrections)

## Practice identity
(official name, tagline if any, doctors with exact credentials as written)

## Contact & location
(address, phone, email, socials, bill-pay URL)

## Hours of operation
(verbatim from homepage, including "Friday: By Appointment Only")

## Services & pricing
(one subsection per Task-2 service group; every service with any price listed
on the site carries the exact price verbatim; services without listed prices
say "no price listed on source site")

## Financing
(verbatim summary of what the financing page actually offers)

## Reviews
(verbatim quotes with attribution exactly as shown on the reviews page; if
reviews are only images, transcribe via browser read of the live page and
note "transcribed from image" per quote. If a quote cannot be read reliably,
exclude it — never reconstruct.)
```

- [ ] **Step 2: Verify no fact lacks provenance**

Formatting contract for this file: every fact is a `- ` bullet ending with its `(source: …, captured 2026-07-22)` citation; prose lines carry no facts. Then the check is mechanical:

Run: `grep -nE '^- ' brand/products.md | grep -v 'source:'`
Expected: zero output. Any line it prints is a fact bullet missing provenance — fix it. Then read the non-bullet prose once to confirm no fact snuck into prose form.

- [ ] **Step 3: Commit**

```bash
git add -A && git commit -m "Add products.md: verbatim practice facts with provenance"
```

---

### Task 4: Visual family

**Files:**
- Create: `brand/visual.md`, `brand/visual_decisions.md`, `brand/visual_handoff.md`

**Interfaces:**
- Consumes: `computed-styles.json`, logo color samples, screenshots, Task 1 imagery.
- Produces: design tokens (CSS-ready hex/font values) that Task 9 copies into `site/src/styles/global.css` verbatim.

- [ ] **Step 1: Draft `brand/visual.md`**

Required sections:
- **Design tokens** — table: token name · value · status tag. Colors: primary (from logo sample), accent, neutrals, plus WCAG-AA-checked text/background pairs `[OBSERVED]` where taken from site/logo, `[PROPOSED]` where adjusted for contrast. Typography: if computed fonts are Wix-proprietary, pick the nearest open equivalent (self-hosted or system stack — no external font CDN, Pages + performance), tag `[PROPOSED]`, record reasoning in visual_decisions.md. Type scale (body 16px min, h1/h2/h3), spacing scale, one border-radius, one shadow.
- **Imagery rules** — real practice photos over stock; the building photo and hometown-Snohomish imagery `[OBSERVED]`; treatment/crop rules `[PROPOSED]`.
- **Channel rules** — website-only for now; mobile-first.

- [ ] **Step 2: Draft `brand/visual_decisions.md`**

Per the guide: "what this file is" preamble with portability discipline (invariant vs expression; deletion test: a reason naming a hex/font/px is an expression → belongs in visual.md); "why this aesthetic" paragraph; design invariants tagged `[RATIFIED]`/`[PROPOSED]`/`[PREFERENCE]`/`[CONSTRUCTION]`; every `[INFERRED]` visual claim from Step 1 logged here as `[PROPOSED]`; open register at bottom.

- [ ] **Step 3: Draft `brand/visual_handoff.md`**

WITH section: load order (visual.md, then products.md for any content), "Rules that survive if nothing else is loaded" (≤6 lines: token values are exact, never approximated; AA contrast; real photos only; mobile-first; facts from products.md verbatim; check gotchas). Pre-delivery QA gate: token pass · contrast pass · render pass (look at the rendered result). ON section: how to change tokens (bump revision, log in visual_decisions.md, ripple-check). `## State of play (one paragraph — as of 2026-07-22)`.

- [ ] **Step 4: Commit**

```bash
git add -A && git commit -m "Add visual family: extracted tokens, decisions, handoff"
```

---

### Task 5: Voice family

**Files:**
- Create: `brand/voice.md`, `brand/voice_decisions.md`, `brand/voice_handoff.md`

**Interfaces:**
- Consumes: all Task 1 scrapes (the practice's actual written copy).
- Produces: voice rules that all site copy in Tasks 10–12 must pass.

- [ ] **Step 1: Draft `brand/voice.md`**

Required sections per the guide: **Emotional engine** (customer inner life + core conviction — `[INFERRED]` unless stated on site; pricing transparency conviction is `[OBSERVED]` if the pricing page confirms it); **Personality** (3 words with in-practice meaning, tag each); **Rules** (≤10 — e.g., "doctors are named people, not 'our team'" `[OBSERVED]`, "prices stated plainly, never 'contact us for pricing' when a price exists" `[OBSERVED]`); **Anti-patterns** (no corporate-dental hype, no fear-based copy, no fabricated warmth — each tagged); **Messaging tiers** (brand-level vs page-level).

- [ ] **Step 2: Draft `brand/voice_decisions.md`**

Key choices + rejected directions with status tags; every `[INFERRED]` voice claim logged as `[PROPOSED]`; open register at bottom.

- [ ] **Step 3: Draft `brand/voice_handoff.md`**

WITH: load order (voice.md → products.md); "Rules that survive if nothing else is loaded" (≤6, must include: facts from products.md verbatim — never improvise; no invented practice copy). Pre-delivery QA gate: guardrail pass · fact pass (every claim traces to products.md) · specificity pass (could this sentence be any dentist? → rewrite) · clarity pass. ON section + `## State of play (one paragraph — as of 2026-07-22)`.

- [ ] **Step 4: Commit**

```bash
git add -A && git commit -m "Add voice family: rules, decisions, handoff"
```

---

### Task 6: _START_HERE.md and root CLAUDE.md

**Files:**
- Create: `brand/_START_HERE.md`
- Create: `CLAUDE.md` (repo root)
- Create: `README.md` (repo root)

**Interfaces:**
- Consumes: all brand files from Tasks 3–5.
- Produces: the entry points every future session loads.

- [ ] **Step 1: Draft `brand/_START_HERE.md`**

Master map: file table (file · what it is · when to load); task→handoff lookup ("site copy → voice_handoff.md"; "styling/tokens → visual_handoff.md"; "any fact → products.md"); family tree; maintenance rules including the July additions (rules live at point of use; research snapshots dated + immutable; never rename without a full-folder sweep; status-line discipline; grow gotchas from corrections; rule lists soft cap ~10 / handoffs ~150 lines).

- [ ] **Step 2: Draft root `CLAUDE.md`**

```markdown
# cfd-website — session instructions

Redesign pitch for Centennial Family Dentistry (Snohomish, WA).
Spec: `architecture/specs/2026-07-22-cfd-website-design.md`.
Brand system: start at `brand/_START_HERE.md`; load the relevant `*_handoff.md` before brand or copy work.
Site: Astro project in `site/` — dev: `cd site && npm run dev`; deploys to GitHub Pages via Actions on push to main. Base path is `/cfd-website` — all internal links/assets must respect it.

## Hard rules (every session, every model)
- **Never improvise facts.** Prices, hours, names, contact details come verbatim from
  `brand/products.md` (check its Locked Terminology & Fact Gotchas). Not there → ask.
- **Primary CTA is Call (`tel:360-568-6017`) everywhere.** No forms, no booking flows.
- **No fabricated practice content** — no invented testimonials, copy, or stock-photo padding.
- **Corrections go into files the same session** (facts → products.md gotchas; rules → the
  owning driver/handoff).
- **`brand/_sources/` is immutable** — new research gets a new dated folder.
- **Never present a rendered/visual change without rendering it** (browser, mobile + desktop).
- **If a handoff's State of play isn't from the most recent session, compress it first.**

## Universal session shape (every production session)
1. **Startup inventory** — read the relevant handoff's State of play; verify last session's
   write-back landed; compress if stale.
2. **Work** — load reference files per the handoff's table.
3. **QA gate** — run the handoff's pre-delivery gate on the finished artifact.
4. **Write-back** — fresh dated State of play; decisions logged; revisions bumped.

<!-- seed version: July 2026 -->
```

- [ ] **Step 3: Draft `README.md`**

Short: what this repo is, live URL, layout (brand/ · site/ · architecture/), how to run the site locally.

- [ ] **Step 4: Commit and push**

```bash
git add -A && git commit -m "Add brand system entry points and project CLAUDE.md" && git push
```

---

### Task 7: CHECKPOINT — owner gut-check (not a subagent task)

- [ ] **Step 1:** Present Josh every `[PROPOSED]`/`[INFERRED]` item from `visual_decisions.md` and `voice_decisions.md`, grouped, with one-line rationale each. Scope per spec: plausibility and presentation only — items stay tagged as hypotheses regardless; the practice is the only ratifier. Apply any corrections to the brand files (same session, per hard rules) before starting Task 8.

- [ ] **Step 2: Commit the checkpoint outcome** (even if no corrections: amend the decisions files' State of play noting the check happened)

```bash
git add -A && git commit -m "Owner gut-check of inferred brand items: corrections applied" && git push
```

---

### Task 8: Astro scaffold

**Files:**
- Create: `site/package.json`, `site/astro.config.mjs`, `site/src/pages/index.astro` (placeholder)

**Interfaces:**
- Produces: working Astro project; `npm run dev` serves, `npm run build` emits `site/dist/`. Base path config later tasks rely on.

- [ ] **Step 1: Create `site/package.json`**

```json
{
  "name": "cfd-website",
  "type": "module",
  "private": true,
  "scripts": {
    "dev": "astro dev",
    "build": "astro build",
    "preview": "astro preview"
  },
  "dependencies": {
    "astro": "^5.0.0"
  }
}
```

- [ ] **Step 2: Create `site/astro.config.mjs`**

```js
import { defineConfig } from 'astro/config';

export default defineConfig({
  site: 'https://deliciousllc.github.io',
  base: '/cfd-website',
});
```

- [ ] **Step 3: Create placeholder `site/src/pages/index.astro`**

```astro
---
---
<html lang="en">
  <head><meta charset="utf-8" /><title>Centennial Family Dentistry</title></head>
  <body><h1>Scaffold OK</h1></body>
</html>
```

- [ ] **Step 4: Install and verify build**

Run: `cd site && npm install && npm run build`
Expected: build succeeds, `dist/index.html` exists.

- [ ] **Step 5: Verify dev server renders**

Start the dev server via the browser preview tooling (launch config: `npm run dev` in `site/`, port 4321), open `http://localhost:4321/cfd-website/` (note the base path), confirm "Scaffold OK" renders.

- [ ] **Step 6: Commit**

```bash
git add -A && git commit -m "Scaffold Astro site with GitHub Pages base path"
```

---

### Task 9: Layout, nav, footer, global styles

**Files:**
- Create: `site/src/layouts/BaseLayout.astro`, `site/src/components/Nav.astro`, `site/src/components/Footer.astro`, `site/src/styles/global.css`
- Create: `site/public/` assets (logo + photos copied from `brand/_sources/2026-07-22/assets/`, web-optimized)
- Modify: `site/src/pages/index.astro` (use BaseLayout)

**Interfaces:**
- Consumes: tokens from `brand/visual.md` (copied verbatim into CSS custom properties); facts from `brand/products.md`.
- Produces: `BaseLayout.astro` with props `{ title: string, description: string }` and a default slot — Tasks 10–12 wrap every page in it. Global CSS custom properties (`--color-primary`, `--color-accent`, `--color-text`, `--color-bg`, `--space-*`, `--font-body`, `--font-heading`).

**Mobile nav spec (locked here, per spec requirement):** No hamburger, no JS. ≥768px: single bar — logo/wordmark left; links Home, Services & Pricing, About center/right; Call button (tel:) far right. <768px: two rows — row 1: wordmark + Call button; row 2: the three links evenly spaced. Active page gets `aria-current="page"` + visible treatment (underline/color from tokens). All interactive elements show `:focus-visible` outline. First element inside `<body>` is the skip-to-content link targeting `#main`.

- [ ] **Step 1: Write `site/src/styles/global.css`**

CSS reset (box-sizing, margin 0), custom properties from `brand/visual.md` tokens verbatim, base typography (body 16px min, line-height ≥1.5), `:focus-visible` outline style, `.skip-link` (visually hidden until focused), container width utility. Mobile-first media queries at 768px.

- [ ] **Step 2: Write `Nav.astro` and `Footer.astro`**

Nav per the locked spec above. **Active-page interface:** `Nav.astro` derives the current route itself from `Astro.url.pathname` — no prop from BaseLayout. Normalize before comparing: strip the `import.meta.env.BASE_URL` prefix and any trailing slash, giving `''` (home), `'services'`, or `'about'`; each nav link whose route matches gets `aria-current="page"` plus the active visual treatment. Footer: hours (verbatim from products.md), address, phone (tel: link), email, Instagram + Facebook links, bill-pay link — all from `brand/products.md`. Footer includes a small pitch disclaimer: "Concept redesign by Delicious LLC — not the practice's official site." (Required: this is spec work; the site must not impersonate the practice's official presence.)

- [ ] **Step 3: Write `BaseLayout.astro`**

Props `{ title, description }`; `<html lang="en">`; meta viewport; imports global.css; skip link → `<Nav/>` → `<main id="main"><slot/></main>` → `<Footer/>`. All asset/internal URLs via `import.meta.env.BASE_URL` or Astro's base-aware helpers.

- [ ] **Step 4: Optimize and copy assets**

Copy logo + selected photos into `site/public/images/` (ImageMagick: resize to max 1600px wide, quality ~82, strip metadata). Sources in `brand/_sources/` stay untouched (immutable); the optimized copies in `site/public/images/` are the ones pages reference.

- [ ] **Step 5: Update `index.astro` to use BaseLayout, verify in browser**

Wrap placeholder content. Dev server: confirm nav/footer render at 375px and 1280px, keyboard-tab through nav shows focus, skip link appears on first Tab. (Active-state verification across all three routes happens in Task 13 once all pages exist; for now confirm Home shows `aria-current="page"` on the Home link.)

- [ ] **Step 6: Commit**

```bash
git add -A && git commit -m "Add base layout, nav, footer, global styles from brand tokens"
```

---

### Task 10: Home page

**Files:**
- Modify: `site/src/pages/index.astro`

**Interfaces:**
- Consumes: BaseLayout; facts from `brand/products.md`; voice rules from `brand/voice.md`; service groups from `service-inventory.md`.

- [ ] **Step 1: Load `brand/voice_handoff.md` WITH section, then build the page**

Sections in order: **Hero** (practice name, one-line identity statement passing the voice specificity test, Call CTA button, real practice photo); **Services overview** (the five Task-2 groups as cards linking to Services page sections via anchor links); **Meet the doctors teaser** (three names + link to About); **Reviews strip** (2–3 verbatim quotes from products.md); **Visit us** (hours, address with Google Maps link, phone).

- [ ] **Step 2: Run the voice QA gate on the finished page copy**

Guardrail · fact · specificity · clarity passes from `voice_handoff.md`. One reported line per pass.

- [ ] **Step 3: Browser-verify at 375px and 1280px, then commit**

```bash
git add -A && git commit -m "Add home page"
```

---

### Task 11: Services & Pricing page

**Files:**
- Create: `site/src/pages/services.astro`

**Interfaces:**
- Consumes: BaseLayout; `service-inventory.md` groups (authoritative — no regrouping); prices verbatim from `brand/products.md`.

- [ ] **Step 1: Build the page**

One section per service group with `id` anchors matching Home's card links. Every service from the inventory map appears in its mapped group. Prices shown exactly as sourced; services without listed prices show no price (never "call for pricing" unless the source says it). **Financing** section at bottom from products.md. Pricing-transparency framing kept prominent (it's the differentiator per spec).

- [ ] **Step 2: Cross-check against the inventory map**

Every row of `service-inventory.md` marked "Services & Pricing" appears exactly once on the page. List any mismatch and fix.

- [ ] **Step 3: Voice QA gate + browser verify both widths + commit**

```bash
git add -A && git commit -m "Add services and pricing page"
```

---

### Task 12: About page

**Files:**
- Create: `site/src/pages/about.astro`

**Interfaces:**
- Consumes: BaseLayout; doctor names/credentials + practice copy facts from `brand/products.md`; photos from Task 9 assets.

- [ ] **Step 1: Build the page**

Sections: **The doctors** (three, exact names/credentials, photos if captured — no photo → clean text card, never a stock face); **The practice** (story from about-us scrape facts only, building photo); **Reviews** (fuller set of verbatim quotes); **Socials + contact**.

- [ ] **Step 2: Voice QA gate + browser verify both widths + commit**

```bash
git add -A && git commit -m "Add about page"
```

---

### Task 13: Accessibility + full-site verification pass

**Files:**
- Modify: any page/component fixes that fall out

**Interfaces:**
- Consumes: the accessibility contract in the spec (Deployment & verification section).

- [ ] **Step 1: Contrast check**

For every token text/background pair actually used, verify AA (4.5:1 normal, 3:1 large) — compute ratios from the hex values (e.g., a small node/python script or a browser-run snippet). Fix failures in `global.css` and record the change in `visual_decisions.md` as `[PROPOSED]` adjustment.

- [ ] **Step 2: Structure + alt-text audit**

On each built page in `site/dist/` (run `npm run build`): exactly one `h1`; no skipped heading levels; `<header>/<nav>/<main>/<footer>` landmarks present; every `<img>` has meaningful alt or `alt=""` if decorative. Mechanical check for missing alt attributes (flatten first so multiline tags can't evade it):

```bash
for f in $(find site/dist -name '*.html'); do tr '\n' ' ' < "$f" | grep -oE '<img[^>]*>' | grep -v 'alt='; done
```

Expected: zero output — any printed `<img>` tag lacks an alt attribute. This only proves presence; read each page's alt texts yourself to confirm they're meaningful (not filenames or "image").

Also verify the nav active state here: visit all three routes in `npm run preview`; each page's own nav link (and only it) carries `aria-current="page"` with the visible active treatment.

- [ ] **Step 3: Keyboard + zoom pass in the browser**

Tab through every page: skip link first, visible focus on all interactive elements, logical order. Set 200% zoom at 1280px: no horizontal scroll, no clipped content.

- [ ] **Step 4: Link pass**

Every internal link resolves under the `/cfd-website` base in `npm run preview`; every external link (socials, bill pay, maps) opens the right target. `tel:` link is `tel:360-568-6017` everywhere it appears.

- [ ] **Step 5: Commit fixes**

```bash
git add -A && git commit -m "Accessibility and verification pass fixes"
```

---

### Task 14: Deploy to GitHub Pages

**Files:**
- Create: `.github/workflows/deploy.yml`

- [ ] **Step 1: Write `.github/workflows/deploy.yml`**

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: withastro/action@v3
        with:
          path: ./site

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

- [ ] **Step 2: Enable Pages with Actions as source**

Run: `gh api -X POST repos/deliciousllc/cfd-website/pages -f build_type=workflow`
If it returns 409 (already exists): `gh api -X PUT repos/deliciousllc/cfd-website/pages -f build_type=workflow`

- [ ] **Step 3: Push and watch the run**

```bash
git add -A && git commit -m "Add GitHub Pages deploy workflow" && git push
gh run watch --exit-status
```

Expected: build + deploy jobs green.

- [ ] **Step 4: Verify the live URL in a real browser**

Open `https://deliciousllc.github.io/cfd-website/` — all three pages render, images load (base path correct), nav works. Task is not done until the live URL renders. Spot-check on mobile width.

---

### Task 15: Wrap-up

- [ ] **Step 1: Re-verify facts against the live source site** — spot-check prices/hours/phone on cfdentistrysnohomish.com against `products.md`; any drift → fix products.md + affected pages, add a gotcha rule.
- [ ] **Step 2: If Step 1 changed any site file: redeploy and re-verify.** Commit + push the fixes, then `gh run watch --exit-status`, then re-check the live URL in the browser at 375px and 1280px (all changed pages). The delivered URL must be the version that passed verification — never push a fact fix and walk away.
- [ ] **Step 3: Update spec status** to "Implemented — live at https://deliciousllc.github.io/cfd-website/"; fresh State of play in both handoffs; README live-URL check.
- [ ] **Step 4: Final whole-branch review** (per SDD practice: per-task reviews miss cross-task bugs) — one reviewer pass over the full diff `git diff <first-commit>..HEAD` against spec + this plan. Findings adjudicated before close.
- [ ] **Step 5: Commit and push**

```bash
git add -A && git commit -m "Wrap up: verify facts, update spec status" && git push
```
