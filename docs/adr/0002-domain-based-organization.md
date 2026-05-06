# ADR-0002: Organize the project directory by domain, not by phase

- **Status:** Accepted
- **Date:** 2026-05-06

## Context

A prop build naturally has several work streams: reference research,
electronics, 3D enclosure design, software, and physical assembly. Two
ways to lay out the project directory:

- **Phase-based.** Top-level dirs `01-research/`, `02-design/`,
  `03-build/`, `04-test/`. Reflects chronology.
- **Domain-based.** Top-level dirs by subject matter: `reference/`,
  `hardware/`, `software/`, `build/`, `docs/`.

## Decision

Use domain-based organization with the following layout:

```
hitchhikers-guide-prop/
├── README.md
├── CONTEXT.md
├── OPEN-QUESTIONS.md
├── reference/
│   ├── screenshots/
│   ├── annotated/
│   └── dimensional-analysis/
├── hardware/
│   ├── electronics/
│   └── enclosure/
├── software/
│   ├── playback/
│   └── content/
├── build/
│   ├── log.md
│   └── photos/
└── docs/
    └── adr/
```

## Consequences

Positive:

- Files live where the user's mental model puts them when searching
  ("where's the battery datasheet?" → `hardware/electronics/`).
- Iterative work doesn't fight the structure. Re-measuring screenshots
  in month six doesn't require deciding whether that's "research" or
  "build."
- Matches the user's existing project conventions (CONTEXT.md and
  `docs/adr/` at the root).

Negative:

- Less obvious "what stage is this project in?" at a glance. Mitigated by
  the README status line and `OPEN-QUESTIONS.md`.

## Alternatives considered

- **Phase-based.** Rejected — prop builds aren't linear; phase folders
  rot when work loops back, which it always does.
