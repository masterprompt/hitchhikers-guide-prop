# ADR-0004: License the project under CC BY-NC-SA 4.0

- **Status:** Accepted
- **Date:** 2026-05-06

## Context

The repository will be hosted publicly on GitHub. The project is a fan
prop replicating the visual design of a copyrighted film, mixing several
content types: written analysis, ADRs, software code, 3D model sources
and STL exports, schematics, photographs.

A license needs to:

- Permit non-commercial sharing and remixing in the maker-community
  tradition.
- Discourage anyone from selling kits or prints derived from this work,
  which would be legally risky for them and could implicate the project
  in commercializing third-party IP.
- Cover mixed content (code + prose + 3D models + images), not just
  software.
- Require attribution.
- Prevent proprietary forks (share-alike).

GitHub's repository-creation license dropdown only lists OSI-approved
software licenses plus CC0. Creative Commons content licenses
(CC BY-NC-SA, CC BY-SA, CC BY) are not in the picker.

## Decision

License the project under
**Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
(CC BY-NC-SA 4.0)**.

The canonical legal text from
`https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode.txt`
is committed verbatim as the repository's `LICENSE` file.

A separate `NOTICE.md` clarifies:

- The license covers only original work in this repository.
- The film's IP, the *Hitchhiker's Guide* name, characters, and trade
  dress remain the property of their respective rights holders.
- Frame captures from the film, where present, are included for
  analysis/commentary under fair use and are not covered by the project
  license.

GitHub's repository creation flow is set to "no license"; the `LICENSE`
file is added manually after the repo is created. GitHub's licensee
detector reads the file and labels the repository correctly.

## Consequences

Positive:

- Same license covers code, prose, 3D models, and images — no need to
  partition the repo.
- Non-commercial term aligns with the fan-work nature of the project and
  reduces legal exposure.
- Share-alike preserves the open-source spirit of any derivative works.
- Attribution requirement matches maker-community norms (Thingiverse /
  Printables / Hackaday).

Negative:

- CC BY-NC-SA is not OSI-approved and is generally considered unsuitable
  for "real" software libraries. The video-playback code in this repo is
  prop-specific and unlikely to be useful as a standalone library, so
  this is acceptable. If portions of the code later prove generally
  useful, they can be extracted to a separate repository under MIT.
- The "NonCommercial" boundary is fuzzy in edge cases (e.g., a maker
  charges materials cost for a friend's print). The intent — no kit
  manufacturing or commercial sale — is documented in NOTICE.md.

## Alternatives considered

- **MIT / Apache 2.0 / BSD.** Rejected — permissive software licenses
  don't restrict commercial use, and the repo's primary content is not
  software.
- **GPL v3.** Rejected — copyleft is a fit, but GPL is awkward for 3D
  models and prose, and doesn't restrict commercial use.
- **CC0.** Rejected — wrong direction; abandons attribution and
  non-commercial intent.
- **CC BY-SA 4.0** (no NC). Rejected — would permit someone to sell
  printed kits derived from this work, which we want to discourage.
- **Dual license: MIT for `software/`, CC BY-NC-SA 4.0 for everything
  else.** Deferred — adds repo-management overhead. Revisit if any code
  matures into a generally useful library.
