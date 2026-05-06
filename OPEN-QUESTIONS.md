# Open Questions

Items needing decisions, in roughly dependency order. Each blocks the next
unless noted. Move resolved items into a new ADR under `docs/adr/` and
remove them from this list.

---

## 1. Prop dimensions (BLOCKS everything physical)

**Question:** What are the closed and open dimensions of the on-screen
prop?

**Method:**

- Pick screenshots in `reference/screenshots/` where the prop is held by
  an actor (Arthur, Ford, or Trillian) in roughly the camera plane.
- Measure pixel dimensions of the prop and a known anatomical reference
  (adult male hand width ≈ 8.5 cm; head height ≈ 22 cm).
- Estimate prop dimensions in cm. Cross-check across multiple frames and
  angles to bound the error.
- Document findings in `reference/dimensional-analysis/` with the source
  screenshots annotated under `reference/annotated/`.

**Output:** Closed dimensions (height × width × thickness), open dimensions
including hinge geometry, and an error bar on each.

## 2. Screen size, aspect ratio, resolution

**Depends on:** #1.

**Question:** What display fits the inner upper panel with appropriate
bezel and matches the on-screen aspect ratio?

**Candidates to evaluate once #1 is known:**

- 3.5" SPI LCD (480×320, 3:2)
- 4" round/square IPS (~720×720, 1:1)
- 5" HDMI/DSI IPS (800×480, 5:3) — current leading candidate
- 7" HDMI IPS (1024×600, ~16:9)

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
