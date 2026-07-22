## P1

1. **Evidence-output directories are never created**
   - **Plan section:** Task 1, Steps 1–5
   - **What fails:** The first Firecrawl and `curl` commands write into `brand/_sources/2026-07-22/` and its `assets/` child, but no step runs `mkdir -p` first. These commands can fail immediately in a clean checkout, preventing every downstream brand task.
   - **Confidence:** 100

2. **Screenshot fallback does not produce the promised PNG files**
   - **Plan section:** Task 1, Step 3
   - **What fails:** `firecrawl scrape "<url>" --format screenshot` returns screenshot output/metadata through the CLI; the plan gives neither `-o` targets nor a procedure for downloading or decoding the returned screenshot. An implementer cannot obtain the required `home-*.png` and `services-*.png` artifacts from the stated fallback.
   - **Confidence:** 100

3. **Every supplied commit command violates the plan’s own commit contract**
   - **Plan section:** Global Constraints; Tasks 1–6 and 8–15
   - **What fails:** The plan requires every commit message to end with a `Co-Authored-By:` line, but every example uses a one-line `git commit -m` without that trailer. Executing the plan verbatim creates noncompliant commits throughout.
   - **Confidence:** 100

4. **Final fact corrections can reach production without verification**
   - **Plan section:** Tasks 14–15
   - **What fails:** Task 14 performs the live browser check before Task 15 re-verifies facts. Task 15 may then change `products.md` and affected pages and push them, triggering a new deployment, but it does not watch that workflow or recheck the final live site at mobile and desktop widths. The delivered URL can therefore differ from the version that passed deployment, rendering, link, and accessibility checks.
   - **Confidence:** 100

5. **The evidence set cannot guarantee complete service and pricing provenance**
   - **Plan section:** Task 1, Step 2; Task 3, Step 1
   - **What fails:** Task 1 scrapes the aggregate pricing page and only three representative service pages, while Task 3 requires every service and every price listed anywhere on the source site. The plan never checks the complete inventory for service pages containing additional facts or prices, nor conditionally scrapes those pages. An implementer can follow the plan exactly and still produce an incomplete “single source of truth.”
   - **Confidence:** 90

## P2

6. **Brand-file task ordering conflicts with the approved build order**
   - **Plan section:** Tasks 3–5
   - **What fails:** The approved spec orders the brand files as visual → voice → products → handoffs. The plan creates `products.md` first and combines each family’s driver, decisions, and handoff into one task. Although technically executable, it does not implement the approved dependency sequence and gives no rationale for the change.
   - **Confidence:** 100

7. **The provenance verification command cannot verify its stated invariant**
   - **Plan section:** Task 3, Step 2
   - **What fails:** Counting lines containing `captured 2026-07-22` only counts citations; it cannot identify fact-bearing lines without citations. The instructed “spot-check” likewise cannot establish that every fact has provenance, despite this being a success criterion and the contract consumed by all three pages.
   - **Confidence:** 100

8. **The owner checkpoint can modify files without the required task commit**
   - **Plan section:** Task 7
   - **What fails:** Task 7 explicitly applies corrections to brand files but has no commit step, contradicting “Commit at the end of every task.” Those changes become mixed into the Astro scaffold commit, obscuring checkpoint decisions and weakening the promised per-task history.
   - **Confidence:** 100

9. **Complete navigation inventory is inferred from an unscoped link dump**
   - **Plan section:** Task 2, Step 1
   - **What fails:** `home.json` contains page links, not a normalized navigation model. It may include repeated responsive/footer links and unrelated page links, while client-rendered or hidden navigation entries may be absent. The plan supplies no rendered-nav cross-check against desktop/mobile screenshots or DOM output, so “every nav item exactly once” is not reliably achievable.
   - **Confidence:** 85

10. **Active-page navigation behavior lacks an implementable interface**
    - **Plan section:** Task 9, Steps 2–3
    - **What fails:** The plan requires `aria-current="page"` and visible active treatment but does not specify whether `Nav.astro` derives the current route from `Astro.url`, receives it from `BaseLayout`, or normalizes paths with the `/cfd-website` base. It also never explicitly verifies the active state on all three routes. A zero-context implementer can easily compare incompatible pathname forms or render no active state.
    - **Confidence:** 85

11. **The accessibility image audit uses a misleading count comparison**
    - **Plan section:** Task 13, Step 2
    - **What fails:** Comparing `grep -c "<img"` with `grep -c 'alt='` counts matching lines per file, not image elements. Multiple images on one line, multiline markup, or unrelated `alt=` text defeats the check. The later eyeball instruction helps, but the stated smoke test cannot support the claimed structural verification.
    - **Confidence:** 95

## P3

12. **Service-group naming drifts between the spec and plan**
    - **Plan section:** Task 2, Step 2; Tasks 10–11
    - **What fails:** The spec calls the final group “extras,” with 3D printing explicitly included, while the plan establishes “Technology & extras” as authoritative. The change is plausible but unexplained, and the exact anchor IDs are never fixed, leaving Home and Services to coordinate names and fragments during implementation.
    - **Confidence:** 80

---
*Reviewer: Codex CLI 0.145.0 (read-only, non-interactive). Adjudication: all 12 findings accepted and fixed in the plan same-day; finding 6 resolved by amending the spec's build-order line (products first, families bundled) rather than reordering the plan. See Review Log in the spec.*
