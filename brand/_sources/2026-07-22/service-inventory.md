# Service Inventory Map — Task 2

Authoritative source-page → destination-section map for the Centennial Family
Dentistry redesign pitch. This is the single source of truth for navigation
restructuring; Tasks 10–12 build pages against the group names and anchor IDs
below **verbatim**. Do not rename, re-slug, or add groups downstream of this
file — if a naming problem is found later, fix it here first.

Source site: https://www.cfdentistrysnohomish.com/

## Step 1: Nav enumeration — link dump vs. rendered nav

**Source A — `home.json` link dump** (markdown nav list + `links` array,
captured 2026-07-22): 21 nav entries (Home, About Us, Services and Pricing,
Financing, Blog, Reviews, Call Us, Sleep apnea, Botox and Fillers, Routine
Cleanings and Exams, Fillings and Crowns, Cosmetic Dentistry, 3D Printing,
Botox, Willo, TMJ, Kids' Days, Sleep Apnea, Invisalign, Laser Dentistry,
Teeth Whitening), plus non-nav incidental links in the page body/footer
(Instagram, Facebook, the "Pay Here" bill-pay link, and a `mailto:` link) and
one `tel:` link inside the nav itself (Call Us).

**Source B — rendered nav, live browser** (2026-07-22): the visible header
only shows **Home**, **More**, and the phone number — everything else is
collapsed behind the "More" dropdown (confirmed via `preview_start` +
`read_page`/`computer` against `https://www.cfdentistrysnohomish.com/`).
Clicking "More" and re-reading the DOM (`read_page filter:all`, then
`filter:interactive` with the menu open) surfaced the full item list.

**Cross-check result: no discrepancy.** The rendered "More" dropdown exposed
exactly the same 21 nav entries, in the same order, with the same hrefs, as
the `home.json` link dump — no additional client-rendered items, no extra
items hidden past what was already in the dump. The dump's non-nav
extras (Instagram, Facebook, Pay Here, mailto) are confirmed to live outside
the `nav`/"Site" navigation list in the DOM (social icons in the banner, and
an inline body link respectively) — correctly excluded from the nav
inventory, not a miss.

One structural note: the `copy-of-fillings-and-crowns-*` slug family in the
nav has entries `-1`, `-2`, `-4` (and the unsuffixed original) but no `-3` —
a Wix page-duplication artifact (a duplicated page that was presumably
deleted or never linked). No nav item points to `-3`, so it is out of scope
for this inventory; noted here only as an explanation for the numbering gap,
not as evidence of a missed source item.

