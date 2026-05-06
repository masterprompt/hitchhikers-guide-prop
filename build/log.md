# Build Log

A dated journal of work done on the prop. Newest entries on top.

---

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
