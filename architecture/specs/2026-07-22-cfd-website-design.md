# CFD Website — Redesign Pitch Design

**Date:** 2026-07-22
**Status:** Implemented — live at https://deliciousllc.github.io/cfd-website/ (deployed 2026-07-22). Facts re-verified against the source site on deploy day: no drift.
**Project:** `cfd-website` — spec-work redesign pitch for Centennial Family Dentistry (Snohomish, WA)

---

## Problem & purpose

Centennial Family Dentistry's current site (https://www.cfdentistrysnohomish.com/, Wix) has a flat navigation of ~20 items (including leftover slugs like `blank-page` and `copy-of-fillings-and-crowns-2`), no hero or call-to-action, stock photography mixed with real photos, and content organized as a wall of links. The practice has real strengths the site buries: three named doctors, unusual pricing transparency, and differentiating services (laser dentistry, 3D printing, Botox, sleep apnea, Kids' Days).

This project builds a redesign pitch — "here's what you could have" — not a commissioned rebuild. The audience is the practice owners; the goal is to make the improvement obvious enough to win the work.

## Success criteria

1. A live, shareable URL showing a modern, mobile-first 3-page site built from the practice's own real content.
2. Navigation reduced from ~20 flat items to ~4, with a defensible information architecture.
3. Every fact on the pitch site (prices, hours, names, address, phone) traces verbatim to the current site — nothing improvised — and every fact in `products.md` carries its source URL and capture date so staleness is auditable.
4. A lean brand MD system in the repo that lets any future session work on this brand without re-explaining it.
5. The site meets the accessibility contract in Deployment & verification (keyboard, contrast, alt text, zoom) — dental patients skew older; this is not optional polish.

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
- Archive all raw scrapes and screenshots in `brand/_sources/` with capture dates — dated and immutable (research-snapshot rule). Every fact in `products.md` cites its source page URL and capture date, so any fact can be re-verified against the live site before the pitch is shown.
- Produce a **complete service inventory map**: every service/page in the current site's navigation, mapped to exactly one destination section on the new site (or explicitly marked omitted, with reason). No ad-hoc grouping decisions during page construction.

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

**Primary CTA — resolved:** the one conversion action everywhere is **Call** (`tel:` link to 360-568-6017). No appointment-request form — booking workflows are out of scope, and the practice's current conversion path is the phone. Hero, nav, and footer all use the same call CTA.

