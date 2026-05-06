# Open Questions

Items needing decisions, in roughly dependency order. Each blocks the next
unless noted. Move resolved items into a new ADR under `docs/adr/` and
remove them from this list.

---

## 1. Prop dimensions (PROVISIONAL — needs cross-check)

**Status:** First-pass estimate complete from a single frame. See
[`reference/dimensional-analysis/dimensions-v1.md`](reference/dimensional-analysis/dimensions-v1.md).

**Working estimate:** closed prop ≈ **150 × 105 × 32 mm
(6.0 × 4.1 × 1.3 in), ± 15%**.

**Open follow-up before locking dimensions:**

- Cross-check using a second anatomical reference (hand or head width)
  in the same frame, OR
- Re-measure on a more camera-perpendicular frame, OR
- Use a second actor in the same scene as a sanity check.

The 80 mm nose-to-chin assumption is the largest single error source
and is on the high end of typical adult-male anthropometrics; tightening
this could shift the dimensions down by ~13%.

## 2. Screen size, aspect ratio, resolution (DUAL-DISPLAY)

**Depends on:** #1 (provisionally known).

**Architectural decision:** the prop uses **two displays**, one per
inner cover, butted at the spine. See ADR-0005.

**Per-screen target (per dimensions-v1):** ~92 × 86 mm active area,
~1:1 aspect, matched panels.

**The sourcing problem:** no off-the-shelf hobbyist panel hits exactly
92 × 86 mm at a near-square aspect. Available options:

- **4" 480×480 square IPS** (Waveshare and similar): ~70 × 70 mm
  active. 24% smaller per side than the film-prop target. Matched
  pair available.
- **4" 720×720 round/square** (e.g., Waveshare, BTF-Lighting): ~72 × 72
  mm active. Same magnitude undersize; higher resolution.
- **3.5" 320×480 SPI LCD**: aspect is 3:2 not 1:1. Wrong shape.
- **5" 1080×1080 square IPS**: ~110 × 110 mm active. Too big — exceeds
  the 105 mm v1 cover-width.

**Two design paths to choose between:**

- **A.** Match panel to cover. Use a 4" 70 × 70 mm panel, accept wider
  matte than film-accurate. Closed prop stays at v1 dimensions.
- **B.** Match cover to panel. Pick the panel and shrink the closed
  prop dimensions so the screen-to-cover ratio matches film. Closed
  prop ends up smaller than film.

Open follow-up:

- Confirm the v1 cover-width estimate by cross-check (see #1) before
  picking A vs B.
- Resolve the bezel-measurement discrepancy (see dimensions-v1.md
  bezel-arithmetic section) — may inform how aggressively the matte
  needs to scale.

## 3. Compute platform

**Depends on:** #2.

**Question:** What drives **two** synchronized displays?

**Implications of the dual-display decision (ADR-0005):** Pi Zero 2 W
has only one HDMI output. To drive two panels from a single board,
options are:

- **Pi 4 / Pi 5 with dual micro-HDMI.** Both panels treated as full
  HDMI displays. Most ergonomic in software. Larger physical board than
  Zero 2 W.
- **Pi Zero 2 W + DPI display(s).** DPI uses GPIO pins directly to
  drive a parallel-RGB panel; can pair with the HDMI output for a
  second panel. Tight wiring, GPIO-pin-hungry.
- **Pi Zero 2 W + USB display adapter.** Lower performance, additional
  USB hub may be needed. Probably not viable for synchronized video.
- **Two ESP32-S3 + parallel TFT panels, sync'd over an internal bus.**
  Cheap, small, but writing synchronized video playback firmware is
  non-trivial.

**Tentative:** Raspberry Pi 4 with dual micro-HDMI. Trades some board
size for software simplicity.

## 4. Open-trigger mechanism

**Question:** How does the prop know it has been opened?

**Candidates:** Reed switch + magnet in cover, hinge potentiometer,
hall-effect sensor, tilt switch, hidden physical button in the spine.

**Tentative:** Reed switch — silent, no exposed contacts, easy to hide
inside the cover.

## 5. Audio path

**Question:** Internal speaker (which one, where mounted), Bluetooth out,
or 3.5 mm jack?

**Tentative:** Small internal speaker (mono, ≥ 2 W) with adequate volume
for room audio. No exposed jack, to preserve prop aesthetic.

## 6. Battery and charging

**Depends on:** #3, #5.

**Question:** Cell type, capacity, charging port location.

**Tentative:** LiPo with TP4056-class charge controller. USB-C charging
port hidden along the spine or under a removable panel.

## 7. Enclosure construction

**Depends on:** #1, #2, #3, #4, #5, #6.

**Question:** Fully 3D-printed shell, hollowed-out hardback book, or
hybrid (printed inner sled inside a leather-wrapped outer)?

**Tentative:** Hybrid. Printed structural inner sled holds electronics;
faux-leather outer with embossed "DON'T PANIC" sells the book illusion.

## 8. Content production pipeline

**Independent — can start in parallel with #1.**

**Question:** How are Guide entries produced?

**Plan:** Animate in After Effects or Blender, output at the combined
display resolution. **Per ADR-0005 (dual displays), the master must be
split into a left and right stream for synchronized playback.** Source
narration from a TTS Stephen Fry voice clone or record originally.
Track sources and rendered outputs in `software/content/`. Note:
rendered videos are gitignored — only the source project files are
versioned.

**Spine-seam treatment:** render content with a deliberate dark vertical
band at the seam line so the small physical gap between panels reads as
intentional framing rather than a hardware seam.
