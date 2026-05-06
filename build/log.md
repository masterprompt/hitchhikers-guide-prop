# Build Log

A dated journal of work done on the prop. Newest entries on top.

---

## 2026-05-06 — Dual-display architecture decision and per-screen analysis

- Clarified design: prop uses **two displays**, one per inner cover,
  butted at the spine. Each renders one half of the on-screen image.
- This reconciles the previous aspect-ratio confusion: combined ~2:1
  visible display = two ~1:1 panels side-by-side.
- Per-screen target dimensions (using v1 cover-width scale):
  ~92 × 86 mm active area, near-square aspect.
- Wrote ADR-0005 capturing the dual-display rationale and consequences.
- Updated OPEN-QUESTIONS:
  - #2: now requires two matched square-ish panels; flagged the
    sourcing problem (no off-the-shelf hobbyist panel hits 92 × 86 mm
    at 1:1; available 4" square panels are ~70 × 70 mm).
  - #3: dual-display means Pi 4/5 with dual micro-HDMI is the new
    leading compute candidate (Zero 2 W only has one HDMI).
  - #8: content pipeline must split master into two synchronized
    streams; render with a dark vertical band at the seam.
- Updated CONTEXT.md scope and glossary to reflect dual-display.
- Open issue: bezel arithmetic in dimensions-v1 doesn't internally
  reconcile (screen + 2×side-bezel exceeds cover width by ~10 mm).
  Likely cause: side-bezel measurement is leather only, not full
  cover-edge-to-screen distance. Needs follow-up measurement clarifying
  which physical edge each measurement reaches.

## 2026-05-06 — Dimensional analysis v1 from single frame

- Source: `reference/screenshots/Screenshot 2026-05-06 at 1.53.15 PM.png`
  (Arthur Dent holding the Guide open).
- Reference: nose-to-chin = 180 px = 80 mm assumed.
- Computed closed-prop dimensions: ~152 × 105 × 32 mm
  (6.0 × 4.1 × 1.26 in), ± ~15% mostly from the nose-to-chin assumption.
- Detailed analysis: `reference/dimensional-analysis/dimensions-v1.md`.
- Major implication: 5" landscape display no longer fits the envelope.
  Updated leading candidate to 4" 800×480 IPS landscape. Captured in
  OPEN-QUESTIONS #2.
- OPEN-QUESTIONS #1 marked PROVISIONAL pending a cross-check against a
  second anatomical reference (hand or head width) or a more
  camera-perpendicular frame.

## 2026-05-06 — Researched: unmarked-raffle-on-personal-website scenario

- Question: would running a paid-entry raffle on the personal website,
  with the prop unnamed (just a video), avoid the IP issues?
- Answer: no, and it makes things worse.
  - State lottery law: individuals cannot run paid-entry raffles in any
    US state. Only registered 501(c)(3) nonprofits qualify (and 3 states
    ban raffles outright).
  - Copyright: hiding the name doesn't unrecognize the work; deliberate
    obscuration is read as bad faith.
  - Value proposition self-cancels: people only pay to enter because
    they recognize what it is, which is exactly the infringement.
- Cleaner alternatives: free sweepstakes with separate tip jar, or
  donate to a 501(c)(3) makerspace that already holds a raffle license.

## 2026-05-06 — Refined research: one-time prototype sale scenario

- Clarified intent: one-time build, publish plans for free, sell the
  single prototype.
- Conclusion unchanged for the prototype sale: still copyright
  infringement, no "first build" exception. Most likely real outcome:
  Etsy/eBay listing pulled before it sells.
- Free plan distribution is in a different bucket: technically
  derivative, but free fan-file distribution is essentially never
  pursued by rights holders. Existing CC BY-NC-SA 4.0 license is the
  right vehicle.
- Recommended disposal alternatives: gift, donate to fan raffle, or
  display indefinitely. Full updated analysis in the addendum to
  `docs/research/commercial-sale-feasibility.md`.

## 2026-05-06 — Researched commercial-sale feasibility

- Question: can the prop be sold on Etsy or eBay?
- Conclusion: no — copyright on the 2005 film's prop design and residual
  trademark/literary IP held by Disney and the Adams estate make it
  unsafe and unlawful, regardless of profit margin.
- Found that Disney's two USPTO trademarks for "Hitchhiker's Guide to
  the Galaxy" were abandoned in 2007, but copyright in the prop design
  is still in force and is the load-bearing risk. Trade dress and the
  Adams estate's marks add additional layers.
- Marketplace enforcement is fast: Disney files thousands of DMCAs per
  month; Etsy/eBay pull listings within hours.
- Practical alternatives written up in
  `docs/research/commercial-sale-feasibility.md`. Short version: build
  for self, document publicly, develop a separate original-design prop
  brand if commercial revenue is the goal.

## 2026-05-06 — License added for public GitHub release

- Repo will be published publicly on GitHub.
- Selected CC BY-NC-SA 4.0 — see ADR-0004 for rationale.
- GitHub repo-creation license picker doesn't include CC content
  licenses, so picker was set to "none" and the canonical license text
  is committed manually as `LICENSE`.
- Added `NOTICE.md` clarifying third-party IP boundaries and that the
  film and its characters/designs remain the property of their rights
  holders.
- Updated README with a License section.

## 2026-05-06 — Project bootstrapped

- Created directory structure under `~/Projects/Personal/hitchhikers-guide-prop/`.
- Decided Tier 2 (video playback with audio) — see ADR-0001.
- Decided domain-based directory layout — see ADR-0002.
- Decided git + extension-based `.gitignore` for binaries — see ADR-0003.
- Captured undecided work in `OPEN-QUESTIONS.md`.
- Next action: dimensional analysis of the on-screen prop from film
  screenshots — drop screenshots into `reference/screenshots/` and start
  measuring.
