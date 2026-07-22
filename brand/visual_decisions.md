# Visual decisions — Centennial Family Dentistry

**Revision:** 1 · **Last updated:** 2026-07-22 · Covers `visual.md` revision 1.

---

## What this file is

The **why** layer behind `visual.md`. It is a diagnostic file, not a production
file — load it when reconsidering the design itself, never when building a page.
Building a page needs `visual.md` and `products.md`; loading this one just
crowds the context.

### Portability discipline

Every rule is held at two levels:

- the **invariant** — the durable reason, which survives a re-skin, a palette
  change, a font swap, or a move to a different platform. It lives here.
- the **expression** — the current value that implements it. It lives in
  `visual.md`'s token tables.

**Deletion test:** if a stated reason names a specific hex, font name, or pixel
value, it is an expression, not an invariant — move it to `visual.md`. Nothing
below should survive that test with a value still in it.

The point: if the practice hates the green, we change one row of a token table
and every invariant here still holds.

### Status tags

- `[RATIFIED]` — confirmed deliberate by the party who can confirm it.
- `[PROPOSED]` — an analytical read awaiting confirmation. **Everything derived
  by inference from the captures is here, and stays here.** The project lead's
  gut-check at the Task 7 checkpoint tests plausibility and presentation only;
  it does not promote anything to `[RATIFIED]`. Only the practice can do that,
  and only by saying so.
- `[PREFERENCE]` — taste, honestly labelled as taste, with no strategic claim
  behind it.
- `[CONSTRUCTION]` — emerged from building the thing, with no strategic intent.
  Free to change; nobody chose it.

---

## Why this aesthetic at all

This is a redesign pitch for a practice that already has an identity and is
being let down by the platform carrying it. So the design brief is not "make a
dental website" — it is **give them back the identity their logo, their
building, and their own review cards already state, at a fidelity the current
site cannot reach.** Three independent artifacts they control (the logo, the
building they chose and painted, the quote cards they had made) agree with each
other on register: Pacific-Northwest evergreen, quiet, warm, crisp-edged,
generous with white space, serif where it matters. Three artifacts they do *not*
control (the template's type scale, the flat twenty-item navigation, the mixed
stock photography) disagree with all three. The pitch wins on the argument that
we removed the disagreement — which only works if every design move can be
traced back to something the practice already owns. Nothing here may be
invented to look modern.

---

## Design invariants

### The palette is extracted, never designed

1. **The brand's colors come from the logo and are ratified by the practice's
   own usage elsewhere.** A color earns a place in the system by appearing in
   more than one artifact the practice controls. `[PROPOSED]`
2. **The action color and the brand color are the same color.** The practice
   already made this choice; the redesign does not introduce a separate
   "call-to-action" hue on top of it. `[PROPOSED]`
3. **The darkest brand color is the text color.** Text is not neutral black —
   it is the same dark the logo already uses, so type and mark sit in one
   family. `[PROPOSED]`
4. **There is no cool/clinical color in this brand and none may be added.** The
   entire evidence base is warm — greens, plum, off-whites, tans. The reflex to
   add a medical blue would be importing a category cliché the practice never
   asked for. `[PROPOSED]`
5. **Palette breadth is capped at what three pages need.** Surface, alternate
   surface, text, muted text, brand, brand-dark, one decorative accent, one
   hairline. A ninth color is a sign a layout problem is being solved with
   paint. `[PREFERENCE]`

### Accessibility is a constraint on the palette, not a filter after it

6. **A color that cannot carry text does not get to carry text — and we say so
   in the token table rather than leaving it to be rediscovered.** Each
   restricted color is labelled with what it may and may not do. `[PROPOSED]`
7. **When a brand color fails the contrast requirement, the brand hue is kept
   and an accessible sibling is derived from it for text use.** We never
   substitute a different hue, and we never quietly drop the practice's color.
   The original stays in the system for decorative work. `[PROPOSED]`
8. **Every text/background pair in the system has a computed, recorded ratio
   before it ships.** Not estimated, not eyeballed, not "looks fine" — arithmetic,
   written down next to the token. The patient base skews older; this is
   load-bearing, not polish. `[PROPOSED]`
9. **Body copy sits above the usual minimum, not at it.** The current site's
   body size is the most fixable readability problem in the evidence, and the
   audience makes the extra step worth taking. `[PROPOSED]`
10. **Boundaries that carry meaning must meet the non-text contrast requirement;
    decorative hairlines need not, and are labelled as decorative.** `[PROPOSED]`

### Typography follows the practice's taste, not the template's default

11. **The display face answers to the practice's own typographic artifacts, not
    to what the template happened to load.** Where the practice commissioned
    something typographic, that is evidence of taste; where the platform picked
    a default, that is evidence of nothing. `[PROPOSED]`
