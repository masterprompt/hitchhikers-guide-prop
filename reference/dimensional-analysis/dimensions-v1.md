# Prop Dimensions — Estimate v1 (single-frame)

**Source frame:** `reference/screenshots/Screenshot 2026-05-06 at 1.53.15 PM.png` —
Arthur Dent (Martin Freeman) holding the Guide open in front of him.

**Source measurements:** see [`notes.md`](notes.md).

---

## Scale calibration

| Reference | Pixel measurement | Real-world value | Scale |
|---|---|---|---|
| Arthur's nose-to-chin (subnasale to gnathion) | 180 px | 80 mm (assumed) | **0.4444 mm/px** |

## Computed prop dimensions (closed book)

| Dimension | Pixels | mm | inches |
|---|---|---|---|
| Height (spine length) | 343 | **152.4** | **6.00"** |
| Cover width (one face) | 236 | **104.9** | **4.13"** |
| Thickness (closed) | 72 | **32.0** | **1.26"** |

For mental reference: this is the size class of a **compact mass-market
paperback** — slightly shorter than a typical paperback (which is
~178 × 110 × 25 mm) but a bit thicker.

---

## Error sources, ranked by impact

### 1. Assumed nose-to-chin reference (largest source of error)

The 80 mm assumption is at the high end of typical adult-male
anthropometric ranges. Common values in the literature for subnasale-to-gnathion
distance fall around 65–75 mm. If Martin Freeman's actual nose-to-chin is
closer to 70 mm, dimensions scale down by ~13%:

| Dimension | At 80 mm assumption | At 70 mm assumption |
|---|---|---|
| Height | 152 mm (6.00") | **133 mm (5.25")** |
| Cover width | 105 mm (4.13") | **92 mm (3.61")** |
| Thickness | 32 mm (1.26") | **28 mm (1.10")** |

**To tighten this:** measure a second anatomical reference (hand width
≈ 85–90 mm for adult male, or head width ≈ 145–160 mm) from the same
frame and cross-check.

### 2. Camera-plane angle of the prop

In the source frame the prop is held open at a clamshell angle and
rotated relative to the camera. The "cover width" measurement is taken
on a face that may not be exactly perpendicular to the camera. If the
prop face is rotated by angle θ from camera-perpendicular, the apparent
width is foreshortened by `cos(θ)` — true width could be 5–15% larger
than the measurement suggests.

The spine-height measurement is much less affected (the book is held
roughly vertically). Thickness is most sensitive to angle and could be
under- or over-estimated by 10–20%.

### 3. Pixel-measurement precision

Eyeball pixel measurements are typically ±2–3 px. At 0.4444 mm/px that's
±1–1.5 mm per dimension. Smaller than the error from #1 and #2 but not
zero.

### 4. Open-vs-closed ambiguity

The frame shows the prop **open**. The "thickness" measurement is what's
visible at the hinge/spine in the open configuration, which is roughly
the closed thickness — but it's not the same dimension as a perfectly
side-on closed-book measurement.

---

## Working estimate

Taking the central numbers and acknowledging ~15% error bars:

> **Closed prop: ~150 × 105 × 32 mm (6.0 × 4.1 × 1.3 in), ± 15%**

That maps to a lower-bound estimate of ~133 × 92 × 28 mm and an upper
bound of ~165 × 115 × 35 mm. The **true** dimension almost certainly sits
within that envelope.

---

## Implications for downstream decisions

### Screen size

Originally OPEN-QUESTIONS #2 had 5" HDMI as the leading candidate.
**These measurements bring that into question.** With ~105 mm cover
width, the inner upper panel (after enclosure walls and bezel) has
roughly:

- **Usable face:** ~95 × 142 mm (assuming ~5 mm wall on each side)

A common 5" 800×480 IPS panel has an active area of ~109 × 65 mm in
landscape. **That exceeds the 95 mm width budget** — a 5" landscape
panel won't fit without violating the closed-book width.

Better fits:

| Display | Active area | Fits in ~95 × 142 mm? |
|---|---|---|
| 4" 800×480 IPS (landscape) | ~88 × 53 mm | Yes, comfortably |
| 4.3" 800×480 IPS (landscape) | ~95 × 54 mm | Tight, marginal |
| 5" 800×480 IPS (portrait) | ~65 × 109 mm | Yes, but wrong orientation |
| 3.5" SPI LCD | ~75 × 55 mm | Yes, with large bezels |

