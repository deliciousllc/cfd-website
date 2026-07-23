# Visual handoff — Centennial Family Dentistry

**Revision:** 1 · **Last updated:** 2026-07-22

Session starter for anything that touches how the pitch site looks. Two modes —
pick one before you start.

- **Working WITH** — building or styling pages using the established tokens.
- **Working ON** — changing the tokens or the design rules themselves.

---

## Working WITH (producing — pages, components, CSS)

### Load order

1. `brand/visual.md` — the tokens. This is the whole design system.
2. `brand/products.md` — **any** practice fact that appears on screen (names,
   prices, hours, address, phone, quotes), including its "Locked Terminology &
   Fact Gotchas" section at the top. Read the gotchas; several are traps.
3. `brand/voice_handoff.md` — only if you are also writing copy.

Do **not** load `visual_decisions.md` in a production session. It is a
diagnostic file; loading it spends context on debate you are not having.

### Rules that survive if nothing else is loaded

1. Token values are exact — copy the hex, size and stack character for character; never approximate, round, or "improve" one.
2. Every text/background pair meets WCAG AA (4.5:1 normal, 3:1 large) — compute it, don't estimate it.
3. Real practice photos only; no stock, and strip EXIF from anything that ships.
4. Mobile-first: build narrow, then widen; 44px minimum tap targets; usable at 200% zoom.
5. Every practice fact comes from `products.md` verbatim — if it isn't there, ask; never fill from general knowledge.
6. One primary action per page — the call CTA — and nothing competes with it visually.

### Pre-delivery QA gate (run before calling any page done)

1. **Token pass** — every color, size, space, radius and shadow in the diff
   resolves to a token from `visual.md`. Grep the diff for raw hex values and
   raw px outside the token definitions; each hit is either a token or a bug.
2. **Contrast pass** — list every text/background pair the page actually renders
   (including text on tinted surfaces and any text over an image) and compute
   the ratio. A pair whose ratio you did not compute is not passing. New pairs
   not already in `visual.md`'s contrast ledger get added there.
3. **Render pass** — **look at it.** Open it in a browser at a phone width and a
   desktop width and read the rendered result. Build output, a passing lint, and
   a clean diff are not evidence that a page looks right. Check that fonts
   actually loaded (a fallback silently rendering is a common miss), that
   nothing overflows horizontally, and that focus is visible when you tab.
4. **Fact pass** — every on-screen fact traces to a `products.md` line, and no
   gotcha is violated (especially: no star ratings, no "13 reviews", no picking
   a winner between contradicted prices).
5. **Alt pass** — every image has meaningful alt text or an explicit empty alt.

Report the gate's result with the work, one line per pass.

---

## Working ON (improving — changing tokens or design rules)

### Load order

1. `brand/visual.md`
2. `brand/visual_decisions.md` — including the open register at the bottom
3. `brand/_sources/2026-07-22/` — the evidence, if the change claims to be
   evidence-based. This folder is **immutable**: read it, never edit it. A new
   capture goes in a new dated folder.

### How to change a token

1. **Name the invariant first.** Which rule in `visual_decisions.md` does this
   change serve? If none does, you are changing taste, not design — label it
   `[PREFERENCE]` and say so.
2. **Change the value in `visual.md`**, keeping its status tag honest. A value
   the practice has not ratified stays `[PROPOSED]` no matter how confident you
   are, and no matter how many people internally like it.
3. **Recompute contrast** for every pair the changed color participates in, and
   update the contrast ledger. Changing one color usually moves several rows.
4. **Bump the revision number** at the top of `visual.md` and stamp the date.
5. **Log it in `visual_decisions.md`** — the invariant, not the value. Apply the
   deletion test: if your recorded reason names a hex, a font, or a pixel value,
   it belongs back in `visual.md`.
6. **Ripple-check.** Grep `site/src/` for the old value in case it was inlined
   somewhere instead of tokenized, and re-run the pre-delivery QA gate on at
   least one page that uses it. Then update this file's State of play.

### Rules about the rules

- Inferences never self-promote. `[PROPOSED]` becomes `[RATIFIED]` only when the
  practice says so — not when the project lead approves it, and not when it has
  survived a few sessions.
- Corrections become rules the same session they happen, at their point of use.
- Never rename a token without sweeping the whole repo for it.
- If this file passes ~150 lines, compress rather than append.

---

## State of play (one paragraph — as of 2026-07-22)

The visual family exists at revision 1, extracted from the 2026-07-22 capture of
the live Wix site — logo samples, corrected computed styles, desktop and mobile
screenshots, the building photo, fourteen staff portraits, and the practice's
own review-card images. The palette, type scale, spacing scale, single radius
and single shadow are all specified in `visual.md`, and every text/background
pair in the system has a computed WCAG ratio recorded beside it; all specified
pairs pass AA, and the three colors that cannot carry text are labelled with
what they may and may not do instead. Typography is two self-hosted open
families with no external font request, one of which is the practice's own
existing face. Nothing here has been seen by the practice: every value derived
by inference is tagged `[PROPOSED]` in `visual.md` and logged with its basis and
risk in `visual_decisions.md`, and the nine inferred claims plus a six-item open
register are what the project lead's checkpoint (Task 7) should be pointed at —
in particular whether the review cards are the practice's own commission, which
is the strongest single piece of evidence behind the serif direction and the
cheapest to confirm. Next consumer is Task 9, which copies these token values
verbatim into `site/src/styles/global.css`; nothing in the site has been built
against them yet, so no ripple-check has been exercised.

**Last shipped (2026-07-22):** cfd-website 3-page pitch built and deployed live at https://deliciousllc.github.io/cfd-website/ — brand system drove the Astro site; all tasks reviewed; final whole-branch review clean; facts re-verified against source (no drift).
