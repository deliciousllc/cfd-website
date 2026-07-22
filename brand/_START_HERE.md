# Brand system — start here

Master map of the `brand/` directory for the Centennial Family Dentistry redesign
pitch. Read this file first in any session that touches facts, copy, or design —
then jump to the one file the task actually needs. Don't load the whole
directory; each row below tells you when a file earns its context.

## File map

| File | What it is | When to load |
|---|---|---|
| `brand/products.md` | Verbatim practice facts (names, prices, hours, address, phone, quotes) with a per-fact `(source: …, captured 2026-07-22)` citation. Opens with a **Locked Terminology & Fact Gotchas** section — 16 numbered rules, including that the source site contradicts itself on six prices. | Any session that puts a practice fact on screen or in copy. Load unconditionally — this is the only place facts come from. |
| `brand/visual.md` | The design tokens: palette, type scale, spacing, radius, shadow, contrast ledger. Status-tagged (`[OBSERVED]` / `[PROPOSED]` / `[RATIFIED]`). | Building or styling any page or component. |
| `brand/visual_decisions.md` | The why-layer for `visual.md` — invariants, rejected alternatives, the open register of unconfirmed inferences. | Only when *changing* a token or design rule — not in a production styling session. |
| `brand/visual_handoff.md` | Session starter for visual work: Working WITH vs Working ON, load order, survive-if-nothing-else-loaded rules, pre-delivery QA gate, State of play. | First file opened for any visual/styling task. |
| `brand/voice.md` | The voice rules: emotional engine, personality words, numbered rules, anti-patterns, messaging tiers. Status-tagged like `visual.md`. | Writing or editing any page copy. |
| `brand/voice_decisions.md` | The why-layer for `voice.md` — extraction basis per rule, rejected alternatives, open register. | Only when *changing* a voice rule — not in a production copy session. |
| `brand/voice_handoff.md` | Session starter for copy work: Working WITH vs Working ON, load order, survive rules, pre-delivery QA gate, State of play. | First file opened for any copywriting task. |
| `brand/_sources/2026-07-22/` | Immutable dated evidence: page scrapes, desktop/mobile screenshots, computed styles (`computed-styles.json`), logo palette resample, verbatim review transcriptions, the service-inventory map, and the capture log. | Only when a change claims to be evidence-based, or to re-verify a fact/token against the live capture. Never edit — a new capture gets a new dated folder. |

## Task → handoff lookup

| If the task involves… | Load |
|---|---|
| Any practice fact (price, hour, name, quote, credential, address, phone) | `brand/products.md` — always, regardless of what else is loaded |
| Site copy (writing, editing, rewriting page text) | `brand/voice_handoff.md` |
| Styling, layout, or tokens (colors, type, spacing, components) | `brand/visual_handoff.md` |
| Changing a voice rule or its rationale | `brand/voice_handoff.md` → its "Working ON" section |
| Changing a design token or its rationale | `brand/visual_handoff.md` → its "Working ON" section |
| Verifying a fact or token against the original site | `brand/_sources/2026-07-22/` |

## Family tree

```
brand/
├── _START_HERE.md          you are here
├── products.md              facts (no decisions file — facts don't need one; corrections
│                             become numbered gotchas in place, per session)
├── visual.md                ← visual_decisions.md   (evidence/rationale)
│      ↑                            ↑
│      └──────── visual_handoff.md ─┘   (session starter, points at both)
├── voice.md                 ← voice_decisions.md    (evidence/rationale)
│      ↑                            ↑
│      └──────── voice_handoff.md ──┘   (session starter, points at both)
└── _sources/2026-07-22/     immutable evidence behind every fact and every
                              inferred token/rule in the files above
```

Pattern: each driver (`visual.md`, `voice.md`) has one decisions file (the why,
read only when changing the driver) and one handoff (the session starter, read
first, points to whichever of the other two the task needs). `products.md` is
the exception — it has no decisions file because facts aren't designed, they're
sourced; a correction becomes a new numbered gotcha in `products.md` itself,
the same session it's found.

## Maintenance rules

1. **Rules live at the point of use.** A rule about facts goes in
   `products.md`'s gotchas; a rule about tokens goes in `visual.md`; a rule
   about copy goes in `voice.md`. Don't centralize rules somewhere else "for
   convenience" — the next session won't find them there.
2. **Research snapshots are dated and immutable.** Everything under
   `brand/_sources/` is read-only once written. New research — a re-scrape, a
   new screenshot, a corrected computed-style pull — goes in a new dated
   folder (e.g. `brand/_sources/2026-08-15/`). Never edit an existing dated
   folder's contents.
3. **Never rename a file without a full-folder sweep for the old name.** A map
   entry, a handoff's load order, or a cross-reference that still points at
   the old filename is a broken pointer — grep the whole `brand/` directory
   (and `site/` once it exists) for the old name before considering a rename
   done.
4. **Status-line discipline.** Every `visual.md` / `voice.md` value and rule
   carries a status tag (`[OBSERVED]`, `[INFERRED]`, `[PROPOSED]`,
   `[RATIFIED]`). An inference never self-promotes to `[RATIFIED]` — only the
   practice's own confirmation does that, never a project lead's approval or a
   value surviving a few sessions untouched.
5. **Grow `products.md`'s gotchas from corrections, not from foresight.** When
   a fact turns out to be wrong, contradicted, or easy to misread, the fix is
   a new numbered rule in the Locked Terminology & Fact Gotchas section the
   same session — don't pre-write hypothetical gotchas.
6. **Rule lists have a soft cap.** Keep numbered rule lists (gotchas, voice
   rules, decisions) to roughly 10 items and handoff files to roughly 150
   lines. Hitting the cap is a signal to consolidate or compress overlapping
   entries before appending a new one — don't let any single file grow
   without bound.

<!-- seed version: July 2026 -->
