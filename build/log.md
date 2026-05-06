# Build Log

A dated journal of work done on the prop. Newest entries on top.

---

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
