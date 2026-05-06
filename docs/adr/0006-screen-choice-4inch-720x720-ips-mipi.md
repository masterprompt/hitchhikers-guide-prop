# ADR-0006: Use two 4" 720×720 IPS MIPI panels for the displays

- **Status:** Accepted
- **Date:** 2026-05-06

## Context

ADR-0005 committed the prop to a dual-display architecture (one panel
per inner cover, butted at the spine). That triggered a screen-sourcing
question (OPEN-QUESTIONS #2): what matched-pair square-ish IPS panel
fits the per-half target of ~92 × 86 mm derived from
`reference/dimensional-analysis/dimensions-v1.md`?

Survey of available hobbyist options:

| Option | Active area | Voltage | Notes |
|---|---|---|---|
| 4" 720×720 IPS MIPI | ~72 × 72 mm | 3.3 V (panel) / 5 V (kit via USB) | Square; matched pairs available; FanyiTek/CDTech/YOURITECH sources |
| 4" 480×480 IPS RGB | ~72 × 72 mm | 3.3 V | Lower res; cheaper; bare panel |
| 5" round 1080×1080 IPS HDMI | 127 mm Ø; 90 × 90 mm inscribed | 5 V | Round visible area; would crop content |
| 7" round 1080×1080 IPS HDMI | 178 mm Ø; 126 × 126 mm inscribed | 5 V | Round; large; doubles prop size |
| 7" 720×720 / 768×768 LVDS true square | 126 × 126 mm | 5–12 V + LVDS bridge | True square; needs LVDS-to-HDMI bridge per panel; industrial sourcing |
| 7" 800×600 4:3 TFT (CLAA070MA0ACW) | 141.6 × 106.2 mm | **12 V** | TN not IPS; aspect wrong for dual-screen architecture |
| 6" / 5.5" / 6.5" square IPS | — | — | Effectively absent from hobbyist supply |

Power budget is the deciding factor. The prop's enclosure is ~28 mm
closed thickness, split across two halves. A 12 V panel forces either
a 3S LiPo (bulky) or a boost converter from a single-cell LiPo (heat
and component count). A 3.3 V / 5 V panel runs directly from a
single-cell LiPo with a small step-up regulator.

Among 3.3–5 V options, the 4" 720×720 IPS MIPI is the only matched-pair
*genuinely-square* panel widely available at hobbyist retail.

## Decision

Use **two 4" 720×720 IPS MIPI panels** with the bundled HDMI controller
boards. Reference part: FanyiTek 4" 720×720 300nit IPS MIPI LCD Square
Capacitive Touch Screen with controller board (Amazon B0DWMQ6N27).
Equivalents from CDTech and YOURITECH are acceptable substitutes if the
FanyiTek SKU goes out of stock.

Each panel's controller board takes HDMI in, runs from 5 V via micro-USB,
and drives the panel's MIPI DSI input. Two panels = two HDMI inputs,
matching a Pi 4 / Pi 5's dual micro-HDMI outputs.

Capacitive touch is included in the panel and retained in the build —
unused for current Tier 2 scope, available for a future Tier 3 upgrade
without rework.

## Consequences

Positive:

- **Power.** Single-cell LiPo + a small 5 V boost regulator drives both
  panels. No multi-cell battery pack, no high-current 12 V boost.
- **Thermal.** Lower current draw, less waste heat in a tight
  enclosure.
- **Cost.** ~$30–50 per panel kit; total screen budget under $100.
- **Software.** Each panel is HDMI from the Pi's perspective. Standard
  graphics stack works without custom drivers.
- **Future-proof.** Capacitive touch hardware is in place for Tier 3
  upgrades.

Negative:

- **Prop scales down.** The 72 × 72 mm active area is smaller than the
  film-prop per-screen target of 92 × 86 mm. Maintaining the film prop's
  screen-to-cover proportions forces the closed prop to shrink to roughly
  **127 × 82 × 28 mm** — pocket-paperback size, smaller than the
  estimated film-accurate ~152 × 105 × 32 mm. See `dimensions-v2.md`.
- **Resolution.** 720×720 per panel is plenty for handheld video at
  this size, but is lower than the 1080×1080 round options.
- **Spine seam.** Two panels still leave a small physical gap at the
  spine. Mitigation per ADR-0005: render content with a deliberate dark
  vertical band at the seam.

## Alternatives considered

- **5" round 1080×1080 IPS HDMI.** Would have preserved film-accurate
  prop dimensions (90 × 90 mm inscribed square ≈ target). Rejected —
  round visible area departs from the rectangular-screen aesthetic of
  the film prop, and 5 V boost is the same cost as 4" anyway with no
  fidelity benefit.
- **7" round 1080×1080 IPS HDMI.** Inscribed square 126 × 126 mm gives
  true scale-up. Rejected — doubles prop size to ~222 × 144 mm, prop
  no longer reads as paperback-class. Round shape same fidelity issue.
- **7" 800×600 4:3 TFT (CLAA070MA0ACW).** Rejected — 12 V power, TN
  panel viewing angles, single panel conflicts with ADR-0005 dual
  architecture.
- **7" true-square LVDS panels.** Rejected — needs an LVDS-to-HDMI
  bridge board per panel, industrial sourcing, doubled wiring effort
  for the same outcome as the 7" round option (which is itself
  rejected on size).
- **Roll-your-own bare 4" 720×720 RGB panel without bundled controller.**
  Deferred — possible Phase 2 cost optimization once the build is
  proven, but for a first build the bundled HDMI controller board is
  worth the markup.

## Follow-ups this triggers

- Update OPEN-QUESTIONS #2: mark resolved.
- Update OPEN-QUESTIONS #3: Pi 4 / Pi 5 with dual micro-HDMI confirmed
  as compute. Each panel kit takes HDMI input.
- Add `reference/dimensional-analysis/dimensions-v2.md` with the
  scaled-down prop dimensions.
- Update CONTEXT.md scope to reflect pocket-paperback class prop.
- New consideration for OPEN-QUESTIONS #6 (battery): single-cell LiPo
  + 5 V boost is now the default architecture.
