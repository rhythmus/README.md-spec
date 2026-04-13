# Repository README Specification (RRS)

[![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/) [![readme-rfc-validator on npm](https://img.shields.io/npm/v/readme-rfc-validator?label=validator&color=cb3837&logo=npm)](https://www.npmjs.com/package/readme-rfc-validator)

A formal, machine-checkable specification that defines what a well-structured `README.md` must contain, how it must be organized, and what quality thresholds it must meet — for any software repository, from weekend projects to critical infrastructure. A free CLI tool, [`readme-rfc-validator`](https://www.npmjs.com/package/readme-rfc-validator), is available to run validation checks on your own local machine.

```markdown
# My Project

A tool that does X for Y, so they can Z.        ← Summary (§3.2.2)

## Installation                                  ← Required section (§3.2.4)
## Quickstart                                    ← Required section (§3.2.5)
## Usage                                         ← Required section (§3.2.6)
## Documentation                                 ← Required section (§3.2.7)
## Support                                       ← Required section (§3.2.8)
## Contact                                       ← Required section (§3.2.10)
## License                                       ← Required section (§3.2.11)
```

## Summary

The **Repository README Specification** (RRS) is a normative document that codifies best practices for repository-level `README.md` files. It was developed by studying documentation patterns across thousands of open-source projects — identifying what the best READMEs have in common, and what the worst ones consistently lack. The result is a single, versioned reference that maintainers can adopt to ensure their project's front door is never the reason people walk away. To check compliance instantly, run the free reference validator on any repository: `npx readme-rfc-validator check .`

## Why

README files are the most-read document in any repository, yet most are written ad hoc, without structure, and drift out of date. There is no widely adopted standard for what a README must include. The RRS fills that gap by defining required sections, recommended sections, ordering rules, formatting constraints, accessibility requirements, and quality metrics — all in a single, versionable specification.

## Features

- **Normative section taxonomy** — required, recommended, and optional sections with canonical heading names and ordering rules
- **Readability targets** — Flesch-Kincaid, Gunning Fog, and Dale-Chall thresholds for clear prose
- **Accessibility requirements** — alt text rules, decorative image detection, and screen-reader considerations
- **Formatting constraints** — badge limits, emoji usage, code block sizing, and heading-level rules
- **Compliance levels** — none, minimal, recommended, and strict tiers with clear promotion criteria
- **Scoring model** — weighted 100-point scale across structural, ordering, formatting, accessibility, repository, heuristic, and link categories
- **Machine-checkable** — every normative rule is expressed precisely enough for automated validation

## Project Status

Stable — v1.0.0. The specification is versioned and follows semantic versioning. Amendments are tracked in the specification document itself. A reference validator is published as [`readme-rfc-validator`](https://www.npmjs.com/package/readme-rfc-validator) on npm.

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
npx readme-rfc-validator check .
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
3. Run the [reference validator](https://www.npmjs.com/package/readme-rfc-validator) to check compliance.
4. Address diagnostics iteratively until you reach your target compliance level.

### Compliance Levels

| Level | Requirements |
| --- | --- |
| **none** | One or more errors present |
| **minimal** | Zero errors; title, summary, and license present |
| **recommended** | Zero errors; all required sections present with quality thresholds met |
| **strict** | Zero errors; zero warnings; all rules passing |

### Specification Structure

| Part | Contents |
| --- | --- |
| Part 1 | Scope, purpose, and audience |
| Part 2 | Conformance language (RFC 2119) |
| Part 3 | Document structure (sections, ordering, content rules) |
| Part 4 | Content quality (readability, language, length) |
| Part 5 | Formatting (badges, emoji, code, accessibility) |
| Part 6 | Repository integration (LICENSE, CONTRIBUTING, CHANGELOG) |
| Appendix A | Section taxonomy and heading aliases |
| Appendix B | Scoring model and category weights |
| Appendix C | Validator architecture and rule engine |

## Documentation

- [README Specification.md](README%20Specification.md) — the full normative specification
- [readme-rfc-validator](https://www.npmjs.com/package/readme-rfc-validator) — the reference CLI validator
- [RRS Validator Playground](https://github.com/rhythmus/Repose) — interactive web-based validation

## Limitations

- The specification targets Markdown-formatted README files only. reStructuredText, AsciiDoc, and plain text READMEs are out of scope.
- Section detection relies on heading text matching against canonical names. Projects with unconventional heading names may need to configure aliases.
- Readability metrics are calibrated for English prose. Non-English READMEs may score differently on Flesch-Kincaid and Gunning Fog measures.
- The specification is not an IETF RFC, ISO standard, or W3C recommendation. It is a community-driven, versioned document.

## Support

- Open an issue in the [specification repository](https://github.com/rhythmus/README.md-spec/issues) for errata, clarifications, or proposed amendments.
- Open an issue in the [validator repository](https://github.com/rhythmus/Repose/issues) for bugs and feature requests related to the reference implementation.

## Prior Art

The RRS was informed by patterns and conventions observed across the open-source ecosystem:

- [standard-readme](https://github.com/RichardLitt/standard-readme) — a widely cited README layout and checklist for npm-style projects; conceptually overlapping with the RRS required-section taxonomy but without the same formal compliance levels and scoring model.
- [Make a README](https://www.makeareadme.com/) — a community guide for writing READMEs; provides informal advice where the RRS provides normative, machine-checkable rules.
- [GitHub community health files](https://docs.github.com/en/communities) — platform-level guidance on README presence and community documents; complementary to, but less prescriptive than, the RRS.

## Contributing

Contributions are welcome. The specification evolves through a structured amendment process:

1. Open an issue describing the proposed change and its rationale.
2. Reference the relevant specification section number (e.g. "Amend section 3.2.4 to allow...").
3. If accepted, submit a pull request against `README Specification.md`.

All amendments must preserve backward compatibility with the current compliance levels unless a major version bump is explicitly agreed.

## Acknowledgements

Many thanks to every maintainer who writes clear documentation and every user who files an issue when something is missing.

## Contact

- **Author:** [Dr Wouter Soudan](https://github.com/rhythmus)

## License

This specification is licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/). See [LICENSE](LICENSE) for the full text.
