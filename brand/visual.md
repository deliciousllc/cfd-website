# Visual — Centennial Family Dentistry

**Revision:** 1 · **Last updated:** 2026-07-22

The design reference for the redesign pitch site. Every value below is a token a
builder copies **verbatim** into `site/src/styles/global.css` — no approximating,
no "close enough" hexes, no substituting a font because it renders faster.

**Evidence base:** `brand/_sources/2026-07-22/` (immutable). Specifically
`computed-styles.json` (live computed styles, `reliable: true` entries only),
`capture-log.md` (ImageMagick logo samples), `logo-palette-resample.md`
(follow-up ImageMagick logo samples, added after a code-review finding that
the original narrative-only re-sample wasn't traceable), `assets/logo.jpg`,
`assets/building.jpg`, the four screenshots, and the review-card images linked
from `reviews-rendered.md`.

**Claim tags:** `[OBSERVED]` = directly evidenced in the 2026-07-22 captures ·
`[INFERRED]` = analytical read. Every `[INFERRED]` claim here is also logged in
`visual_decisions.md` as `[PROPOSED]`, awaiting gut-check. The practice is the
only party that can ratify an inference.

**Facts** (names, prices, hours, address) never come from this file — they come
from `brand/products.md` verbatim.

---

## What the evidence actually shows

Read this before the token table; the tokens only make sense against it.

- **The logo is the brand.** Three evergreens — deep plum, mid forest green,
  light sage — over a hand-drawn ridgeline, beside a classical roman-caps
  wordmark. Sampled colors: `#5C704A` (mid tree), `#B0B471` (light tree),
  `#372732` (dark tree / wordmark), `#B0B0A1` (muted gray-tan), on a near-white
  field `#EEF1EB`. `[OBSERVED]` — `#B0B0A1` is in `capture-log.md`'s "Logo
  color samples"; `#5C704A`, `#B0B471`, `#372732` and `#EEF1EB` are in
  `logo-palette-resample.md` (whole-image 12-color quantize and a region-cropped
  re-sample of the same asset, both re-run and logged 2026-07-22 after the
  original narrative-only version of this sample was flagged as unlogged).
- **The live site already uses the logo's green as its action color.** The
  homepage hero band and the "Pay Here" / "Financing Options" buttons are
  `#596749` with white labels — within a hair of the logo's mid tree.
  `[OBSERVED]` — `computed-styles.json` `button.backgroundHex`, visible in
  `home-desktop.png` and `services-desktop.png`.
- **The site's text color is the logo's dark tree.** h1, h2 and body all compute
  to `#372532`; the logo's darkest sample is `#372732`. Same color, two decimal
  places apart. `[OBSERVED]` — `#372532` from `computed-styles.json` (h1/h2/body
  all `reliable: true`); `#372732` from `logo-palette-resample.md` (whole-image
  quantize).
- **The practice's own most deliberate design artifact is a serif.** The review
  cards are 1080×1080 images: a transitional serif set in an olive green read
  as `#5B694B` on white, with oversized quote marks, centered, generously
  leaded, lots of white space. Nobody makes thirteen of those by accident —
  this is the practice's taste, expressed where Wix's template could not
  overrule it. `[OBSERVED]` (the artifact's existence, layout and serif style —
  image referenced by URL in `reviews-rendered.md`, listed in `products.md`) /
  `[INFERRED]` (the specific hex `#5B694B`, and that the aesthetic is the
  practice's taste rather than a widget vendor's template — the source image
  was never downloaded into `_sources/` or sampled with a tool, so no logged
  evidence file backs this reading; see `visual_decisions.md` I9, I10).
- **The Wix template's typography is not a brand choice.** Headings compute to
  Barlow at 72px, body to a licensed Avenir cut at 15px, nav at 14px `#6C6869`.
  72px headings over 15px body is a template default, not a designed
  relationship. `[OBSERVED]` (the values) / `[INFERRED]` (that it is template
  default, not choice).
- **The building contradicts the website.** `assets/building.jpg` is a
  near-black board-and-batten modern farmhouse with crisp square edges, a
  standing-seam awning, big windows, a mown lawn, a Douglas fir and open blue
  sky. It is a considered, contemporary building. The website is not.
  `[OBSERVED]` (the photo) / `[INFERRED]` (the mismatch).

**The extraction, in one line:** the practice's identity is Pacific-Northwest
evergreen — olive green, deep plum-black, sage, off-white, serif, crisp edges,
lots of air — and the Wix site is currently obscuring it. `[INFERRED]`

---

## Design tokens

Copy these values exactly. Where a value is `[PROPOSED]`, it is a hypothesis
with a logged reason in `visual_decisions.md` — it is still the value to use
until the practice says otherwise.

### Color

| Token | Value | Status | What it is |
|---|---|---|---|
| `--color-ink` | `#372532` | `[OBSERVED]` | Primary text. The live site's computed h1/h2/body color (`computed-styles.json`, h1/h2/body all `reliable: true`); the logo's dark tree is `#372732` (`logo-palette-resample.md`, whole-image quantize). |
| `--color-ink-muted` | `#6C6869` | `[OBSERVED]` | Secondary text (meta, captions, nav-inactive). The live site's computed nav-label color. Passes AA unmodified — no adjustment needed. |
| `--color-green` | `#596749` | `[OBSERVED]` | Brand primary / action color. The live site's CTA button background (`computed-styles.json`) is the token value itself; the logo's mid tree is `#5C704A` (`[OBSERVED]`, `logo-palette-resample.md`) and the review cards' text reads as a close olive match (`[INFERRED]`, ~`#5B694B`, never sampled to a logged file) — one color, corroborated by two further readings. |
| `--color-green-deep` | `#4C5840` | `[PROPOSED]` | Hover/active state for green surfaces, and green text where extra headroom is wanted. Same hue, darkened. |
| `--color-sage` | `#B0B471` | `[OBSERVED]` | The logo's light tree (`logo-palette-resample.md`, trees-only crop). **Decorative only** — 2.18:1 on white, fails AA for any text. Use for rules, icons-on-dark, quote marks on ink. |
| `--color-sage-text` | `#6F7338` | `[PROPOSED]` | Accessible variant of the sage hue, for the rare case sage must carry text on a light surface. Hue preserved, lightness dropped until AA passes. |
| `--color-stone` | `#B0B0A1` | `[OBSERVED]` | The logo's muted gray-tan (`capture-log.md`, "Logo color samples"). **Non-text only** — 2.19:1 on white. Photo mattes, dividers on dark. |
| `--color-border` | `#D9DCD2` | `[PROPOSED]` | Hairline rules and card edges. Lightened from stone. **Decorative boundaries only** — 1.39:1 on white; any boundary that carries meaning (focus, error, control edge) must use `--color-ink-muted` or `--color-green`. |
| `--color-paper` | `#F2F4EE` | `[PROPOSED]` | Alternating section surface. Derived from the logo's own off-white field (`#EEF1EB`, `[OBSERVED]` in `logo-palette-resample.md`), lifted slightly so text keeps headroom. |
| `--color-surface` | `#FFFFFF` | `[OBSERVED]` | Default page background. The live site's, and the review cards'. |

There is deliberately **no** blue, no teal, no clinical mint. The practice's
palette has none. `[OBSERVED]` (absence in every capture).

### Contrast ledger — every text/background pair specified

Method: WCAG 2.1 relative luminance. Each 8-bit channel → `c/255`; linearize
(`c/12.92` if `≤0.04045`, else `((c+0.055)/1.055)^2.4`); `L = 0.2126R +
0.7152G + 0.0722B`; ratio = `(L_light + 0.05) / (L_dark + 0.05)`. Computed in
Python from the hex values above, not estimated.

Thresholds: **4.5:1** normal text, **3:1** large text (≥24px, or ≥18.66px bold).

| Foreground | Background | Ratio | Needs | Verdict |
|---|---|---|---|---|
| `--color-ink` `#372532` | `--color-surface` `#FFFFFF` | **14.26:1** | 4.5 | ✅ AA + AAA |
| `--color-ink` `#372532` | `--color-paper` `#F2F4EE` | **12.86:1** | 4.5 | ✅ AA + AAA |
| `--color-ink-muted` `#6C6869` | `--color-surface` `#FFFFFF` | **5.49:1** | 4.5 | ✅ AA |
| `--color-ink-muted` `#6C6869` | `--color-paper` `#F2F4EE` | **4.96:1** | 4.5 | ✅ AA |
| `--color-green` `#596749` | `--color-surface` `#FFFFFF` | **6.07:1** | 4.5 | ✅ AA |
| `--color-green` `#596749` | `--color-paper` `#F2F4EE` | **5.48:1** | 4.5 | ✅ AA |
| `--color-green-deep` `#4C5840` | `--color-surface` `#FFFFFF` | **7.56:1** | 4.5 | ✅ AA + AAA |
| `--color-green-deep` `#4C5840` | `--color-paper` `#F2F4EE` | **6.82:1** | 4.5 | ✅ AA |
| `--color-sage-text` `#6F7338` | `--color-surface` `#FFFFFF` | **5.02:1** | 4.5 | ✅ AA |
| `--color-sage-text` `#6F7338` | `--color-paper` `#F2F4EE` | **4.53:1** | 4.5 | ✅ AA |
| `#FFFFFF` (button label) | `--color-green` `#596749` | **6.07:1** | 4.5 | ✅ AA |
| `#FFFFFF` (button label) | `--color-green-deep` `#4C5840` | **7.56:1** | 4.5 | ✅ AA + AAA |
| `--color-paper` `#F2F4EE` | `--color-green` `#596749` | **5.48:1** | 4.5 | ✅ AA |
| `#FFFFFF` | `--color-ink` `#372532` | **14.26:1** | 4.5 | ✅ AA + AAA |
| `--color-sage` `#B0B471` | `--color-ink` `#372532` | **6.53:1** | 4.5 | ✅ AA (dark surfaces only) |

**Failing pairs, recorded so nobody rediscovers them:**

| Foreground | Background | Ratio | Ruling |
|---|---|---|---|
| `--color-sage` `#B0B471` | `#FFFFFF` | 2.18:1 | ❌ Never text. Use `--color-sage-text` instead. |
| `--color-stone` `#B0B0A1` | `#FFFFFF` | 2.19:1 | ❌ Never text, never a meaningful boundary. |
| `--color-border` `#D9DCD2` | `#FFFFFF` | 1.39:1 | ❌ Decorative hairlines only. |
| `--color-border` `#D9DCD2` | `--color-paper` `#F2F4EE` | 1.25:1 | ❌ Too weak to divide sections on paper — use whitespace instead. |

**Focus ring:** `2px solid var(--color-green)`, `outline-offset: 2px`. Against
white that is 6.07:1, comfortably over the 3:1 non-text requirement of WCAG
1.4.11. `[PROPOSED]`

### Typography

No external font CDN. The site deploys to GitHub Pages and must be
self-contained; a Google Fonts request is both a third-party dependency and a
render-blocking round trip. Fonts are self-hosted `woff2` in
`site/public/fonts/`, `font-display: swap`, with a real fallback stack behind
each.

| Token | Value | Status |
|---|---|---|
| `--font-display` | `"Lora", Georgia, "Times New Roman", serif` | `[PROPOSED]` |
| `--font-ui` | `"Barlow", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif` | `[OBSERVED]` face / `[PROPOSED]` role |

**Lora** (SIL OFL, Cyreal) is the nearest open equivalent to the transitional
serif on the practice's review cards — moderate stroke contrast, sturdy
bracketed serifs, large x-height, brushed curves. The exact face on those cards
cannot be identified: they are flattened PNGs with no font metadata, so this is
a visual match, not a confirmed identification. `[INFERRED]`

**Barlow** (SIL OFL, Jeremy Tribby) is the practice's *actual current heading
font* per `computed-styles.json` — and it happens to be open-licensed, so it is
self-hostable with no substitution. It moves from headings to body/UI here.
The current body face (`avenir-lt-w01_35-light1475496`, a licensed Avenir cut)
is proprietary and cannot ship; Barlow is a low-contrast humanist grotesk in the
same register. `[OBSERVED]` that Barlow is theirs / `[PROPOSED]` that it becomes
the UI face.

**Files to ship (4, latin subset):** Lora 400, Lora 600, Barlow 400, Barlow 600.
Nothing else. Do not add weights to solve a layout problem.

**The logo wordmark is an image asset.** Never re-typeset "Centennial Family
Dentistry" in Lora and call it the logo — the logo is `assets/logo.jpg` (or a
cleaned derivative). Its roman-caps face is not in this system. `[OBSERVED]`

