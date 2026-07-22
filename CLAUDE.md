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