**Provisional recommendation update: 4" 800×480 IPS in landscape**
becomes the new leading candidate. Re-confirm after error reduction
(see #1 above).

### Electronics envelope

32 mm closed thickness, split across two halves = ~16 mm per half. With
~3 mm walls top and bottom, internal Z-height ≈ 10 mm per half. That's:

- Plenty for a Pi Zero 2 W (max ~5 mm board thickness with USB-C
  daughterboard).
- Enough for a 1500–2000 mAh LiPo (typical thickness 5–7 mm).
- Tight but feasible for a small speaker (most thin speakers are 3–8 mm).

### Aspect ratio reality check

Cover face = 152 × 105 mm = 1.45:1 ratio. That's between portrait A5
(1.41:1) and US trade paperback (1.55:1). The film prop reads as
"slightly tall paperback" — the measurements are consistent with how
the prop appears in hand on screen.

---

## Per-screen analysis (added after dual-display clarification)

Source frame: `reference/screenshots/Screenshot 2026-05-06 at 1.53.21 PM.png`
— close-up of the open Guide showing the screen with content playing.

The user clarified that the prop is intended as a **dual-display build**
(one panel per inner cover, butted at the spine), and that the
measurements in this frame are for **one half** of the open Guide. See
ADR-0005 for the architectural rationale.

### Measurements (one half)

From [`notes.md`](notes.md):

- Book cover width (one half): 1033 px
- Screen width: 905 px
- Screen height: 842 px
- Matte/bezel side: 116 px
- Matte/bezel top/bottom: 156 px

### Frame-specific scale

Using the v1 cover-width estimate of 105 mm (note: this assumption
inherits the v1 error bar):

> 105 mm / 1033 px = **0.1017 mm/px**

### Computed per-screen dimensions

| Element | Pixels | Real-world (mm) | Real-world (in) |
|---|---|---|---|
| Each screen (active area) | 905 × 842 | **92.0 × 85.6** | 3.62" × 3.37" |
| Per-screen aspect ratio | — | **1.075 : 1** (basically square) | — |
| Combined display when open | 1810 × 842 | ~184 × 86 | 7.24" × 3.37" |
| Top/bottom matte (each) | 156 px | ~15.9 | ~0.62" |
| Side matte (each) | 116 px | ~11.8 | ~0.46" |

### Aspect-ratio reconciliation

The combined open-Guide visible display in the film reads as ~2:1
landscape. Two near-square panels butted side-by-side gives a 2.15:1
combined aspect, which matches what's observable in the source frame.
The dual-display design is consistent with what the film prop appears
to do.

### Bezel arithmetic discrepancy (open issue)

The horizontal numbers do not internally reconcile:

- Screen width 905 + 2 × side bezel 116 = **1137 px**
- Cover width = **1033 px**
- Discrepancy: **+104 px** (≈ +10.6 mm)

That is, screen-plus-symmetric-side-bezels overshoots the cover width
by ~10%. Three plausible explanations:

1. **The 116 px "matte/bezel side" is the leather border only**, not
   the full distance from cover edge to screen edge. There is a silver
   metal frame between the leather and the screen visible in the
   source image; that frame's width may be unmeasured.
2. **Asymmetric bezel.** The film prop has a speaker grille on one
   side (visible bottom-left in the source frame), so the matte on
   that side may be wider than on the opposite side. A single 116 px
   measurement applied symmetrically would over-count.
3. **Different reference edges.** "Cover width" may have been measured
   to the outer edge of one element (e.g., cover leather), while
   "screen width" is the active LCD area, while "bezel side" is to a
   third reference (e.g., the silver frame outer edge).

**Action:** clarify which physical edge each measurement is taken to,
in a follow-up measurement pass. Until resolved, treat the screen
width and height as more reliable than the bezel measurements.

### Vertical sanity check

Screen height 842 + 2 × top/bottom bezel 156 = **1154 px**.

We don't have a direct cover-height measurement in this frame to
compare against, but the v1 cover height is 152 mm = ~1496 px in this
frame's scale. That leaves 1496 − 1154 = 342 px (~35 mm) unaccounted
for, presumably distributed as additional matte or trim above/below
the measured bezel. Plausible — many prop devices have larger bezels
at the long ends than the short ends.

### Implications for screen sourcing

A 92 × 86 mm square-ish IPS panel is not a common hobbyist part.
Available options and how they compare:

| Available panel | Active area | Compared to target |
|---|---|---|
| 4" 480×480 square IPS | ~70 × 70 mm | **24% smaller** per side |
| 4" 720×720 round/square | ~72 × 72 mm | **22% smaller** per side |
| 3.5" 320×480 SPI LCD | ~75 × 50 mm | Wrong aspect (3:2 not 1:1) |
| 5" 1080×1080 square IPS | ~110 × 110 mm | Too large for 105 mm cover |

There is no off-the-shelf hobbyist panel that hits 92 × 86 mm at the
target aspect. Two practical paths:

- **A.** Match panel to cover: use the best-available square panel
  (~70 × 70 mm) and live with a wider matte than the film prop has.
  Closed prop dimensions stay film-accurate; the matte:screen ratio
  drifts.
- **B.** Match cover to panel: scale the closed prop dimensions down
  so the panel-to-cover ratio matches the film. Closed prop becomes
  smaller than the film-accurate 152 × 105 mm.

The right choice depends on which fidelity matters more — overall
prop size or screen-to-cover proportion. Recommend evaluating both
mock-ups before committing.

## Next step before locking the dimensions

Before committing to a 3D model based on this, do at least one of:

1. **Cross-check on a second reference in the same frame** (Arthur's
   hand width or head width).
2. **Re-measure on a different frame** where the prop is held more
   perpendicularly to camera (look for frames where the cover faces the
   camera rather than being held at an angle).
3. **Look up Martin Freeman's actual subnasale-to-gnathion** from any
   public anthropometric data (unlikely to exist) or use a second actor
   in the same scene as a sanity check.

Any of these tightens the error bar significantly. After that, lock the
dimensions and proceed to screen selection.
