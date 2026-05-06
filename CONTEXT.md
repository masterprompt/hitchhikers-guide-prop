# Context

## Vision

Build a hand-held replica of the Hitchhiker's Guide to the Galaxy device as
seen in the 2005 Garth Jennings film. The prop is a clamshell book that,
when opened, plays screen-accurate animated entries with synchronized audio,
recreating the visual moments where Arthur, Ford, or Trillian consult the
Guide.

## Scope (Tier 2 — Video Playback Prop)

In scope:

- Clamshell book enclosure that opens like the on-screen prop.
- **Two embedded displays**, one per inner cover, butted at the spine
  to render a single visible image when open. See ADR-0005.
- Speaker for synchronized audio.
- Plays pre-rendered video files of Guide entries.
- Triggered on open (mechanism TBD — likely reed switch).
- Battery powered with hidden charging port.

Out of scope (for now):

- Interactive navigation between entries (Tier 3).
- Voice activation, LLM-generated entries (Tier 4).
- Functional tactile keypad on the lower inner panel.

## Source material

The 2005 film "The Hitchhiker's Guide to the Galaxy" is the canonical visual
reference. Screenshots captured from the film live in
`reference/screenshots/`. The 1981 BBC TV series Guide is intentionally
**not** the reference — its visual design is materially different.

## Glossary

- **The Guide / the prop / the book** — the device being built.
- **Entry** — an animated segment narrated by Stephen Fry in the film
  (e.g., the Babel Fish entry, the Vogon entry, the Pan Galactic Gargle
  Blaster entry).
- **Tier** — the functional level of the prop. We are building Tier 2
  (see ADR-0001).
- **Inner panel(s)** — the inside faces of the two clamshell halves
  when opened. Each hosts one of the two displays.
- **Spine seam** — the small physical gap between the two panels where
  they meet at the spine. Visually disguised in content rendering with
  a deliberate dark vertical band at the seam line.
- **Cover / spine / outer shell** — the outer physical shell of the book.

## Build philosophy

Screen accuracy first, ergonomics second, expandability third. The prop
should look right in hand and on camera before optimizing for things like
extended battery life or modular content swapping. If a choice trades
fidelity for engineering elegance, fidelity wins.