**Union inventory: 21 nav items** (matches the brief's "~20"). Table below.

## Step 2: Inventory → destination map

Locked group names/anchors (Services & Pricing page, per spec):

| Group name | Anchor ID |
|---|---|
| Routine care | `#routine-care` |
| Restorative | `#restorative` |
| Cosmetic | `#cosmetic` |
| Sleep & TMJ | `#sleep-tmj` |
| Technology & extras | `#technology-extras` |
| Financing | `#financing` |

| # | Source item (nav label) | Source URL | Destination | Notes |
|---|---|---|---|---|
| 1 | Home | `/` | Home page | Direct 1:1. |
| 2 | About Us | `/about-us` | About page | Direct. |
| 3 | Services and Pricing | `/services-and-pricing` | Services & Pricing page (hub) | Top-level nav item; parent page containing the six anchor groups below. |
| 4 | Financing | `/financing` | Services & Pricing → **Financing** `#financing` | Page content becomes this group's body. |
| 5 | Blog | `/blog` | **Omitted** | Out of scope per spec. Not scraped (nothing to capture for an out-of-scope item). |
| 6 | Reviews | `/about-me` | About page (reviews section); excerpt also stays on Home | Matches spec: "About Us + Reviews → About page (reviews also excerpted on Home)." |
| 7 | Call Us | `tel:360-568-6017` | Global header/contact utility action, all pages | Not a content page — a click-to-call action. Carried forward as a persistent header/contact CTA on the new site rather than a mapped destination page. |
| 8 | Sleep apnea | `/blank-page` | Services & Pricing → **Sleep & TMJ** `#sleep-tmj` → Sleep Apnea | Junk slug (`blank-page`) but real, distinct content (in-office screening protocol, no pricing). Merges with #18 per spec ("Sleep Apnea ×2, merged") but see concern below — content is NOT a literal duplicate. |
| 9 | Botox and Fillers | `/blank-page-1` | Services & Pricing → **Cosmetic** `#cosmetic` → Botox | Junk slug (`blank-page-1`). Merges with #14 per spec ("Botox and Fillers/Botox merge the two Botox entries") — see concern below, content differs (no pricing here vs. priced on #14). |
| 10 | Routine Cleanings and Exams | `/routine-cleanings-and-exams` | Services & Pricing → **Routine care** `#routine-care` | Scraped in Task 1. |
| 11 | Fillings and Crowns | `/fillings-and-crowns` | Services & Pricing → **Restorative** `#restorative` | Newly scraped this task. |
| 12 | Cosmetic Dentistry | `/cosmetic-dentistry` | Services & Pricing → **Cosmetic** `#cosmetic` | Newly scraped this task. |
| 13 | 3D Printing | `/3d-printing` | Services & Pricing → **Technology & extras** `#technology-extras` | Scraped in Task 1. |
| 14 | Botox | `/botox` | Services & Pricing → **Cosmetic** `#cosmetic` → Botox | Newly scraped. Merges with #9 (see concern below). H1 on this page is itself "Botox and Fillers," same as #9's page. |
| 15 | Willo | `/willo` | Services & Pricing → **Technology & extras** `#technology-extras` | Newly scraped, as "Willo Toothbrush" per spec member list. |
| 16 | TMJ | `/copy-of-fillings-and-crowns` | Services & Pricing → **Sleep & TMJ** `#sleep-tmj` → TMJ | Junk slug, real distinct content. Newly scraped. Not a duplicate of anything — its own subsection within the group. |
| 17 | Kids' Days | `/kidsdays` | Services & Pricing → **Technology & extras** `#technology-extras` | Newly scraped. |
| 18 | Sleep Apnea | `/copy-of-fillings-and-crowns-1` | Services & Pricing → **Sleep & TMJ** `#sleep-tmj` → Sleep Apnea | Junk slug, real distinct content (pricing: Home Sleep Test $250, Oral Sleep Device $2,500). Merges with #8 (see concern below). Newly scraped. |
| 19 | Invisalign | `/copy-of-fillings-and-crowns-2` | Services & Pricing → **Cosmetic** `#cosmetic` | Junk slug, real distinct content. Newly scraped. |
| 20 | Laser Dentistry | `/laser` | Services & Pricing → **Technology & extras** `#technology-extras` | Scraped in Task 1. |
| 21 | Teeth Whitening | `/copy-of-fillings-and-crowns-4` | Services & Pricing → **Cosmetic** `#cosmetic` | Junk slug, real distinct content. Newly scraped (page H1 reads "Whitening"). |

**Non-nav incidental items** (from the link dump / page body, not nav
entries — recorded for completeness per the brief's "note any discrepancy"
instruction, disposition: omitted as non-content utility links, not pages):

| Item | URL | Disposition |
|---|---|---|
| Instagram icon | `https://www.instagram.com/cfdentistrysnoho/` | Omitted — social icon link, carried forward as a footer/header social icon on the new site, not a mapped content page. |
| Facebook icon | `https://www.facebook.com/CFDsnohomish/` | Omitted — same as above. |
| Pay Here | `https://bestcardteam.com/Payments/?Profile=centennialfamPAY` | Omitted — third-party bill-pay redirect, not practice content; carried forward as a utility link/button if the redesign keeps online bill pay, not a mapped page. |
| Send us your resume! (mailto) | `mailto:info@cfdentistrysnohomish.com` | Omitted — a mailto action embedded in the Home page's "Employment Opportunities" section, not a nav item or distinct page. |

**Total: 21 nav items — 19 mapped to a destination, 1 omitted with reason
(Blog), 1 mapped to a non-page utility destination (Call Us). Every item
appears exactly once above.** (4 additional non-nav incidental links also
accounted for, omitted with reason, per the brief's completeness requirement.)

## Step 3: Newly scraped pages (this task)

Compared against `brand/_sources/2026-07-22/` as it stood at the start of
this task (see `capture-log.md`'s existing table: about-us, services-and-pricing,
financing, reviews, reviews-rendered, routine-cleanings-and-exams, laser,
3d-printing, home.json were already captured in Task 1). The remaining 11
mapped pages had no scrape and were captured now:

| File | Source URL | Nav label | Result |
|---|---|---|---|
| fillings-and-crowns.md | `/fillings-and-crowns` | Fillings and Crowns | OK — real content, pricing present (Fillings $212–416, Crowns $1,828). |
| cosmetic-dentistry.md | `/cosmetic-dentistry` | Cosmetic Dentistry | OK — real content, pricing present (Fillings $212–416, Whitening $90–600, Invisalign $3,000–5,400), plus one embedded patient testimonial. |
| botox.md | `/botox` | Botox | OK — real content, pricing present (Botox $14/unit, Filler $650/syringe). |
| blank-page-1.md | `/blank-page-1` | Botox and Fillers | OK — real content, no pricing on this page (see merge concern below). |
| willo.md | `/willo` | Willo | OK — real content, no pricing (links out to `partners.willo.com/CFDSNOHOMISH`). |
| copy-of-fillings-and-crowns.md | `/copy-of-fillings-and-crowns` | TMJ | OK — real content, pricing present (CBCT $550, Orthotic $1,268, Botox $13/unit — note: differs from the $14/unit price on `/botox`, see concern below). |
| kidsdays.md | `/kidsdays` | Kids' Days | OK — real content; gallery image `alt`/`src` attributes resolved to the page's own URL rather than image asset URLs (a scrape/lazy-load artifact), body text unaffected. |
| blank-page.md | `/blank-page` | Sleep apnea | OK — real content, no pricing on this page (see merge concern below). |
| copy-of-fillings-and-crowns-1.md | `/copy-of-fillings-and-crowns-1` | Sleep Apnea | OK — real content, pricing present (Home Sleep Test $250, Oral Sleep Device $2,500). |
| copy-of-fillings-and-crowns-2.md | `/copy-of-fillings-and-crowns-2` | Invisalign | OK — real content, pricing present (Invisalign $5,400 — differs from the $3,000–5,400 range quoted on `/cosmetic-dentistry`, see concern below). |
| copy-of-fillings-and-crowns-4.md | `/copy-of-fillings-and-crowns-4` | Teeth Whitening | OK — real content, pricing present (Zoom $600, Take-Home Syringes $45/2-pack, Custom Trays $350, Go Trays $90/10-pack). |

No page 404'd or scraped empty. All 11 newly requested captures returned
real page content, confirmed by manual read-through.

## Dead / empty pages found

None. Every mapped URL (19 pages) returned real, non-empty content across
Task 1 + Task 2 scrapes. The two junk-slug pages under "More" (`blank-page`,
`blank-page-1`) are junk *slugs* (Wix's auto-generated default page names),
not dead pages — both render real practice content, just under an
un-renamed URL. This is itself evidence of the IA problem the pitch fixes:
the practice never renamed these pages after creating them, so the nav
carries meaningless URLs for real content.

## Concerns for later tasks

1. **The four "merge the duplicate" pairs are NOT literal duplicates —
   they contain different, non-overlapping facts, including different
   prices.** The spec's grouping table describes two merges: "Sleep Apnea
   (×2, merged)" and "Botox and Fillers/Botox (merge the two Botox
   entries)." Reading both pairs of scrapes side by side:
   - **Sleep Apnea**: `/blank-page` describes the in-office screening
     process (small-airway checks during exams, at-home sleep study
     referral) with **no pricing**. `/copy-of-fillings-and-crowns-1`
     describes the same service from a patient-facing marketing angle
     **with pricing** (Home Sleep Test $250, Oral Sleep Device $2,500).
     Merging these into one Sleep & TMJ subsection must union both sets of
     facts — using only one source page would silently drop either the
     screening-process description or the pricing.
   - **Botox**: `/blank-page-1` ("Botox and Fillers") is a short paragraph
     with **no pricing**. `/botox` (also titled "Botox and Fillers" as its
     on-page H1, despite the nav label being just "Botox") has fuller
     marketing copy **with pricing** (Botox $14/unit, Filler $650/syringe).
     Same union requirement applies.
   Task 3 (fact extraction) should treat each "merged" pair as **two source
   documents to reconcile**, not one canonical page with a redundant
   duplicate to discard.

2. **Conflicting Botox unit price across pages.** `/botox` states Botox at
   **$14 per unit**; `/copy-of-fillings-and-crowns` (TMJ page, which also
   offers "Botox for muscle related TMJ issues") states Botox at **$13 per
   unit**. This is a real inconsistency on the live site, not a capture
   error — both values are verbatim from their respective pages. Task 3
   should record both and flag the discrepancy rather than silently picking
   one; it may be relevant to the pitch's "your data is inconsistent
   across pages" narrative.

3. **Conflicting Invisalign price.** `/cosmetic-dentistry` quotes Invisalign
   as **$3,000–5,400** (a range, alongside other cosmetic services);
   `/copy-of-fillings-and-crowns-2` (the dedicated Invisalign page) quotes
   a single **$5,400**. Same treatment as above — both are real, verbatim,
   and should be reconciled/flagged in Task 3, not silently collapsed.

4. **Kids' Days image references did not resolve to real asset URLs** —
   `kidsdays.md`'s gallery images show `src`/`alt` values pointing back to
   the page's own URL rather than to `static.wixstatic.com` asset paths
   (likely a lazy-loaded Wix gallery Firecrawl's markdown conversion
   couldn't resolve without JS execution). The body text is complete and
   unaffected. If Kids' Days imagery is wanted for the redesign, it may
   need a browser-based re-capture (same method used for the mobile
   screenshots in Task 1) rather than relying on this scrape's image links.

5. **"Call Us" has no natural page destination.** It is mapped above to a
   global header/contact utility rather than any of the six anchor groups
   or About/Home — flagging this now so Tasks 10–11 don't go looking for a
   "Call Us" section under Services & Pricing that was never meant to
   exist there.

6. **EXIF/GPS concern from Task 1 still applies** and is unaffected by this
   task's scrapes (text-only captures, no new images downloaded here).
