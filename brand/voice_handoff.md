# Voice handoff — Centennial Family Dentistry

**Revision:** 1 · **Last updated:** 2026-07-22

Session starter for anything that touches how the pitch site *reads*. Two modes
— pick one before you start.

- **Working WITH** — writing or editing copy using the established voice.
- **Working ON** — changing the voice rules themselves.

---

## Working WITH (producing — copy for pages, components, CTAs)

### Load order

1. `brand/voice.md` — the rules. This is the whole voice system.
2. `brand/products.md` — **any** practice fact that appears in the copy (names,
   prices, hours, address, phone, quotes, credentials), including its "Locked
   Terminology & Fact Gotchas" section at the top. Read the gotchas; several are
   traps (six contradicted prices, "13 reviews" is wrong, typos in quotes are
   verbatim).
3. `brand/visual_handoff.md` — only if you are also laying the copy into a page.

Do **not** load `voice_decisions.md` in a production session. It is a diagnostic
file; loading it spends context on debate you are not having.

### Rules that survive if nothing else is loaded

1. **Facts come from `products.md` verbatim — never improvise.** If a fact isn't
   there, ask; never fill it from general knowledge.
2. **No invented practice copy.** No testimonials, anecdotes, credentials,
   sentiment, or claims that aren't traceable to the evidence.
3. **Rewrite how it reads, never what it asserts** — phrasing, grammar,
   structure, and first-person→"we" are fixable; a fact, price, name,
   credential, or patient quote is not. Patient quotes keep their original typos.
4. **Name people, not "our team"** — doctors and staff by name.
5. **State the price plainly** — never "call for pricing" where a price exists.
6. **Name the fear, then lower it** — reassure, never scare; no corporate hype.

### Pre-delivery QA gate (run before calling any copy done)

Report the gate's result with the work, one line per pass.

1. **Guardrail pass** — no anti-pattern present: no anonymous "our team," no
   "contact us for pricing" where a price exists, no corporate hype, no
   fear-based selling, no fabricated warmth, no cold/clinical register, no
   invented facts (star ratings, "13 reviews," "years serving Snohomish," a
   single made-up figure for a contradicted-price service).
2. **Fact pass** — every fact in the copy traces to a `products.md` line, and no
   gotcha is violated. Every price, name, credential, hour, and quote is
   verbatim from that file; patient-quote typos are preserved, not corrected.
3. **Specificity pass** — read each sentence and ask: *could this describe any
   dentist?* If yes, rewrite it until it could only describe this practice — add
   the name, the price, the town, or the specific thing that happens at the
   visit. Generic warmth fails this pass.
4. **Clarity pass** — plain-spoken and readable: short sentences, patient's
   words not clinical jargon, "we" not "I", no filler adjectives standing in for
   a specific. Read it aloud; if it sounds like a brochure, it isn't done.

---

## Working ON (improving — changing the voice rules)

### Load order

1. `brand/voice.md`
2. `brand/voice_decisions.md` — including the open register at the bottom.
3. `brand/_sources/2026-07-22/` — the evidence, if the change claims to be
   evidence-based. This folder is **immutable**: read it, never edit it. A new
   capture goes in a new dated folder.

### How to change a rule

1. **Name what it's extracted from first.** Which source phrasing, in which
   file, does this rule come from? If none, it is a guardrail or a preference,
   not an extraction — label it `[INFERRED]` and log it as `[PROPOSED]` in
   `voice_decisions.md`.
2. **Keep the status tag honest.** An inference stays `[PROPOSED]` no matter how
   confident you are, and no matter how many people internally like it.
   `[PROPOSED]` becomes `[RATIFIED]` only when the practice says so — not when
   the project lead approves it, and not after it survives a few sessions.
3. **Corrections become rules the same session they happen,** at their point of
   use — mirroring the products.md convention.
4. **Bump the revision number** at the top of `voice.md` and stamp the date.
5. **Log it in `voice_decisions.md`** — the choice and its basis, plus any
   rejected alternative — and update this file's State of play.

---

## State of play (one paragraph — as of 2026-07-22)

The voice family exists at revision 1, extracted from the 2026-07-22 capture of
the live Wix site — the About-page bios, every service and pricing page, the
financing page, and all twelve verbatim patient reviews. `voice.md` carries an
emotional engine, three personality words (Named / Plain-spoken / Steadying),
ten rules, seven anti-patterns, and brand-vs-page messaging tiers; every rule
and anti-pattern is tagged `[OBSERVED]` with its source phrasing or `[INFERRED]`
as a guardrail. Nothing here has been seen by the practice: all seven inferred
claims (V1–V7) are logged `[PROPOSED]` with basis and risk in
`voice_decisions.md`, alongside a six-item open register — the sharpest
questions for the project lead's Task 7 checkpoint being whether the practice
deliberately publishes its prices (which decides how hard the transparency
thesis leans) and whether "Steadying" or "thorough" is the truer third word. The
two real tensions are resolved on the page: the rewrite-vs-never-change line is
Rule 10 and lives in the survive-if-nothing-else list, and the first-person page
plus the site's typos are classed as errors the rewrite fixes, not voice to
preserve. Next consumers are Tasks 10–12, which write the actual home, services,
and financing copy against these rules; no page copy has been drafted yet, so no
rule has been exercised against real headlines.