#### Type scale

Root stays at the browser default (`16px` = `1rem`) — never set `html { font-size }`
to a fixed px, it breaks user zoom preferences.

| Token | Value | Used for | Status |
|---|---|---|---|
| `--text-xs` | `0.875rem` (14px) | Captions, image credits, footer fine print. **Never** body copy. | `[PROPOSED]` |
| `--text-sm` | `1rem` (16px) | Secondary text, labels, nav. Absolute floor for anything a patient must read. | `[PROPOSED]` |
| `--text-base` | `1.125rem` (18px) | **Body copy.** | `[PROPOSED]` |
| `--text-lg` | `1.25rem` (20px) | Lede paragraph, pull quotes. | `[PROPOSED]` |
| `--text-h3` | `1.375rem` (22px) | h3 | `[PROPOSED]` |
| `--text-h2` | `clamp(1.625rem, 1.35rem + 1.4vw, 2rem)` (26→32px) | h2 | `[PROPOSED]` |
| `--text-h1` | `clamp(2.125rem, 1.6rem + 2.6vw, 3.25rem)` (34→52px) | h1 (one per page) | `[PROPOSED]` |

Body at 18px sits above the 16px floor on purpose: the patient base skews older,
and the current site's 15px body is the single most fixable readability problem
in the captures. `[OBSERVED]` (15px, `computed-styles.json`) / `[INFERRED]`
(that 18px is the right answer).

