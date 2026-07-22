# Logo palette re-sample — 2026-07-22

Follow-up capture. Task 4's report (`.superpowers/sdd/task-4-report.md`)
describes re-sampling `assets/logo.jpg` beyond the four-color average already
recorded in `capture-log.md` ("Logo color samples") — a whole-image 12-color
quantize, plus a crop isolating the tree artwork — but those results were
never written to a file in this evidence folder, only narrated in the report.
This file re-runs that sampling for real and records the exact commands and
raw output, so the hex values used in `brand/visual.md` trace to something
anyone can re-open, per the review finding that prompted it.

Source asset: `assets/logo.jpg`, confirmed 591×264 px:

```
$ magick brand/_sources/2026-07-22/assets/logo.jpg -format "%wx%h" info:
591x264
```

## Sample 1 — whole-image, 12-color quantize

```
$ magick brand/_sources/2026-07-22/assets/logo.jpg -colors 12 -unique-colors txt:-
# ImageMagick pixel enumeration: 10,1,0,255,srgb
0,0: (55,39,50)  #372732  srgb(21.5582%,15.1114%,19.6722%)
1,0: (72,63,62)  #483F3E  srgb(28.3599%,24.5599%,24.4567%)
2,0: (93,109,78)  #5D6D4E  srgb(36.5668%,42.7636%,30.5217%)
3,0: (123,129,111)  #7B816F  srgb(48.2643%,50.4884%,43.691%)
4,0: (181,184,114)  #B5B872  srgb(70.9787%,72.2047%,44.5607%)
5,0: (176,176,161)  #B0B0A1  srgb(69.0667%,69.1625%,63.0895%)
6,0: (238,241,235)  #EEF1EB  srgb(93.2026%,94.3791%,92.0261%)
7,0: (245,247,244)  #F5F7F4  srgb(95.9477%,96.8627%,95.7516%)
8,0: (254,254,253)  #FEFEFD  srgb(99.5518%,99.5378%,99.3975%)
9,0: (255,255,255)  #FFFFFF  srgb(99.999%,99.999%,99.9991%)
```

12 colors were requested (`-colors 12`); ImageMagick found 10 unique colors in
the actual image. Reading off the non-white/near-white rows:

| Hex | Read as |
|---|---|
| `#372732` | dark tree / wordmark (plum) |
| `#483F3E` | transitional shadow tone between plum and green |
| `#5D6D4E` | mid green |
| `#7B816F` | transitional tone between mid green and sage |
| `#B5B872` | sage |
| `#B0B0A1` | muted gray-tan (matches `capture-log.md`'s existing sample exactly) |
| `#EEF1EB` | off-white field |

This exactly reproduces the five hex values the Task 4 report's narrative
attributed to "12-color quantize": `#372732`, `#5D6D4E`, `#B5B872`, `#B0B0A1`,
`#EEF1EB`.

## Sample 2 — trees-only crop (left 40%)

Crop region: left 40% of the 591px width, full 264px height —
`round(591 × 0.4) = 236`, so `236x264+0+0`.

```
$ magick brand/_sources/2026-07-22/assets/logo.jpg -crop 236x264+0+0 +repage /tmp/logo-crop-left40.png
$ magick /tmp/logo-crop-left40.png -format "%wx%h" info:
236x264
```

Quantizing this crop at `-colors 12` (matching Sample 1's request) still mixes
the plum and the darkest green into shared buckets. Requesting fewer colors
gives the crop's own distinct clusters room to separate; `-colors 7` was the
smallest count that cleanly isolated four hues plus white:

```
$ magick /tmp/logo-crop-left40.png -colors 7 -unique-colors txt:-
# ImageMagick pixel enumeration: 6,1,0,255,srgb
0,0: (62,45,54)  #3E2D36  srgb(24.1928%,17.6938%,21.0264%)
1,0: (92,112,74)  #5C704A  srgb(36.1842%,44.1089%,28.9931%)
2,0: (176,180,113)  #B0B471  srgb(68.9648%,70.443%,44.2041%)
3,0: (185,187,156)  #B9BB9C  srgb(72.3826%,73.4605%,61.3669%)
4,0: (255,255,255)  #FFFFFF  srgb(99.9967%,99.9966%,99.9961%)
5,0: (254,254,254)  #FEFEFD  srgb(99.6581%,99.6843%,99.4135%)
```

7 colors were requested; 6 unique were found. Reading off the non-white rows:

| Hex | Read as |
|---|---|
| `#3E2D36` | dark tree / wordmark edge (plum), crop-local sample |
| `#5C704A` | mid tree (green) |
| `#B0B471` | light tree (sage) |
| `#B9BB9C` | muted gray-tan, crop-local sample |

This exactly reproduces the four hex values the Task 4 report's narrative
attributed to "Trees-only crop (left 40%)": `#3E2D36`, `#5C704A`, `#B0B471`,
`#B9BB9C`.

For reference, intermediate `-colors` values tried on the same crop before
landing on 7 (kept here for transparency, not as separate findings):

```
$ magick /tmp/logo-crop-left40.png -colors 5 -unique-colors txt:-
0,0: (81,88,66)    #515842
1,0: (176,180,113) #B0B471
2,0: (185,187,156) #B9BB9C
3,0: (255,255,255) #FFFFFF
4,0: (254,254,254) #FEFEFE
```
(`#B0B471` already resolves here; the plum has not yet separated from the
green at this color count.)

## Reconciliation

Both re-samples reproduce the Task 4 report's narrated values exactly — this
was a real, repeatable ImageMagick result all along, just never written to a
file in `_sources/`. No hex value in `brand/visual.md`'s color tokens needs to
change as a result of this re-sample.

One color is **not** covered by this file: `brand/visual.md` also cites
`#5B694B` as a sample from the review-card image
(`856d6c_f8a699b786684210ade3a46574cf5672~mv2.png`). That image was never
downloaded into `_sources/2026-07-22/assets/` (only referenced by URL in
`reviews-rendered.md`), and no tool-based color sample of it exists anywhere
in this evidence folder. It is out of scope for this file (which only
re-samples `logo.jpg`) and is addressed instead by retagging that specific
claim `[INFERRED]` in `visual.md` and logging it in `visual_decisions.md`.

**Date:** 2026-07-22. **Tool:** ImageMagick (`magick`, confirmed on `PATH`).
**Source asset:** `brand/_sources/2026-07-22/assets/logo.jpg` (unmodified,
591×264 px JPEG, per `capture-log.md`). The intermediate crop
(`/tmp/logo-crop-left40.png`) is a derived scratch file, not evidence itself —
it is fully reproducible from the two commands above and is not checked in.
