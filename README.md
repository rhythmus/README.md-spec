# README.md Specification

[![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/) [![@rhythmus/readme-validator on npm](https://img.shields.io/npm/v/@rhythmus/readme-validator?label=validator&color=cb3837&logo=npm)](https://www.npmjs.com/package/@rhythmus/readme-validator) [![Sponsor](https://img.shields.io/badge/sponsor-%E2%9D%A4-pink?logo=github)](https://github.com/sponsors/rhythmus)

A formal, machine-checkable specification that defines what a well-structured `README.md` must contain, how it must be organized, and what quality thresholds it must meet — for any software repository, from weekend projects to critical infrastructure. A **free CLI** tool, [`@rhythmus/readme-validator`](https://www.npmjs.com/package/@rhythmus/readme-validator), is available to run validation checks on your own local machine.

```markdown
#            Repository README.md Specification (Version 0.1.0)

   Independent Submission                                        W. Soudan
   Request for Comments: —                                     Independent
   Category: Informational                                   14 April 2026

## Abstract

   This document specifies version 0.1.0 of the Repository README.md
   Specification. It specifies the structure, content, and presentation
   of repository README files, with integrated validation schema and
   tooling blueprints.

## Status of This Memo

   This is an Independent Submission for the RFC Series. It represents
   the consensus of the opensource community. It does not deliver
   an Internet Standards Track specification; it is published for
   informational purposes.

## Copyright Notice

   Copyright (c) 2026 Dr Wouter Soudan.  All rights reserved.

```

## Summary

The **README.md Specification** is a normative document that codifies best practices for repository-level `README.md` files. Based on extensive research into documentation standards across thousands of open-source repositories — from one-person weekend projects to critical infrastructure maintained by hundreds of contributors — the Repository README Specification codifies what the best READMEs have in common and what the worst ones consistently lack. The result is a single, versioned reference that maintainers can adopt to ensure their project's front door is never the reason people walk away. This repository contains the README.md Specification, and a reference implementation **[@rhythmus/readme-validator](https://www.npmjs.com/package/@rhythmus/readme-validator)** CLI tool.

## Why

README files are the most-read document in any repository, yet most are written ad hoc, without structure, and drift out of date. They drift out of date, omit critical sections, bury prerequisites, and fail to orient newcomers. There is no widely adopted standard for what a README must include. The [README.md Specification](README%20Specification.md) fills that gap by defining required sections, recommended sections, ordering rules, formatting constraints, accessibility requirements, and quality metrics — all in a single, versionable specification. The [**free validator CLI**](https://www.npmjs.com/package/@rhythmus/readme-validator) enforces it — automatically, reproducibly, and at any strictness level you choose: point it at any README.md and get instant, actionable feedback on structure, completeness, ordering, accessibility, and compliance.

## Features

- **Normative section taxonomy** — required, recommended, and optional sections with canonical heading names and ordering rules
- **Readability targets** — Flesch-Kincaid, Gunning Fog, and Dale-Chall thresholds for clear prose
- **Accessibility requirements** — alt text rules, decorative image detection, and screen-reader considerations
- **Formatting constraints** — badge limits, emoji usage, code block sizing, and heading-level rules
- **Compliance levels** — none, minimal, recommended, and strict tiers with clear promotion criteria
- **Scoring model** — weighted 100-point scale across structural, ordering, formatting, accessibility, repository, heuristic, and link categories
- **Machine-checkable** — every normative rule is expressed precisely enough for automated validation

## Project Status

Stable — v1.0.0. The specification is versioned and follows semantic versioning. Amendments are tracked in the specification document itself. A reference validator is published as [`@rhythmus/readme-validator`](https://www.npmjs.com/package/@rhythmus/readme-validator) on npm.

## Installation

No installation is required. The specification is a single Markdown document:

```bash
curl -O https://raw.githubusercontent.com/rhythmus/README.md-spec/main/README%20Specification.md
```

Or clone the repository:

```bash
git clone https://github.com/rhythmus/README.md-spec.git
```

## Quickstart

Read the specification document, then validate your own README against it using the reference validator:

```bash
npx @rhythmus/readme-validator check .
```

Expected output for a compliant repository:

```text
README validation passed

Compliance level: recommended
Score: 97
Errors: 0
Warnings: 2
```

## Usage

### Adopting the Specification

1. Read [README Specification.md](README%20Specification.md) to understand the structural and quality requirements.
2. Structure your `README.md` to include the required sections defined in Part 3 of the specification.
3. Run the [reference validator](https://www.npmjs.com/package/@rhythmus/readme-validator) to check compliance.
4. Address diagnostics iteratively until you reach your target compliance level.

### Compliance Levels

| Level | Requirements |
| --- | --- |
| **none** | One or more errors present |
| **minimal** | Zero errors; title, summary, and license present |
| **recommended** | Zero errors; all required sections present with quality thresholds met |
| **strict** | Zero errors; zero warnings; all rules passing |

## Documentation

- [README Specification.md](README%20Specification.md) — the full normative specification
- [readme-validator](https://www.npmjs.com/package/@rhythmus/readme-validator) — the reference CLI validator
- [README.md Validator Playground](https://rhythmus.github.io/README.md-spec/) — interactive web-based validation

## Limitations

- The specification targets Markdown-formatted `README.md` files only. reStructuredText, AsciiDoc, and plain text READMEs are out of scope.
- Section detection relies on heading text matching against canonical names. Projects with unconventional heading names may need to configure aliases.
- Readability metrics are calibrated for English prose. Non-English READMEs may score differently on Flesch-Kincaid and Gunning Fog measures.
- The specification is not an IETF RFC, ISO standard, or W3C recommendation. It is a community-driven, versioned document.

## Support

Open an issue in the [specification repository](https://github.com/rhythmus/README.md-spec/issues) for errata, clarifications, or proposed amendments.

## Prior Art

The RRS was informed by patterns and conventions observed across the open-source ecosystem:

- [standard-readme](https://github.com/RichardLitt/standard-readme) — a widely cited README layout and checklist for npm-style projects; conceptually overlapping with the RRS required-section taxonomy but without the same formal compliance levels and scoring model.
- [Make a README](https://www.makeareadme.com/) — a community guide for writing READMEs; provides informal advice where the RRS provides normative, machine-checkable rules.
- [GitHub community health files](https://docs.github.com/en/communities) — platform-level guidance on README presence and community documents; complementary to, but less prescriptive than, the RRS.
- [GitHub Docs Style Guide](https://docs.github.com/en/contributing/style-guide-and-content-model/style-guide) — the authoritative source for GitHub's technical documentation standards; informs the RRS formatting, accessibility, and writing style requirements.
- [SPDX License List](https://spdx.org/licenses/) — the foundational standard for machine-readable license identifiers, providing the normative vocabulary for the RRS License section.

## Contributing

Contributions are welcome. The specification evolves through a structured amendment process:

1. Open an issue describing the proposed change and its rationale.
2. Reference the relevant specification section number (e.g. "Amend section 3.2.4 to allow...").
3. If accepted, submit a pull request against `README Specification.md`.

All amendments must preserve backward compatibility with the current compliance levels unless a major version bump is explicitly agreed.

## Acknowledgements

A.M.D.G. — Δόξα τω Θεώ!

In loving memory of my father, Karel Soudan. Αιωνία η μνήμη! — 14 April 1951

Many thanks to every maintainer who writes clear documentation and every user who files an issue when something is missing.

If you find this specification useful, consider [sponsoring its maintenance](https://github.com/sponsors/rhythmus).

## Contact

- **Author:** [Dr Wouter Soudan](https://github.com/rhythmus)

## Citation

If you reference or build upon this specification, please cite it:

```bibtex
@misc{soudan2026rrs,
  author       = {Soudan, Wouter},
  title        = {Repository README Specification (RRS)},
  year         = {2026},
  url          = {https://github.com/rhythmus/README.md-spec},
  version      = {1.0.0},
  license      = {CC-BY-SA-4.0}
}
```

Machine-readable citation metadata is available in [CITATION.cff](CITATION.cff).

## License

This specification is licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/). See [LICENSE](LICENSE) for the full text.