- **Home** — hero with practice identity and the primary call CTA, services overview, meet-the-doctors teaser, reviews strip, hours/location/contact block.
- **Services & Pricing** — the ~14 scattered service links consolidated into organized groups: routine care, restorative, cosmetic, sleep/TMJ, and extras (3D printing, Kids' Days, Willo). Pricing transparency kept front and center — a genuine differentiator for a dental practice. Financing folded in as a section on this page.
- **About** — the three doctors (Dr. Eve Rutherford DDS, Dr. Rachel Greene DDS, Dr. Samiksha Gulrajani DMD), practice story, the building, socials.

**Nav:** ~4 items (Home, Services & Pricing, About, and the call CTA). Footer on all pages carries hours, address, phone, socials, and the online bill pay link. Mobile navigation behavior (whether four items fit inline or need a disclosure, active-page treatment, keyboard/focus handling) is specified in the implementation plan before construction — not improvised mid-build. With only four items, the default posture is the simplest presentation that fits without a hamburger.

**Content rules:** reuse their real photos and reviews where the scrape allows; no fabricated testimonials, stock-photo padding, or invented copy about the practice. Where real content is thin, the page design accommodates it rather than faking it.

## Deployment & verification

- GitHub Actions workflow builds Astro and deploys to GitHub Pages on push to `main`.
- **Pages prerequisites (one-time setup, part of the deploy task):** repo Settings → Pages → Source set to "GitHub Actions"; workflow granted `pages: write` + `id-token: write` permissions with the standard `actions/deploy-pages` environment. The deploy task is not done until the live URL renders.
- Live URL: `https://deliciousllc.github.io/cfd-website/` — Astro `base` configured for the `/cfd-website` subpath; all internal links and asset paths must respect it.
- **Verification discipline:** before any push, preview locally in the browser at mobile and desktop widths and look at the rendered result. No fix is declared working from build output alone.
- **Accessibility contract (testable, checked before the pitch is shown):**
  - All text meets WCAG AA contrast against its background.
  - Every image has meaningful alt text (or empty alt if decorative).
  - Semantic landmarks and heading hierarchy (one `h1` per page, no skipped levels).
  - Full keyboard navigation with visible focus states; skip-to-content link.
  - Usable at 200% browser zoom without horizontal scrolling or clipped content.

## Out of scope

Blog, awareness/content family, booking-system integration, the long tail of individual service pages, custom domain, analytics. All are natural follow-ons if the pitch lands.

## Build order

0. **Gate: external review complete and adjudicated.** No step below starts until the Codex review's findings are resolved or explicitly accepted in the Review Log, and the implementation plan is written and reviewed.
1. Phase 1 evidence gathering (scrapes, screenshots, computed styles, logo, service inventory map).
2. Phase 1 brand files (products → visual → voice, each family's decisions + handoff bundled with its driver → `_START_HERE.md` → root `CLAUDE.md`). *Amended 2026-07-22 during plan review: products.md comes first because voice/visual examples cite its facts; bundling keeps each family's task self-contained.*
3. User gut-checks the `[PROPOSED]`/`[INFERRED]` items in the decisions files. **Scope of this check:** plausibility and presentation only — the user is not the validator of brand inferences. `[INFERRED]` items remain tagged hypotheses in the brand files even after this check; the practice owners are the only party who can ratify them, which happens (if ever) at or after the pitch.
4. Phase 2 Astro scaffold + pages, built against the brand files.
5. Pages deploy + browser verification (including the accessibility contract).

---

## Review Log

| Date | Reviewer | Outcome |
|---|---|---|
| 2026-07-22 | Josh + Claude (Fable 5), design session | Design approved (scope B, lean brand subset, Astro + public GitHub Pages) |
| 2026-07-22 | Codex (external) | Spec review: 12 P1 findings. 8 resolved in spec (see below); 4 escalated to owner for decision |
| 2026-07-22 | Codex (external) | Plan review (`architecture/plans/2026-07-22-cfd-website-implementation.md`): 12 findings (5 P1, 6 P2, 1 P3), all accepted and fixed in the plan; one spec amendment (brand-file build order: products first, families bundled) |

## Review findings — resolved in spec (2026-07-22)

- **Primary appointment CTA remains unresolved** (design-lens + coherence + scope-guardian, conf 100) → **Resolved:** primary CTA is Call (`tel:`) everywhere; no form. See "Primary CTA — resolved" in Phase 2.
- **Fact provenance cannot detect staleness** (adversarial + feasibility, conf 100) → **Resolved:** raw scrapes/screenshots archived dated in `brand/_sources/`; every `products.md` fact cites source URL + capture date; re-verify against live site before the pitch is shown. See Evidence gathering + success criterion 3.
- **External review gate missing from build order** (coherence, conf 100) → **Resolved:** Build order step 0 gates all work on review adjudication + a reviewed implementation plan.
- **Brand hypotheses use the wrong validator** (adversarial, conf 75) → **Resolved:** Build order step 3 now scopes the user's check to plausibility/presentation; `[INFERRED]` items stay tagged as hypotheses until the practice ratifies them.
- **Mobile navigation behavior is unspecified** (design-lens, conf 75) → **Resolved:** mobile nav behavior must be specified in the implementation plan before construction; default posture is no-hamburger with 4 items. See Nav.
- **Service grouping lacks a complete content map** (design-lens, conf 75) → **Resolved:** evidence gathering now produces a complete source-inventory → destination map; every source item mapped or explicitly omitted with reason.
- **Pages deployment prerequisites are unspecified** (feasibility, conf 75) → **Resolved:** one-time Pages setup (Actions source, `pages: write` + `id-token: write`) is part of the deploy task; task not done until the live URL renders.
- **Accessibility has no implementation contract** (design-lens, conf 75) → **Resolved:** testable accessibility contract added to Deployment & verification; promoted to success criterion 5.

## Review findings — escalated and decided by owner (2026-07-22)

All four escalated findings were decided by the owner on 2026-07-22:

1. **Public launch risk** → **Keep public as decided.** Risk accepted with the asset-republication angle on the table: discoverability is negligible and the assets are already public on the practice's own site. Re-open if the practice objects.
2. **Brand system weight** → **Keep the lean 8-file build.** The extraction evidence is needed for the site anyway, and the brand system doubles as proof-of-process in the pitch.
3. **Owner needs unvalidated** → **Accepted as a known risk.** Inherent to unsolicited spec work; the site is the conversation starter.
4. **Sales outcome missing from criteria** → **Deferred until the site exists.** Pitch collateral (e.g., before/after comparison) is a possible follow-on, decided after there's something to compare.

### Original findings (for the record)

- **Public launch may undermine prospect trust** — Repo & project structure (P1, product-lens + adversarial, confidence 100)

  Publishing an unsolicited redesign with copied practice assets in a public repository and site could make the prospect feel exposed or trigger an ownership complaint before the pitch reaches the owners. Public availability is not required for a shareable pitch, and technical access to photos, reviews, and branding does not establish permission to republish them.

  *Status: escalated — the "public" decision was made before the asset-republication angle was raised; owner to re-decide with this information.*

- **Brand system outweighs the pitch scope** — Phase 1 — Brand extraction (P1, scope-guardian + product-lens, confidence 100)

  Completing eight interdependent brand artifacts before producing the three-page pitch makes internal documentation a disproportionate part of the pre-commitment effort. This delays the buyer-visible artifact and increases sunk cost before there is evidence that the practice wants the work.

  *Status: escalated — conflicts with the owner's explicit direction to build the brand system first; owner to confirm or trim.*

- **Owner needs remain unvalidated** — Problem & purpose (P1, product-lens, confidence 75)

  The pitch can be polished yet irrelevant if the practice owners do not share the document's diagnosis of their highest-priority website problems. Because this is an uncommissioned proposal, the assumptions about what will persuade them remain untested hypotheses.

  *Status: escalated — inherent to unsolicited spec work; owner to accept as a known risk or address outside this repo.*

- **Success criteria omit the sales outcome** — Success criteria (P1, product-lens, confidence 75)

  The project can satisfy every listed success criterion without advancing toward a commissioned engagement. A live site proves execution, but the document does not require a buyer-facing comparison, a decision moment, or an explicit next step connecting the artifact to winning the work.

  *Status: escalated — the sales motion is the owner's, outside repo scope; owner to decide whether any pitch collateral (e.g., before/after comparison) joins the scope.*
