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

## 2. Screen size, aspect ratio, resolution (RESOLVED)

**Resolved by:** ADR-0006 — two 4" 720×720 IPS MIPI panels with
bundled HDMI controller boards (FanyiTek or equivalent). Selected
primarily on power-budget grounds (3.3 V panel / 5 V via USB on the
controller; no 12 V boost or multi-cell battery needed).

**Consequence:** closed prop scales down to ~127 × 82 × 28 mm — see
[`reference/dimensional-analysis/dimensions-v2.md`](reference/dimensional-analysis/dimensions-v2.md).

## 3. Compute platform (NEEDS RE-EVALUATION POST-V2)

**Depends on:** #2 (resolved per ADR-0006).

**Question:** What drives the two HDMI inputs (one per panel
controller board)?

**Sub-issue surfaced in v2 dimensions:** with the prop scaled down to
~28 mm closed thickness, internal volume per half is ~10 mm deep. A
Pi 4 (17 mm thick) does not fit in one half. Three paths:

- **Pi 4 / Pi 5 with thicker prop.** Increase closed thickness to
  ~32–35 mm to accommodate Pi 4 in the lower half. Loses some prop
  fidelity; simplest electronically.
- **Pi Compute Module 4 on custom thin carrier.** CM4 is 55 × 40 ×
  4.7 mm and fits comfortably. Carrier board would expose dual HDMI.
  Most custom and expensive; thinnest result.
- **Pi Zero 2 W + per-panel HDMI-to-MIPI bridge boards.** Pi Zero 2 W
  is 5 mm thick. Only one HDMI on the Zero, so the second panel needs
  to be driven from GPIO (DPI / SPI) instead — adds wiring complexity
  and may push to a Pi Zero 2 W with a custom HAT. Cheap but more
  bespoke.

**Tentative:** Pi 4 with dual micro-HDMI, prop thickness allowed to
grow to ~32 mm if needed. Validate during CAD layout.

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

**Tentative (post-ADR-0006):** **single-cell LiPo + 5 V boost regulator**
+ TP4056-class charge controller. The 4" panel kits run from 5 V via
micro-USB on the controller boards, so a single-cell cell + boost is
the cleanest path. No multi-cell pack needed. USB-C charging port
hidden along the spine or under a removable panel.

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
