# Prop Dimensions — v2 (scaled down to fit 4" 720×720 panels)

ADR-0006 selected two 4" 720×720 IPS MIPI panels as the displays. Each
panel has an active area of ~72 × 72 mm, smaller than the v1 per-screen
target of ~92 × 86 mm. To preserve the film prop's visual proportions
(matte and screen layout per cover face), the closed prop scales down
proportionally.

This document supersedes the prop-size implications portion of v1 for
build purposes. The v1 estimates remain useful as the *film-accurate*
reference; v2 is the *as-built* target.

## Source ratios (from v1, per-half cover)

- Film-estimated cover (per-half): 105 mm wide × 152 mm tall
- Film-estimated screen (per-half): 92 mm wide × 86 mm tall
- Screen-width / cover-width: **0.876**
- Screen-height / cover-height: **0.566**

The asymmetric ratios mean the film prop has more matte at the top and
bottom of each cover than at the sides — consistent with the visible
"DON'T PANIC" decorative space top/bottom.

## v2 target dimensions

Maintaining both ratios with a 72 × 72 mm panel:

| Dimension | Calculation | Result |
|---|---|---|
| Per-half cover width | 72 / 0.876 | **~82 mm** (3.23") |
| Per-half cover height | 72 / 0.566 | **~127 mm** (5.00") |
| Closed prop height (= cover height) | — | **~127 mm** (5.00") |
| Closed prop width (= cover width) | — | **~82 mm** (3.23") |
| Closed prop thickness (panel + electronics + walls) | proportional to v1 32 mm × ~0.83 avg scaling | **~28 mm** (1.10") |

### Working envelope summary

> **Closed prop: ~127 × 82 × 28 mm (5.0 × 3.2 × 1.1 in)**
>
> **Open spread: ~127 × 168 mm (height × full open width including
> spine ~4 mm hinge gap)**

Cover aspect ratio: 127:82 = 1.55:1 — close to a US trade paperback
(1.55) and slightly less tall than a UK B-format paperback (1.61).

## Mental reference

| Object | Approximate size |
|---|---|
| **v2 prop, closed** | **127 × 82 × 28 mm** |
| Pocket Bible / Moleskine pocket | ~140 × 90 × 13–22 mm |
| Trade paperback (US) | ~203 × 137 × 25 mm |
| iPhone 15 Pro Max | 159 × 76 × 8 mm |
| Mass-market paperback | ~178 × 110 × 25 mm |

The v2 prop is in the **pocket Bible / Moleskine pocket** size class —
visibly smaller than the film prop's apparent in-hand size, but
preserves the screen-on-cover proportions and book-shape character.

## Internal volume budget (each half)

Half thickness ≈ 14 mm; subtract printed walls (~2 mm × 2) → internal
height per half ≈ 10 mm.

Per-half internal envelope: **82 mm wide × 127 mm tall × 10 mm deep =
~104 cm³ usable per half.**

Notional component fit:

| Component | Approx footprint | Notes |
|---|---|---|
| 4" 720×720 panel + controller board | ~80 × 80 × 5 mm (panel) + ~50 × 30 × 7 mm (controller) | Fits one half with the panel as the front face and controller mounted to the inside back |
| Pi 4 (compute) | 85 × 56 × 17 mm | **Does not fit a single half** — needs to span both halves at the spine, or live in the lower-cover half if all electronics consolidate there |
| Pi Zero 2 W (alternative compute) | 65 × 30 × 5 mm | Fits one half easily |
| 18650 LiPo or 2000 mAh pouch | ~70 × 35 × 7 mm | Fits |
| Small mono speaker (e.g., 23 mm × 16 mm × 4 mm) | tiny | Fits |
| 5 V boost regulator board | ~25 × 15 × 6 mm | Fits |

### Compute reality check

A Pi 4 board is too thick (17 mm) to fit in a 10 mm internal half. Two
practical mitigations:

1. **Use Pi Zero 2 W with HDMI-to-MIPI bridge boards** instead of the
   bundled controller boards. Trickier wiring, but Pi Zero 2 W is 5 mm
   thick. Means re-evaluating ADR-0005's compute conclusion.
2. **Use the Raspberry Pi Compute Module 4** mounted on a custom thin
   carrier board. CM4 is 55 × 40 × 4.7 mm; with a thin carrier exposing
   dual HDMI it can be slimmer than a Pi 4. Most expensive and most
   custom path.
3. **Use a Pi 4 anyway** and increase the closed-prop thickness to
   accommodate it (~32–35 mm closed instead of 28). Costs a little
   prop fidelity, gains compute simplicity.

This is an unresolved sub-question. Capture as new follow-up under
OPEN-QUESTIONS #3.

## Caveats

- The v2 dimensions inherit all of v1's error bars, including the
  ±15% uncertainty on the 80 mm nose-to-chin reference. v1's
  cross-check item (OPEN-QUESTIONS #1) still applies and could
  shift v2 dimensions correspondingly.
- The bezel-arithmetic discrepancy noted in v1 is unresolved. If
  resolved in a way that changes the screen-to-cover-width ratio,
  v2 dimensions update.
- The 28 mm thickness estimate is a working assumption based on
  scaling v1 thickness by the average cover-dimension scaling. The
  real thickness will be driven by what actually fits inside (panels,
  Pi, battery, speaker). Validate via CAD before printing.