12. **A font must be open-licensed and self-hostable, or it does not ship.** The
    deploy target is a static host with no font service; a third-party font
    request is both an external dependency and a render-blocking round trip.
    Any proprietary face in the evidence is replaced by the nearest open
    equivalent, and the substitution is recorded as unconfirmed — a visual match
    made against flattened images is not an identification. `[PROPOSED]`
13. **Where the practice's existing face is already open-licensed, keep it.**
    Continuity with what they have costs nothing and buys authenticity.
    `[PROPOSED]`
14. **Two families, two roles, two weights each.** More weights is more bytes on
    a mobile connection for a benefit nobody asked for. `[PREFERENCE]`
15. **The wordmark is an image asset and is never re-typeset in a system font.**
    The logo's face is not part of this type system and must not be approximated.
    `[PROPOSED]`
16. **Type scale is a relationship, not a set of sizes.** The current site's
    heading-to-body ratio is a template artifact; the redesign's scale steps
    proportionally and stops at what three pages use. `[PROPOSED]`

### Structure is quiet and square

17. **The building sets the geometric register: crisp, rectilinear, unfussy.**
    Softening exists only to the degree a family practice needs to feel
    approachable. One radius for the whole site; a second radius is a second
    voice. `[PROPOSED]`
18. **One elevation, used once per page.** If two things on a page are both
    lifted off the surface, neither is. `[PREFERENCE]`
19. **Spacing comes from a single scale and nothing else.** An off-scale value
    is always a symptom of a layout decision that was never made. `[PREFERENCE]`
20. **White space is the practice's own device.** Their review cards are mostly
    empty. Density is not a virtue here. `[PROPOSED]`

### Imagery is theirs or it does not exist

21. **Real practice photography only. No stock, ever.** The pitch's central
    argument is that the practice's real material is better than what the
    current site does with it; a stock photo on the pitch site refutes our own
    case. `[PROPOSED]`
22. **The strongest asset the practice owns leads.** They paid for a building
    that looks considered; the site should show it. `[PROPOSED]`
23. **Photographic treatment is correction, not styling.** The photos look like
    daylight phone photos of a real office because that is what they are, and
    that honesty is an asset for a family practice. Filters would make them look
    like stock, which is the one thing they must not look like. `[PROPOSED]`
24. **People are presented at equal weight.** Same crop, same size, doctors and
    staff alike — the practice's own About page gives everyone a bio, which is a
    statement about how they see the team. `[PROPOSED]`
25. **Where the practice has no photo, the gap is shown honestly, not filled.**
    A missing portrait is a fact about the practice, not a hole to patch.
    `[PROPOSED]`
26. **Published images carry no embedded metadata.** Several source photos carry
    location data; anything that ships is re-encoded clean. Privacy requirement,
    not an optimization. `[PROPOSED]`
27. **Nothing that does not exist in the evidence may be depicted or claimed** —
    no ratings, no counts, no awards, no invented signage. `[PROPOSED]`

### One channel, one action

28. **There is exactly one channel and the system does not speculate about
    others.** Rules for print, email or social get written when those channels
    exist. `[PROPOSED]`
29. **Mobile is the design surface; desktop is the widened version of it.**
    `[PROPOSED]`
30. **One primary action, one visual treatment for it, and nothing else on the
    page competes with it.** A second equally-loud element means the page has
    two primary actions, which means it has none. `[PROPOSED]`
31. **The site is self-contained.** No CDN, no third-party embed, no external
    request at render time. `[CONSTRUCTION]` — this follows from the deploy
    target rather than from any brand intent.

---

## Inferred claims logged for gut-check

Every `[INFERRED]` claim in `visual.md` revision 1, restated here as a
hypothesis. Each is a reading of the evidence, not a fact the practice has
stated. All are `[PROPOSED]`.