| Token | Value | Status |
|---|---|---|
| `--leading-body` | `1.6` | `[PROPOSED]` |
| `--leading-tight` | `1.2` | `[PROPOSED]` |
| `--measure` | `66ch` (max width of any body text block) | `[PROPOSED]` |
| `--tracking-caps` | `0.08em` (only for the small all-caps eyebrow label) | `[PROPOSED]` |

Headings use `--font-display` at weight 600. Body, nav, buttons and labels use
`--font-ui` at 400, with 600 for emphasis. No italics on headings; no weights
below 400 anywhere — thin type on a site for older readers is a defect.

### Spacing

One scale, 4px base, used for every margin, padding and gap. If a value you want
isn't on the scale, you want a different value.

| Token | Value |
|---|---|
| `--space-3xs` | `4px` |
| `--space-2xs` | `8px` |
| `--space-xs` | `12px` |
| `--space-sm` | `16px` |
| `--space-md` | `24px` |
| `--space-lg` | `32px` |
| `--space-xl` | `48px` |
| `--space-2xl` | `64px` |
| `--space-3xl` | `96px` |

All `[PROPOSED]`.

Layout: `--container: 1120px`, `--gutter: var(--space-md)`. Vertical rhythm
between major sections is `--space-2xl` on mobile, `--space-3xl` from 720px up.
Minimum tap target 44×44px, including the phone-number link.

