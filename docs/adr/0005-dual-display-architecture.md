# ADR-0005: Use two displays, one per inner cover, instead of a single panel

- **Status:** Accepted
- **Date:** 2026-05-06

## Context

The on-screen Guide in the 2005 film, when opened, presents a single
wide image spanning the full inside of the clamshell. A prop replica
needs to reproduce that visual experience.

Two physical implementations are possible:

- **Single-panel.** One wide rectangular display mounted across both
  inner covers. Either rigidly bridges the spine (so the prop cannot
  fully close), or uses a flexible/foldable display (rare, expensive,
  and out of scope for a hobbyist build).
- **Dual-panel.** One display per inner cover, butted at the spine.
  Each panel renders one half of the on-screen image. The prop folds
  flat at the spine.

Dimensional analysis of frame `Screenshot 2026-05-06 at 1.53.21 PM.png`
(see `reference/dimensional-analysis/dimensions-v1.md`) shows that one
half of the film prop's visible display measures ~92 × 86 mm with a
near-square aspect ratio (~1.075:1). That is consistent with a
two-panel implementation in the original prop — and is the design
intended for this build regardless.

## Decision

Use **two displays**, one per inner cover, butted at the spine. Each
half of the rendered Guide content is sent to its own panel. The
content production pipeline (OPEN-QUESTIONS #8) renders to a
combined-resolution master, then splits the master into a left frame
and a right frame for playback.

## Consequences

Positive:

- The prop folds flat at the spine like the film prop and a real book.
  No mechanical compromise required.
- No flexible-display sourcing problem.
- Each panel is physically smaller and easier to mount within an
  inner-cover sled.
- Two independent panels are simpler to thermally manage and easier to
  service if one fails.
- Aligns with what the dimensional measurements show is the most
  likely film-prop construction (per-screen aspect ~1:1, not the
  ~2:1 combined visible).

Negative:

- **Sourcing.** Square-ish ~3.5–4" IPS panels with the right active
  area are an uncommon hobbyist part. Off-the-shelf 4" square panels
  are typically 70 × 70 mm active, smaller than the 92 × 86 mm target.
  Either accept wider matte than film-accurate, or scale the prop
  dimensions to match the chosen panels (see follow-up below).
- **Compute complexity.** Driving two displays from a single Pi-class
  board needs either two HDMI/DSI outputs (Pi 4/5 has two; Pi Zero 2 W
  has one), or one HDMI output + one DPI/SPI display, or a USB display
  adapter. Adds wiring and software complexity over a single panel.
- **Content pipeline.** Master video content must be authored at the
  combined resolution and split into two synchronized streams at
  playback. Frame-sync between the two panels matters for visible
  continuity at the seam.
- **Spine seam.** A small visible gap at the spine where the two
  panels meet. Mitigation: render content with a deliberate dark
  vertical band at the seam line so the gap reads as intentional
  framing rather than a hardware seam.

## Alternatives considered

- **Single panel bridging the spine.** Rejected — prop cannot close
  flat, defeating the clamshell illusion central to the prop's
  identity.
- **Flexible/foldable display.** Rejected — sourcing, cost, and
  reliability all unfavorable for a personal build.
- **One panel + decorative second cover with no display.** Rejected —
  only renders correctly from one side; the on-screen prop's content
  spans both halves, and the user explicitly wants both halves to be
  active.

## Follow-ups this triggers

- Update OPEN-QUESTIONS #2 to require **two** matched square-ish
  panels rather than one rectangular panel.
- Update OPEN-QUESTIONS #3: compute platform needs to drive two
  displays. Pi Zero 2 W has only one HDMI; either pair it with a DPI
  panel for the second screen, or step up to a Pi 4/5.
- Update OPEN-QUESTIONS #8: content pipeline must produce two
  synchronized output streams.
- New trade-off in dimensional design: either accept smaller-than-film
  screen-to-cover ratios (with wider matte) or scale the prop to fit
  available panels.
