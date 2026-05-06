# ADR-0003: Track compressed images in git, ignore video and audio

- **Status:** Accepted
- **Date:** 2026-05-06

## Context

The project includes hundreds of film screenshots already on disk plus
future video and audio assets for playback content. Git history bloats
fast with unversioned binaries.

Options considered:

- **A.** No git.
- **B.** Git everything.
- **C.** Git + `.gitignore` for large binaries.
- **D.** Git + git-lfs.

## Decision

Use git with extension-based `.gitignore`. Specifically:

- **Track:** `.jpg`, `.png`, `.webp`, `.svg`, `.pdf`, `.md`, code files,
  3D model sources, STL exports, schematics.
- **Ignore:** `.mp4`, `.mov`, `.avi`, `.mkv`, `.webm`, `.m4v`, `.wav`,
  `.mp3`, `.m4a`, `.flac`, `.ogg`, `.aac`, raw camera files
  (`.raw`, `.dng`, `.cr2`, `.nef`, `.arw`), slicer `.gcode`, and OS junk.

## Consequences

Positive:

- Screenshots and annotations stay versioned alongside the decisions they
  inform.
- Repo stays under ~1 GB even with hundreds of screenshots.
- No LFS dependency — easy to clone and back up.

Negative:

- Source video and audio aren't versioned. Mitigated by treating them as
  derivative outputs that can be re-rendered from project files (After
  Effects projects, Blender files, audio source projects — whichever
  toolchain ends up being used).

## Alternatives considered

- **A. No git.** Rejected — no history, no recovery from mistakes.
- **B. Git everything.** Rejected — multi-GB repos are painful to push,
  clone, and back up.
- **D. Git-lfs.** Rejected — LFS overhead and storage quotas don't pay
  off for a personal project that may never push to a remote.