### Radius and shadow — one each

| Token | Value | Status |
|---|---|---|
| `--radius` | `6px` | `[PROPOSED]` |
| `--shadow` | `0 2px 10px rgba(55, 37, 50, 0.10)` | `[PROPOSED]` |

One radius, applied to buttons, cards and images alike. The building and the
current site's buttons are both hard-edged; 6px keeps that crispness while
softening enough for a family practice. The shadow is tinted with `--color-ink`
rather than pure black, so it reads warm against the off-white palette. Use it
on at most one layer of a page — if two things need lifting, one of them
doesn't.

---

## Imagery rules

**Real practice photos over stock, without exception.** The practice already has
15 usable assets in `brand/_sources/2026-07-22/assets/`: the logo, the building,
and 14 staff/doctor portraits. `[OBSERVED]` Nothing on the pitch site may be a
stock dental photo — no gloved hands, no model smiles, no generic operatory.
The current site mixes real and stock; removing the stock is part of the pitch.

- **The building is the hero-adjacent image.** `assets/building.jpg` (4032×2268)
  shows the actual practice: near-black board-and-batten, standing-seam awnings,
  Douglas fir, blue sky, mown lawn. It is the single strongest photo they own.
  `[OBSERVED]` Crop to 3:2 or 16:9, keeping the roofline and at least one
  evergreen in frame; never crop the practice's own building sign out.
  `[PROPOSED]`
