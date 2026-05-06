# Hitchhiker's Guide to the Galaxy — Prop Build

A working replica of the Guide from the 2005 Garth Jennings film. The prop
is a clamshell book that, when opened, plays screen-accurate animated
entries with synchronized audio.

## Status

**Phase 0** — project bootstrapped. Awaiting dimensional analysis from film
screenshots before hardware decisions can be made.

## Next action

See [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md). The blocking item is
estimating the on-screen prop's dimensions from screenshots, which gates
screen selection, which gates everything else physical.

## Layout

| Path | What lives here |
|---|---|
| `reference/` | Film screenshots, annotated measurements, dimensional analysis |
| `hardware/electronics/` | Component research, BOM, schematics, datasheets |
| `hardware/enclosure/` | 3D model sources, STL exports, renders |
| `software/playback/` | Video player code (Pi-side) |
| `software/content/` | Source animation files and rendering scripts |
| `build/log.md` | Dated build journal |
| `build/photos/` | Build progress photos |
| `docs/adr/` | Architecture Decision Records — one decision per file |
| `CONTEXT.md` | Vision, scope, glossary |
| `OPEN-QUESTIONS.md` | Undecided items, in dependency order |

## Conventions

- Decisions go in `docs/adr/` as numbered ADRs. Don't bury them in code or
  in README.
- Open work goes in `OPEN-QUESTIONS.md`, not as commented-out code or scattered
  TODOs.
- Build log entries are dated and prepended (newest at top).
- Compressed images (JPG/PNG/WebP) are tracked in git. Video, audio, and
  raw camera files are not — see ADR-0003.

## License

This project's original work — written analysis, decision records, 3D
models, schematics, software, and build photographs — is licensed under
the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0
International** license. See [`LICENSE`](LICENSE) for the full text and
[`NOTICE.md`](NOTICE.md) for the third-party-IP statement and the
boundaries of what the license does and does not cover. See ADR-0004 for
the rationale.

This is a non-commercial fan project. The Hitchhiker's Guide to the
Galaxy and all related characters, designs, and trade dress are the
property of their respective rights holders.
