# ADR-0001: Build a Tier 2 video-playback prop

- **Status:** Accepted
- **Date:** 2026-05-06

## Context

A "working" Hitchhiker's Guide replica can mean many things — from a
backlit static "DON'T PANIC" sign to a fully voice-activated AI assistant.
Each level dictates a different display, compute, audio, and battery
envelope, so this is a keystone decision.

Four tiers were considered:

- **Tier 1.** Static screen showing a single looping image.
- **Tier 2.** Pre-rendered video files play with synchronized audio.
  No interactive navigation.
- **Tier 3.** Multiple entries, navigation buttons, a real menu UI.
- **Tier 4.** Voice activation and LLM-generated entries.

## Decision

Build a Tier 2 prop. Animated content is produced as standard video files
(MP4 or equivalent). The device plays them back with audio. Trigger and
looping behavior are TBD but the device is fundamentally "a video player
in book clothing."

## Consequences

Positive:

- Content production becomes a creative exercise rather than a software
  problem. No content management UI to design.
- Hardware envelope is well understood (display + Pi-class compute +
  speaker + battery).
- Screen accuracy is achievable because the user controls the rendered
  output frame-by-frame.

Negative:

- No on-the-fly interactivity. Entry order is whatever the playlist says.
- Adding Tier 3 features later (buttons, menu) may affect enclosure
  dimensions if not planned for. Mitigation: leave a small unused volume
  inside the lower panel envelope for future hardware.

## Alternatives considered

- **Tier 1.** Rejected — too low-fidelity; fails the "looks like the prop
  is doing something" test.
- **Tier 3.** Deferred — possible Phase 2 once Tier 2 is solid; would
  require a content management layer and physical buttons.
- **Tier 4.** Rejected for now — adds wake-word engine, microphone array,
  and an entirely different UX surface. Out of scope.