- **Hometown Snohomish / Pacific Northwest is the imagery register.** Evergreens
  (the logo's three trees, the fir beside the building), open sky, daylight,
  green. `[OBSERVED]` in the logo and building photo. That this is the *rule*
  for future imagery, rather than a coincidence of two assets, is `[INFERRED]`.
- **Portraits:** crop to a consistent 4:5 portrait, eyes near the upper third,
  head not clipped. Present all people at the same crop and size — no doctor
  larger than another, no staff member smaller than a doctor. `[PROPOSED]`
- **Treatment:** color-correct only. No duotones, no green wash, no heavy
  filters, no black-and-white. The photos were shot on phones in daylight and
  look like it; that honesty is the point. `[PROPOSED]`
- **Text over photos:** avoid it. If unavoidable, lay `--color-ink` at ≥60%
  opacity across the text area and re-verify the actual rendered contrast — a
  computed ratio against a flat color is not a measurement of text over an
  image. `[PROPOSED]`
- **Alt text is content, not decoration.** Every photo gets meaningful alt text;
  purely decorative marks get `alt=""`. Names and titles in alt text come from
  `products.md` verbatim.
- **Becca has no photo.** The source site uses the logo as her placeholder. Do
  not substitute a stock portrait, and do not silently drop her. `[OBSERVED]`
- **Strip EXIF before publishing.** Several staff photos carry embedded GPS data
  (flagged in `capture-log.md`). Every image that ships must be re-encoded with
  metadata removed. This is a privacy requirement, not an optimization.
  `[OBSERVED]` (the GPS data) / `[PROPOSED]` (the rule).

---

## Channel rules

- **Website only.** There is one channel: the three-page pitch site at
  `https://deliciousllc.github.io/cfd-website/`. No print, email, or social
  variants exist and none should be invented. If Instagram or signage comes
  later, that is a new section written then.
- **Mobile-first.** Design and build the narrow layout first, then let it widen.
  The current site's mobile view (`home-mobile.png`) is the desktop content
  stacked; the pitch's mobile view should look designed for the phone.
- **Self-contained.** No external font CDN, no analytics, no third-party
  embeds. Everything ships from the repo.
- **Usable at 200% zoom** with no horizontal scroll and nothing clipped, per the
  spec's accessibility contract.
- **Single primary action everywhere: Call.** `tel:360-568-6017`, styled as the
  green button, present in the hero, nav and footer. It is the only filled-green
  button on any page — if a second element is competing with it visually, that
  element is wrong.

---

## Anti-patterns — what this brand is not

- Not clinical blue/white/teal. Not a stock dental template with their logo
  dropped in. `[INFERRED]`
- Not gradients, glassmorphism, or animated everything. The building is quiet
  and square; the site should be too. `[INFERRED]`
- Not stock smiling models. `[OBSERVED]` — they have real people.
- Not star ratings or "4.9★" badges. No rating exists in any capture, and
  inventing one on a pitch site for a real practice is a fabrication.
  `[OBSERVED]` — `products.md` gotcha 15.
- Not 72px headings over 15px body. Scale is a relationship, not a size.