| # | Claim | Basis | Risk if wrong |
|---|---|---|---|
| I1 | The current site's typography is a template default, not a brand choice. | The heading-to-body relationship is not one a designer would specify; the body face is a stock platform license. | If the practice deliberately picked it, replacing it reads as us overriding their taste — recoverable by keeping the face and fixing only the scale. |
| I2 | The building and the website disagree, and the building is right. | The building is contemporary and considered; the site is a template. | Low. Even if they love the site, the building photo is still their best asset. |
| I3 | The practice's identity is Pacific-Northwest evergreen, currently obscured by the platform. | Three artifacts they control (logo, building, review cards) agree on register; the template disagrees. | This is the whole pitch thesis. If wrong, the pitch is wrong — which is why it goes to the practice, not to us, to ratify. |
| I4 | Body copy should sit above the usual minimum size because the patient base skews older. | The practice's own reviews name senior patients and dental-anxious patients; the current body size is small. | Low. Larger body copy harms nobody. |
| I5 | Evergreen / open-sky / Snohomish daylight is the *rule* for future imagery, not a coincidence of two assets. | Two assets is a pattern of two, not a proven system. | Moderate — a future photo that breaks it would look off-brand under a rule the practice never agreed to. |
| I6 | Clinical blue/teal is off-brand and must not be introduced. | Absent from every capture. | Low; absence is strong evidence here. |
| I7 | Decorative effects (gradients, glass, ambient motion) are off-brand. | The register of every controlled artifact is quiet and flat. | Low, and cheap to revisit. |
| I8 | The specific open serif named in `visual.md` is the nearest match to the review cards' face. | Visual comparison only — the cards are flattened images with no font metadata. | Low. If the practice knows the real face and it is licensable, swap the token. |
| I9 | The reviewer-card aesthetic represents the practice's taste rather than a widget vendor's template. | Consistent across all thirteen assets, and distinct from the Wix site around it. | Moderate. If a vendor made them, the serif direction loses its strongest evidence. **Worth asking the practice directly.** |
| I10 | The review cards' text color is close to the brand green, read as `#5B694B`. | A visual read of the review-card image referenced by URL in `reviews-rendered.md`. That image was never downloaded into `_sources/` and no tool-based color sample of it exists in any evidence file — unlike the logo's greens (`#5C704A`, `#B0B471`), which are now backed by `logo-palette-resample.md`. | Low. `#5B694B` is only cited as one of two corroborating readings for `--color-green` (`#596749`), which is independently `[OBSERVED]` from `computed-styles.json` and does not depend on this claim. If the true hex differs, only the "three samples agree" narrative weakens, not the shipped token. Fixable by downloading the source image and sampling it with the same tool used for the logo. |

---

## Values classified as construction or preference

Honest section: these are in `visual.md` and are **not** strategy.

- The exact number of steps in the spacing scale — `[CONSTRUCTION]`, it is what
  three pages needed.
- The alternate-surface tint existing at all — `[CONSTRUCTION]`, sections needed
  separating without rules or boxes.
- The specific breakpoint at which section rhythm loosens — `[CONSTRUCTION]`.
- `--container: 1120px` and `--gutter` — `[CONSTRUCTION]`. Neither traces to
  any brand evidence; they exist because Task 9's page build needs a max
  content width and a gutter, and this is what three pages' content needed.
  Kept in `visual.md` because the build genuinely requires them, not because
  the evidence base implies them.
- The 44×44px minimum tap-target rule — `[CONSTRUCTION]`. It is not derived
  from the logo, the building, or any capture — it exists to satisfy the
  spec's accessibility contract (WCAG 2.5.5-style target-size guidance) for an
  older patient base. Kept for that reason, not as a brand-evidence finding.
- Capping the palette, the weights, and the elevation count — `[PREFERENCE]`
  (restraint as taste, not as evidence).
- The choice of one radius over zero radius — `[PREFERENCE]`. A zero-radius
  system would also be defensible against the same evidence.

---

## Open register — decisions without a recorded why

Carry these forward; do not let them silently become rules.

1. **Which of the three near-identical green samples is canonical.** The logo
   mark, the site's button, and the review cards each give a slightly different
   green. `visual.md` picks one on the reasoning that the site's button is the
   practice's own *applied* choice — but nobody has confirmed that hierarchy.
2. **Whether the practice commissioned the review cards.** Answers I9 and
   determines how much weight the serif direction carries. One question to the
   practice settles it.
3. **Whether the deep plum should ever appear as a color rather than only as
   text.** It is a full third of the logo mark and currently does almost no
   visible work in the system.
4. **Whether the near-black of the building should enter the palette** as a dark
   surface for a footer or hero band. Not included in revision 1 on scope
   grounds; no strategic reason to exclude it.
5. **What happens to the logo asset itself.** It is a JPEG with a white box
   around it, visibly boxed against the green hero band in the current site's
   own screenshots. Whether the pitch cleans it, re-cuts it transparent, or
   leaves it alone has not been decided, and touching a client's logo is not a
   decision to make unilaterally.
6. **Whether the practice has brand assets not published on the website**
   (print collateral, signage specs, an original logo file with real color
   values). Everything here is reverse-engineered from a live Wix site and
   compressed images. One question could replace a lot of inference.

## Owner checkpoint — 2026-07-22

Project lead reviewed the inferred-claim register (I1–I10) at the Task 7 gut-check. Direction **confirmed to build on**: the Pacific-Northwest evergreen thesis (I3) is a sound basis for the redesign — keep the practice's greens, serif display face, and building photo as anchors, replace the Wix template. Scope of this confirmation is plausibility/direction only; I1–I10 remain tagged hypotheses until the practice itself ratifies. I9 (review-card serif = practice taste vs. widget-vendor template) and the parallel voice V2 (published prices as deliberate stance) are flagged to ask the practice directly at pitch time — the pitch proceeds either way.
