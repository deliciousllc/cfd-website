# CFD Website — Redesign Pitch Design

**Date:** 2026-07-22
**Status:** Approved in design session; awaiting external review
**Project:** `cfd-website` — spec-work redesign pitch for Centennial Family Dentistry (Snohomish, WA)

---

## Problem & purpose

Centennial Family Dentistry's current site (https://www.cfdentistrysnohomish.com/, Wix) has a flat navigation of ~20 items (including leftover slugs like `blank-page` and `copy-of-fillings-and-crowns-2`), no hero or call-to-action, stock photography mixed with real photos, and content organized as a wall of links. The practice has real strengths the site buries: three named doctors, unusual pricing transparency, and differentiating services (laser dentistry, 3D printing, Botox, sleep apnea, Kids' Days).

This project builds a redesign pitch — "here's what you could have" — not a commissioned rebuild. The audience is the practice owners; the goal is to make the improvement obvious enough to win the work.

## Success criteria

1. A live, shareable URL showing a modern, mobile-first 3-page site built from the practice's own real content.
2. Navigation reduced from ~20 flat items to ~4, with a defensible information architecture.
3. Every fact on the pitch site (prices, hours, names, address, phone) traces verbatim to the current site — nothing improvised.
4. A lean brand MD system in the repo that lets any future session work on this brand without re-explaining it.

## Scope decision

Option B from the design conversation: **homepage + 2 key pages** (Services & Pricing, About). Chosen over homepage-only (the broken IA is part of the pitch — showing the fixed structure matters) and over a full rebuild (more effort than a pre-commitment pitch warrants).

---

## Repo & project structure

New public repo `deliciousllc/cfd-website`, local at `~/Projects/cfd-website/`:

```
cfd-website/
├── CLAUDE.md            ← project instructions: points at brand/_START_HERE.md,
│                          hard rules + universal session shape (July 2026 update)
├── brand/               ← lean brand MD system (see Phase 1)
├── site/                ← Astro project (see Phase 2)
├── architecture/        ← specs/, plans/, reviews/
└── .github/workflows/   ← GitHub Pages deploy
```

## Phase 1 — Brand extraction

The brand MD system guide (`~/Projects/brand-system/brand_md_system_guide.md` + `brand_md_system_update_july2026.md`) is interview-driven; here the source is the existing site, so extraction replaces the interview.

**Evidence gathering:**
- Scrape key pages: About Us, Services & Pricing, Financing, Reviews, and 2–3 representative service pages.
- Screenshot the live site at desktop and mobile widths.
- Pull **computed** styles from rendered pages for actual fonts and colors (never grep CSS for fonts — verify via computed style).
- Capture the logo asset.

**Files to produce (lean subset):**

| File | Content |
|---|---|
| `brand/_START_HERE.md` | Master file map + maintenance rules (incl. July additions) |
| `brand/visual.md` | Extracted design tokens: logo colors, typography, imagery style, channel rules |
| `brand/visual_decisions.md` | Why-layer with portability discipline (invariant vs expression), status tags |
| `brand/visual_handoff.md` | WITH/ON session starter |
| `brand/voice.md` | How the practice talks: family-run warmth, named doctors, plain-spoken pricing transparency |
| `brand/voice_decisions.md` | Voice choices + rejected directions, status tags |
| `brand/voice_handoff.md` | WITH/ON, incl. "Rules that survive if nothing else is loaded" |
| `brand/products.md` | Real facts verbatim: services, pricing, hours, doctors, address, phone; opens with "Locked Terminology & Fact Gotchas" |

**Explicitly skipped:** the awareness/content-strategy family. The user is not familiar enough with the brand to define content strategy, and the guide says don't create files speculatively.

**Extraction adaptations (this is not an interview):**
- Every claim in the brand files is tagged **[OBSERVED]** (verbatim/directly evidenced on the site) or **[INFERRED]** (analytical read, e.g. "hometown Snohomish warmth" from hot-air-balloon and Huskies imagery).
- Inferred items are logged in the `*_decisions.md` files as `[PROPOSED]` for the user to gut-check — never silently promoted to rules.
- July 2026 update structure is baked in from day one: hard rules and universal session shape in `CLAUDE.md`, QA gates in handoffs, gotchas section in `products.md`, date-stamped State of play paragraphs.

## Phase 2 — The site

**Stack:** Astro static site, mobile-first, plain CSS (no UI framework unless a component demands it). Chosen over plain HTML/CSS because shared layout/nav/footer across 3+ pages needs componentization, and over the NAS review path because GitHub Pages fits "fully GitHub supported."

**Pages & information architecture:**

- **Home** — hero with practice identity and one primary CTA (call / request appointment), services overview, meet-the-doctors teaser, reviews strip, hours/location/contact block.
- **Services & Pricing** — the ~14 scattered service links consolidated into organized groups: routine care, restorative, cosmetic, sleep/TMJ, and extras (3D printing, Kids' Days, Willo). Pricing transparency kept front and center — a genuine differentiator for a dental practice. Financing folded in as a section on this page.
- **About** — the three doctors (Dr. Eve Rutherford DDS, Dr. Rachel Greene DDS, Dr. Samiksha Gulrajani DMD), practice story, the building, socials.

**Nav:** ~4 items (Home, Services & Pricing, About, and a call CTA). Footer on all pages carries hours, address, phone, socials, and the online bill pay link.

**Content rules:** reuse their real photos and reviews where the scrape allows; no fabricated testimonials, stock-photo padding, or invented copy about the practice. Where real content is thin, the page design accommodates it rather than faking it.

## Deployment & verification

- GitHub Actions workflow builds Astro and deploys to GitHub Pages on push to `main`.
- Live URL: `https://deliciousllc.github.io/cfd-website/` — Astro `base` configured for the `/cfd-website` subpath; all internal links and asset paths must respect it.
- **Verification discipline:** before any push, preview locally in the browser at mobile and desktop widths and look at the rendered result. No fix is declared working from build output alone.

## Out of scope

Blog, awareness/content family, booking-system integration, the long tail of individual service pages, custom domain, analytics. All are natural follow-ons if the pitch lands.

## Build order

1. Phase 1 evidence gathering (scrapes, screenshots, computed styles, logo).
2. Phase 1 brand files (visual → voice → products → handoffs → `_START_HERE.md` → root `CLAUDE.md`).
3. User gut-checks the `[PROPOSED]`/`[INFERRED]` items in the decisions files.
4. Phase 2 Astro scaffold + pages, built against the brand files.
5. Pages deploy + browser verification.

---

## Review Log

| Date | Reviewer | Outcome |
|---|---|---|
| 2026-07-22 | Josh + Claude (Fable 5), design session | Design approved (scope B, lean brand subset, Astro + public GitHub Pages) |
| — | Codex (external) | Pending — required before implementation planning |
