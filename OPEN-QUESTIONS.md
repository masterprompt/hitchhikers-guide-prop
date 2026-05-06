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

## 2. Screen size, aspect ratio, resolution

**Depends on:** #1 (provisionally known).

**Question:** What display fits the inner upper panel with appropriate
bezel and matches the on-screen aspect ratio?

**Updated leading candidate (post v1 dimensions):** **4" 800×480 IPS in
landscape**. The earlier 5" recommendation no longer fits — a 5" panel's
~109 mm active width exceeds the ~95 mm usable interior face width
implied by the 105 mm cover dimension.

**Candidates ranked for the v1 envelope:**

- **4.0" 800×480 IPS (landscape, ~88 × 53 mm active)** — current leading
  candidate; comfortable fit with realistic bezel.
- 4.3" 800×480 IPS (landscape, ~95 × 54 mm active) — borderline; would
  need bezel tighter than the enclosure walls likely allow.
- 3.5" SPI LCD (480×320, ~75 × 55 mm active) — fits comfortably, but
  resolution is on the low side for video playback fidelity.
- 5" 800×480 IPS — no longer fits in landscape; only viable if dimensions
  are revised upward after cross-check.

**Re-confirm after** the v1 dimension error bar is reduced (see #1).

## 3. Compute platform

**Depends on:** #2.

**Question:** What drives the display?

**Candidates:** Raspberry Pi Zero 2 W, Pi 4/5, ESP32 + dedicated video
decoder, cheap dedicated MP4 player module.

**Tentative:** Pi Zero 2 W. Small, HDMI/DSI capable, well-supported, and
trivially handles 800×480 H.264 playback.

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

**Plan:** Animate in After Effects or Blender, output MP4 at the display's
native resolution. Source narration from a TTS Stephen Fry voice clone or
record originally. Track sources and rendered outputs in
`software/content/`. Note: rendered videos are gitignored — only the
source project files are versioned.
