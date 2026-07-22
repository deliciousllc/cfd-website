# Accessibility & Verification Audit — Task 13 (2026-07-22)

Controller-run full-site pass over all three built pages. No defects found; no code changes required.

## Contrast (WCAG AA)
Every text/background pair actually in use passes AA (computed from WCAG 2.1 relative luminance):
- On white surface: ink 14.26, ink-muted 5.49, green 6.07, green-deep 7.56, sage-text 5.02 — all PASS.
- On paper (#F2F4EE) sections: ink 12.86, ink-muted 4.96, green 5.48, green-deep 6.82 — all PASS.
- White on green Call button: 6.07 — PASS.
- Decorative colors (sage 2.18, stone 2.19) are NEVER used as text (grep-verified) — correctly decorative-only.

## Structure
- Exactly one `<h1>` per page; no skipped heading levels (index/services/about all verified).
- All four landmarks (`header`/`nav`/`main#main`/`footer`) present on every page. Services has a second legitimate `<nav>` (in-page jump nav).
- All 16 images carry alt text; zero missing.

## Keyboard / focus
- Skip-to-content link is first focusable element, targets `#main`; on focus it animates from `top:-100%` to `top:16px` (on-screen) — verified with transition disabled (rectTop=16, onScreen=true). The `transition: top .15s` means a synchronous read immediately after focus shows the start value; this is cosmetic, not a defect.
- `:focus-visible` = 2px solid green outline (6.07:1 on white), offset 2px — present globally.

## Responsive / zoom
- No horizontal page overflow at 320, 375, 640, 720, or desktop widths (scrollWidth == clientWidth at each). 200%-zoom reflow is covered by the narrow-width passes (zoom halves the effective viewport).
- Financing table on Services scrolls inside its own `overflow-x` container; page body never scrolls horizontally.

## Links
- All internal links base-path-aware (`/cfd-website/...`); zero bare `/` links in built HTML.
- 24 `tel:` links, all `tel:360-568-6017`.
- Skip link on all three pages targets `#main`.
- External links (bill-pay bestcardteam, Willo, Cherry, CareCredit, Instagram, Facebook, Google Maps) all resolve to expected targets matching products.md.

## Accepted minor (for final review)
- Home page uses 700/900px breakpoints for hero/cards while shell nav + services/about use 768px. Verified to cause no overflow or visual defect across the width sweep; left as-is to avoid regressing verified-good layouts.
