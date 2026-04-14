---
first published: 2026-04-13
last updated: 2026-04-14T15:39:38Z
version: 0.1.0
---

#            Repository README.md Specification (Version 0.1.0)

```text
   Independent Submission                                        W. Soudan
   Request for Comments: —                                     Independent
   Category: Informational                                   14 April 2026
```

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

## Table of Contents

- [0. Front Matter](#0-front-matter)
    - [0.1 Document Metadata](#01-document-metadata)
        - [0.1.1 Title and Subtitle](#011-title-and-subtitle)
        - [0.1.2 Authors and Contributors](#012-authors-and-contributors)
        - [0.1.3 Versioning Scheme](#013-versioning-scheme)
        - [0.1.4 Status (Draft, Proposed, Final)](#014-status-draft-proposed-final)
        - [0.1.5 Date of Publication](#015-date-of-publication)
        - [0.1.6 License of the Specification](#016-license-of-the-specification)
    - [0.2 Abstract](#02-abstract)
        - [0.2.1 Purpose of the Specification](#021-purpose-of-the-specification)
        - [0.2.2 Scope of Applicability](#022-scope-of-applicability)
        - [0.2.3 Non-goals](#023-non-goals)
    - [0.3 Terminology and Conventions](#03-terminology-and-conventions)
        - [0.3.1 Normative Language (MUST, SHOULD, MAY)](#031-normative-language-must-should-may)
        - [0.3.2 Definitions](#032-definitions)
        - [0.3.3 Markdown Terminology](#033-markdown-terminology)
        - [0.3.4 Rendering Contexts (GitHub, npm, etc.)](#034-rendering-contexts-github-npm-etc)
- [1. Introduction](#1-introduction)
    - [1.1 Motivation](#11-motivation)
        - [1.1.1 READMEs as Interface Documents](#111-readmes-as-interface-documents)
        - [1.1.2 READMEs as Conversion Surfaces](#112-readmes-as-conversion-surfaces)
        - [1.1.3 READMEs as Reproducibility Anchors](#113-readmes-as-reproducibility-anchors)
        - [1.1.4 READMEs as Maintenance Artifacts](#114-readmes-as-maintenance-artifacts)
    - [1.2 Problem Statement](#12-problem-statement)
        - [1.2.1 Inconsistent README Quality Across Repositories](#121-inconsistent-readme-quality-across-repositories)
        - [1.2.2 Lack of Formal Standards](#122-lack-of-formal-standards)
        - [1.2.3 High Prevalence of Anti-patterns](#123-high-prevalence-of-anti-patterns)
        - [1.2.4 Fragmentation Across Ecosystems](#124-fragmentation-across-ecosystems)
    - [1.3 Objectives of This Specification](#13-objectives-of-this-specification)
        - [1.3.1 Establishing Normative Standards](#131-establishing-normative-standards)
        - [1.3.2 Improving Adoption and Usability](#132-improving-adoption-and-usability)
        - [1.3.3 Enabling Machine-Checkability](#133-enabling-machine-checkability)
        - [1.3.4 Supporting Long-term Maintainability](#134-supporting-long-term-maintainability)
    - [1.4 Scope](#14-scope)
        - [1.4.1 Repository Types Covered](#141-repository-types-covered)
        - [1.4.2 Exclusions (e.g. Profile READMEs)](#142-exclusions-e-g-profile-readmes)
        - [1.4.3 Language and Platform Neutrality](#143-language-and-platform-neutrality)
    - [1.5 Status Quaestionis (State of the Art)](#15-status-quaestionis-state-of-the-art)
        - [1.5.1 Overview of Existing Guidance](#151-overview-of-existing-guidance)
        - [1.5.2 Conceptual Models Identified](#152-conceptual-models-identified)
        - [1.5.3 Structural Convergence](#153-structural-convergence)
        - [1.5.4 Writing and Rhetorical Practices](#154-writing-and-rhetorical-practices)
        - [1.5.5 Visual and Interaction Patterns](#155-visual-and-interaction-patterns)
        - [1.5.6 Tooling Ecosystem](#156-tooling-ecosystem)
        - [1.5.7 Empirical Observations](#157-empirical-observations)
        - [1.5.8 Gaps in Current Practice](#158-gaps-in-current-practice)
        - [1.5.9 Synthesis and Implications](#159-synthesis-and-implications)
- [2. Conceptual Model](#2-conceptual-model)
    - [2.1 README as Multi-Role Artifact](#21-readme-as-multi-role-artifact)
        - [2.1.1 Documentation](#211-documentation)
        - [2.1.2 Landing Page](#212-landing-page)
        - [2.1.3 Onboarding Flow](#213-onboarding-flow)
        - [2.1.4 Trust Signal](#214-trust-signal)
        - [2.1.5 Reader outcomes (orientation through trust)](#215-reader-outcomes-orientation-through-trust)
    - [2.2 Cognitive Funnel Model](#22-cognitive-funnel-model)
        - [2.2.1 Awareness → Interest → Action → Trust → Continuation](#221-awareness-interest-action-trust-continuation)
        - [2.2.2 Mapping Sections to Funnel Stages](#222-mapping-sections-to-funnel-stages)
        - [2.2.3 First-screen comprehension heuristic](#223-first-screen-comprehension-heuristic)
    - [2.3 User Personas](#23-user-personas)
        - [2.3.1 First-time Visitor](#231-first-time-visitor)
        - [2.3.2 Evaluator](#232-evaluator)
        - [2.3.3 User](#233-user)
        - [2.3.4 Contributor](#234-contributor)
        - [2.3.5 Maintainer (Future Self)](#235-maintainer-future-self)
    - [2.4 Interaction Model](#24-interaction-model)
        - [2.4.1 Scan vs Read Behavior](#241-scan-vs-read-behavior)
        - [2.4.2 Entry Points](#242-entry-points)
        - [2.4.3 Navigation Patterns](#243-navigation-patterns)
- [3. Structural Specification](#3-structural-specification)
    - [3.1 Overview of Section Taxonomy](#31-overview-of-section-taxonomy)
        - [3.1.1 Required Sections](#311-required-sections)
        - [3.1.2 Recommended Sections](#312-recommended-sections)
        - [3.1.3 Optional Sections](#313-optional-sections)
        - [3.1.4 Forbidden/Discouraged Content](#314-forbidden-discouraged-content)
    - [3.2 Required Sections (Normative)](#32-required-sections-normative)
        - [3.2.1 Title Section](#321-title-section)
        - [3.2.2 Summary / Value Proposition](#322-summary-value-proposition)
        - [3.2.3 Proof / Demonstration](#323-proof-demonstration)
        - [3.2.4 Installation](#324-installation)
        - [3.2.5 Quickstart](#325-quickstart)
        - [3.2.6 Usage](#326-usage)
        - [3.2.7 Documentation / Further Reading](#327-documentation-further-reading)
        - [3.2.8 Support / Help](#328-support-help)
        - [3.2.9 License](#329-license)
        - [3.2.10 Contact](#3210-contact)
    - [3.3 Recommended Sections](#33-recommended-sections)
        - [3.3.1 Why / Motivation](#331-why-motivation)
        - [3.3.2 Features](#332-features)
        - [3.3.3 Configuration](#333-configuration)
        - [3.3.4 Examples](#334-examples)
        - [3.3.5 Project Status](#335-project-status)
        - [3.3.6 Limitations / Non-goals](#336-limitations-non-goals)
        - [3.3.7 Contributing](#337-contributing)
        - [3.3.8 Roadmap / Future Work](#338-roadmap-future-work)
        - [3.3.9 Acknowledgements / Thanks](#339-acknowledgements-thanks)
        - [3.3.10 Prior Art / Related Work](#3310-prior-art-related-work)
    - [3.4 Optional Sections](#34-optional-sections)
        - [3.4.1 Architecture Overview](#341-architecture-overview)
        - [3.4.2 FAQ](#342-faq)
        - [3.4.3 Performance / Benchmarks](#343-performance-benchmarks)
        - [3.4.4 Comparisons](#344-comparisons)
        - [3.4.5 Screenshots Gallery](#345-screenshots-gallery)
        - [3.4.6 Badges Section](#346-badges-section)
        - [3.4.7 Demo Links](#347-demo-links)
    - [3.5 Section Ordering Rules](#35-section-ordering-rules)
        - [3.5.1 Mandatory Ordering Constraints](#351-mandatory-ordering-constraints)
        - [3.5.2 Recommended Ordering Patterns](#352-recommended-ordering-patterns)
        - [3.5.3 Cognitive Funnel Alignment](#353-cognitive-funnel-alignment)
        - [3.5.4 Anti-pattern Ordering](#354-anti-pattern-ordering)
- [4. Content Requirements](#4-content-requirements)
    - [4.1 Clarity and Precision](#41-clarity-and-precision)
        - [4.1.1 Avoidance of Ambiguity](#411-avoidance-of-ambiguity)
        - [4.1.2 Explicitness Requirements](#412-explicitness-requirements)
        - [4.1.3 Implicit evaluator questions](#413-implicit-evaluator-questions)
    - [4.2 Example-Driven Documentation](#42-example-driven-documentation)
        - [4.2.1 Code Requirements](#421-code-requirements)
        - [4.2.2 Output Requirements](#422-output-requirements)
        - [4.2.3 Real-World Use Cases](#423-real-world-use-cases)
        - [4.2.4 Breadth of examples (typical, advanced, distinctive)](#424-breadth-of-examples-typical-advanced-distinctive)
    - [4.3 Reproducibility Requirements](#43-reproducibility-requirements)
        - [4.3.1 Environment Specification](#431-environment-specification)
        - [4.3.2 Dependency Clarity](#432-dependency-clarity)
        - [4.3.3 Execution Guarantees](#433-execution-guarantees)
    - [4.4 Trust Signals](#44-trust-signals)
        - [4.4.1 Status Indicators](#441-status-indicators)
        - [4.4.2 Maintenance Transparency](#442-maintenance-transparency)
        - [4.4.3 Testing Indicators](#443-testing-indicators)
    - [4.5 Language of the README](#45-language-of-the-readme)
        - [4.5.1 English as the normative document language](#451-english-as-the-normative-document-language)
        - [4.5.2 Rationale — global audience and tooling](#452-rationale-global-audience-and-tooling)
        - [4.5.3 Additional languages (bilingual or localized layers)](#453-additional-languages-bilingual-or-localized-layers)
        - [4.5.4 Proper nouns, code, and identifiers](#454-proper-nouns-code-and-identifiers)
        - [4.5.5 Machine verification](#455-machine-verification)
    - [4.6 Readability and Cognitive Accessibility](#46-readability-and-cognitive-accessibility)
        - [4.6.1 Distinction from other documentation](#461-distinction-from-other-documentation)
        - [4.6.2 Cognitive assumptions](#462-cognitive-assumptions)
        - [4.6.3 Quantitative metrics (normative targets for tooling)](#463-quantitative-metrics-normative-targets-for-tooling)
        - [4.6.4 Minimum sample size](#464-minimum-sample-size)
        - [4.6.5 Relationship to accessibility (WCAG)](#465-relationship-to-accessibility-wcag)
        - [4.6.6 Reference implementation](#466-reference-implementation)
- [5. Visual and Formatting Specification](#5-visual-and-formatting-specification)
    - [5.1 Markdown Compliance](#51-markdown-compliance)
        - [5.1.1 GitHub Flavored Markdown](#511-github-flavored-markdown)
        - [5.1.2 Heading Structure](#512-heading-structure)
        - [5.1.3 Section Anchors](#513-section-anchors)
    - [5.2 Typography and Emphasis](#52-typography-and-emphasis)
        - [5.2.1 Bold / Italic Usage](#521-bold-italic-usage)
        - [5.2.2 Inline Code Usage](#522-inline-code-usage)
        - [5.2.3 Line Length and Paragraph Size](#523-line-length-and-paragraph-size)
    - [5.3 Code Blocks](#53-code-blocks)
        - [5.3.1 Syntax Highlighting](#531-syntax-highlighting)
        - [5.3.2 Length Constraints](#532-length-constraints)
        - [5.3.3 Output Pairing](#533-output-pairing)
    - [5.4 Images and Media](#54-images-and-media)
        - [5.4.1 Screenshot Requirements](#541-screenshot-requirements)
        - [5.4.2 GIF Usage](#542-gif-usage)
        - [5.4.3 Alt Text Requirements](#543-alt-text-requirements)
        - [5.4.4 Relative Paths](#544-relative-paths)
    - [5.5 Layout and Spacing](#55-layout-and-spacing)
        - [5.5.1 Section Separation](#551-section-separation)
        - [5.5.2 Visual Hierarchy](#552-visual-hierarchy)
        - [5.5.3 Readability Constraints](#553-readability-constraints)
        - [5.5.4 Hosting and rendered size limits](#554-hosting-and-rendered-size-limits)
    - [5.6 Badges](#56-badges)
        - [5.6.1 Non-requirement, encouragement, and scoring](#561-non-requirement-encouragement-and-scoring)
        - [5.6.2 Header cluster — after title, before the summary](#562-header-cluster-after-title-before-the-summary)
        - [5.6.3 Body placement — Project status and beyond](#563-body-placement-project-status-and-beyond)
        - [5.6.4 Allowed badge types](#564-allowed-badge-types)
        - [5.6.5 Overall density and badge walls](#565-overall-density-and-badge-walls)
    - [5.7 Emoji and pictographs](#57-emoji-and-pictographs)
        - [5.7.1 Non-requirement, encouragement, and scoring](#571-non-requirement-encouragement-and-scoring)
        - [5.7.2 Natural fit — the Features section](#572-natural-fit-the-features-section)
        - [5.7.3 Density and placement elsewhere](#573-density-and-placement-elsewhere)
        - [5.7.4 Accessibility and tone](#574-accessibility-and-tone)
    - [5.8 Navigation Enhancements](#58-navigation-enhancements)
        - [5.8.1 Table of Contents](#581-table-of-contents)
        - [5.8.2 Quick Links Sections](#582-quick-links-sections)
        - [5.8.3 Anchor Links](#583-anchor-links)
- [6. Writing Style Specification](#6-writing-style-specification)
    - [6.1 Tone](#61-tone)
        - [6.1.1 Technical Precision](#611-technical-precision)
        - [6.1.2 Neutral Confidence](#612-neutral-confidence)
        - [6.1.3 Avoidance of Marketing Hyperbole](#613-avoidance-of-marketing-hyperbole)
    - [6.2 Sentence Structure](#62-sentence-structure)
        - [6.2.1 Short Sentences](#621-short-sentences)
        - [6.2.2 Active Voice](#622-active-voice)
        - [6.2.3 Declarative Statements](#623-declarative-statements)
    - [6.3 Vocabulary](#63-vocabulary)
        - [6.3.1 Domain-Specific Terminology](#631-domain-specific-terminology)
        - [6.3.2 Avoidance of Buzzwords](#632-avoidance-of-buzzwords)
        - [6.3.3 Concrete claims over empty intensifiers](#633-concrete-claims-over-empty-intensifiers)
    - [6.4 Formatting for Scanability](#64-formatting-for-scanability)
        - [6.4.1 Bullet Lists](#641-bullet-lists)
        - [6.4.2 Section Chunking](#642-section-chunking)
        - [6.4.3 Highlighting Key Concepts](#643-highlighting-key-concepts)
    - [6.5 Language and Readability (Cross-Reference)](#65-language-and-readability-cross-reference)
- [7. Advanced Enhancements](#7-advanced-enhancements)
    - [7.1 Visual Enhancements](#71-visual-enhancements)
        - [7.1.1 Logos](#711-logos)
        - [7.1.2 Animations](#712-animations)
        - [7.1.3 Interactive Media](#713-interactive-media)
    - [7.2 Dynamic Content](#72-dynamic-content)
        - [7.2.1 Generated Badges](#721-generated-badges)
        - [7.2.2 Live Data Widgets](#722-live-data-widgets)
        - [7.2.3 CI-Driven Updates](#723-ci-driven-updates)
    - [7.3 Tooling Ecosystem](#73-tooling-ecosystem)
        - [7.3.1 README Generators](#731-readme-generators)
        - [7.3.2 Linters and Validators](#732-linters-and-validators)
        - [7.3.3 Template Systems](#733-template-systems)
- [8. Anti-patterns](#8-anti-patterns)
    - [8.1 Structural Anti-patterns](#81-structural-anti-patterns)
        - [8.1.1 Missing Sections](#811-missing-sections)
        - [8.1.2 Misordered Sections](#812-misordered-sections)
        - [8.1.3 Overloaded README](#813-overloaded-readme)
    - [8.2 Content Anti-patterns](#82-content-anti-patterns)
        - [8.2.1 Vague Descriptions](#821-vague-descriptions)
        - [8.2.2 Missing Examples](#822-missing-examples)
        - [8.2.3 Hidden Requirements](#823-hidden-requirements)
        - [8.2.4 Non-English or mixed-language gatekeeping](#824-non-english-or-mixed-language-gatekeeping)
        - [8.2.5 Academic or specification-style density in a README](#825-academic-or-specification-style-density-in-a-readme)
    - [8.3 Visual Anti-patterns](#83-visual-anti-patterns)
        - [8.3.1 Badge Spam](#831-badge-spam)
        - [8.3.2 Emoji overload](#832-emoji-overload)
        - [8.3.3 Decorative Images](#833-decorative-images)
        - [8.3.4 Poor Formatting](#834-poor-formatting)
    - [8.4 Maintenance Anti-patterns](#84-maintenance-anti-patterns)
        - [8.4.1 Outdated Instructions](#841-outdated-instructions)
        - [8.4.2 Broken Links](#842-broken-links)
        - [8.4.3 Missing Status](#843-missing-status)
- [9. Validation and Compliance](#9-validation-and-compliance)
    - [9.1 Compliance Levels](#91-compliance-levels)
        - [9.1.1 Minimal Compliance](#911-minimal-compliance)
        - [9.1.2 Recommended Compliance](#912-recommended-compliance)
        - [9.1.3 Strict Compliance](#913-strict-compliance)
    - [9.2 Validation Checklist](#92-validation-checklist)
        - [9.2.1 Section Presence](#921-section-presence)
        - [9.2.2 Content Quality](#922-content-quality)
        - [9.2.3 Formatting Rules](#923-formatting-rules)
        - [9.2.4 Language and readability](#924-language-and-readability)
    - [9.3 Automated Validation](#93-automated-validation)
        - [9.3.1 Linting Rules](#931-linting-rules)
        - [9.3.2 CI Integration](#932-ci-integration)
        - [9.3.3 Schema Definitions](#933-schema-definitions)
- [10. Repository Context Integration](#10-repository-context-integration)
    - [10.1 Related Files](#101-related-files)
        - [10.1.1 CONTRIBUTING.md](#1011-contributing-md)
        - [10.1.2 LICENSE](#1012-license)
        - [10.1.3 CODE_OF_CONDUCT.md](#1013-code-of-conduct-md)
        - [10.1.4 ARCHITECTURE.md](#1014-architecture-md)
        - [10.1.5 package.json (and equivalent manifests)](#1015-package-json-and-equivalent-manifests)
        - [10.1.6 Third-party dependencies](#1016-third-party-dependencies)
    - [10.2 Documentation Architecture](#102-documentation-architecture)
        - [10.2.1 README vs Docs](#1021-readme-vs-docs)
        - [10.2.2 Splitting Strategies](#1022-splitting-strategies)
        - [10.2.3 Linking Conventions](#1023-linking-conventions)
- [11. Adaptation Guidelines](#11-adaptation-guidelines)
    - [11.1 By Project Type](#111-by-project-type)
        - [11.1.1 Libraries](#1111-libraries)
        - [11.1.2 CLI Tools](#1112-cli-tools)
        - [11.1.3 Applications](#1113-applications)
        - [11.1.4 Research Projects](#1114-research-projects)
    - [11.2 By Audience](#112-by-audience)
        - [11.2.1 Developers](#1121-developers)
        - [11.2.2 End Users](#1122-end-users)
        - [11.2.3 Contributors](#1123-contributors)
- [12. Future Work and Extensions](#12-future-work-and-extensions)
    - [12.1 Machine-Readable README Schemas](#121-machine-readable-readme-schemas)
    - [12.2 Integration with Package Registries](#122-integration-with-package-registries)
    - [12.3 AI-Assisted README Generation](#123-ai-assisted-readme-generation)
    - [12.4 Standardization Efforts](#124-standardization-efforts)
- [Appendices](#appendices)
    - [A. Reference Templates](#a-reference-templates)
        - [A.1 Minimal Compliant Template](#a1-minimal-compliant-template)
        - [A.2 Full Featured Template](#a2-full-featured-template)
        - [A.3 Domain-Specific Variants](#a3-domain-specific-variants)
    - [B. Example Fully Compliant README](#b-example-fully-compliant-readme)
    - [C. Validation Checklist Summary](#c-validation-checklist-summary)
        - [C.1 Human Checklist](#c1-human-checklist)
        - [C.2 Machine Validation Schema](#c2-machine-validation-schema)
        - [C.3 Validator Design](#c3-validator-design)
        - [C.4 Validation Architecture](#c4-validation-architecture)
        - [C.5 Rule Engine](#c5-rule-engine)
        - [C.6 File Discovery Logic](#c6-file-discovery-logic)
        - [C.7 Parsing and Analysis Model](#c7-parsing-and-analysis-model)
        - [C.8 Diagnostics Model](#c8-diagnostics-model)
        - [C.9 Exit Codes](#c9-exit-codes)
        - [C.10 Configuration Format](#c10-configuration-format)
        - [C.11 Reporting, Warnings, and Logs](#c11-reporting-warnings-and-logs)
        - [C.12 Scoring Model](#c12-scoring-model)
            - [C.12.4 Positive adjustments for language and readability](#c124-positive-adjustments-for-language-and-readability)
        - [C.13 Package Layout](#c13-package-layout)
        - [C.14 CLI Design](#c14-cli-design)
        - [C.15 Rule Packs and Extensibility](#c15-rule-packs-and-extensibility)
        - [C.16 Link Checking Strategy](#c16-link-checking-strategy)
        - [C.17 Performance and Reliability](#c17-performance-and-reliability)
        - [C.18 Testing Strategy](#c18-testing-strategy)
        - [C.19 Recommended Initial Rule Set](#c19-recommended-initial-rule-set)
        - [C.20 Minimal Programmatic API Sketch](#c20-minimal-programmatic-api-sketch)
        - [C.21 Implementation Sequence](#c21-implementation-sequence)
        - [C.22 TypeScript Package Blueprint](#c22-typescript-package-blueprint)
        - [C.23 Token Estimation and Document Size Informatics (Informative)](#c23-token-estimation-and-document-size-informatics-informative)
    - [D. Glossary](#d-glossary)
        - [D.1 Terms and Definitions](#d1-terms-and-definitions)
        - [D.2 Cross-References](#d2-cross-references)
    - [E. Bibliography](#e-bibliography)
        - [E.1 Citation Format](#e1-citation-format)
        - [E.2 Primary Sources](#e2-primary-sources)
        - [E.3 Tooling and Ecosystem References](#e3-tooling-and-ecosystem-references)
        - [E.4 Informal and Community Sources](#e4-informal-and-community-sources)
        - [E.5 Annotated Bibliography (Optional)](#e5-annotated-bibliography-optional)
---

## 0. Front Matter

### 0.1 Document Metadata

#### 0.1.1 Title and Subtitle
This document is titled _“Repository README Specification (RRS)”_. It defines a normative standard for the structure, content, and presentation of repository README files, with particular emphasis on open-source software hosted on platforms such as GitHub and distributed via package registries.

#### 0.1.2 Authors and Contributors
This specification is authored as a synthesis of established best practices, empirical observations, and formalized design principles derived from existing documentation, community knowledge, and exemplary repositories. Contributions to future revisions of this specification SHOULD be made through a transparent and version-controlled process.

#### 0.1.3 Versioning Scheme
This document follows semantic versioning. Major versions introduce breaking changes to normative requirements, minor versions extend or refine the specification without breaking compatibility, and patch versions introduce clarifications or corrections without altering normative meaning.

#### 0.1.4 Status (Draft, Proposed, Final)
This version of the specification is designated as _Draft_. It is intended for review, critique, and iterative refinement prior to stabilization as a Proposed or Final standard.

#### 0.1.5 Date of Publication
The publication date corresponds to the release timestamp of this version and SHALL be updated upon each revision.

#### 0.1.6 License of the Specification
This specification is intended to be openly reusable and SHOULD be distributed under a permissive license to encourage adoption, extension, and integration into tooling ecosystems.

### 0.2 Abstract

#### 0.2.1 Purpose of the Specification
The purpose of this specification is to define a consistent, rigorous, and practical standard for repository README files. It establishes requirements and recommendations that ensure README files are clear, usable, reproducible, and effective as the primary interface between a repository and its users.

#### 0.2.2 Scope of Applicability
This specification applies to README files in software repositories, particularly those intended for public consumption, collaboration, or distribution. It is designed to be **ecosystem-agnostic** (applicable across JavaScript, Python, Rust, and other stacks). **Normative prose in the README itself** — including all required sections — **MUST be written in English** (see §4.5); this is independent of the natural language used in source code, comments, or localized application UI.

#### 0.2.3 Non-goals
This specification does not attempt to standardize full documentation systems, API reference formats, or internal developer documentation. It also does not prescribe visual branding or stylistic identity beyond functional and readability constraints.

### 0.3 Terminology and Conventions

#### 0.3.1 Normative Language (MUST, SHOULD, MAY)
The key words “MUST”, “SHOULD”, and “MAY” are to be interpreted as described in RFC 2119. “MUST” indicates an absolute requirement, “SHOULD” indicates a strong recommendation with possible justified exceptions, and “MAY” indicates optional behavior.

#### 0.3.2 Definitions

##### 0.3.2.1 README
A README is a top-level documentation file within a repository that provides an overview of the project, instructions for use, and contextual information necessary for evaluation and adoption.

##### 0.3.2.2 Repository
A repository is a version-controlled collection of files representing a software project, typically hosted on platforms such as GitHub, GitLab, or Bitbucket.

##### 0.3.2.3 User vs Contributor
A user is an individual who consumes or integrates the project, while a contributor is an individual who modifies or extends the project’s code or documentation. A README MUST primarily address users, while also enabling contributors.

##### 0.3.2.4 First Success
First success refers to the earliest point at which a user achieves a meaningful outcome using the project. A README MUST facilitate reaching this state with minimal friction.

##### 0.3.2.5 Cognitive Funnel
The cognitive funnel describes the ordered progression from awareness to adoption. A README SHOULD guide readers through this progression in a structured and predictable manner.

##### 0.3.2.6 Reproducibility
Reproducibility refers to the ability to recreate the described behavior or output using the instructions provided. A compliant README MUST support reproducible setup and execution.

##### 0.3.2.7 Trust Signal
A trust signal is any element that communicates reliability, maintenance status, or credibility, including badges, versioning, and explicit status declarations.

#### 0.3.3 Markdown Terminology
Markdown refers to the lightweight markup language used to author README files. GitHub Flavored Markdown (GFM) is the reference rendering context for this specification.

#### 0.3.4 Rendering Contexts (GitHub, npm, etc.)
README files are rendered in different contexts, including repository viewers and package registries. A compliant README MUST remain legible and functional across these contexts.

---

## 1. Introduction

### 1.1 Motivation

#### 1.1.1 READMEs as Interface Documents
The README file functions as the primary interface between a repository and its audience. It is often the first and sometimes only artifact encountered by users, and therefore must convey both the purpose and usability of the project with minimal ambiguity.

#### 1.1.2 READMEs as Conversion Surfaces
A README acts as a decision surface where users evaluate whether to adopt, explore, or abandon a project. Its clarity and structure directly influence engagement, trust, and perceived quality.

#### 1.1.3 READMEs as Reproducibility Anchors
Beyond presentation, the README serves as an operational guide that enables others to reproduce the project's behavior. It functions as a minimal executable specification of the system.

#### 1.1.4 READMEs as Maintenance Artifacts
Over time, the README becomes a durable reference for both new contributors and maintainers. It preserves intent, usage patterns, and operational knowledge beyond the lifespan of individual contributors.

---

### 1.2 Problem Statement

#### 1.2.1 Inconsistent README Quality Across Repositories
README files vary widely in quality, completeness, and structure. Many repositories lack essential sections, provide insufficient guidance, or present information in a disorganized manner.

#### 1.2.2 Lack of Formal Standards
There is no widely adopted normative specification governing README structure and content. Existing guidance is fragmented across documentation, blog posts, and community practices.

#### 1.2.3 High Prevalence of Anti-patterns
Common issues include missing installation instructions, vague descriptions, excessive verbosity, badge overuse, and outdated information. These issues degrade usability and trust.

#### 1.2.4 Fragmentation Across Ecosystems
Different ecosystems exhibit different conventions, leading to inconsistency and increased cognitive load for users navigating multiple projects.

---

### 1.3 Objectives of This Specification

#### 1.3.1 Establishing Normative Standards
This specification aims to define a clear and enforceable standard for README files, reducing ambiguity and improving consistency across repositories.

#### 1.3.2 Improving Adoption and Usability
By standardizing structure and content, the specification seeks to reduce friction for users and increase the likelihood of successful adoption.

#### 1.3.3 Enabling Machine-Checkability
The specification is designed to be compatible with automated validation tools, enabling linting, auditing, and continuous enforcement.

#### 1.3.4 Supporting Long-term Maintainability
A structured README improves maintainability by making expectations explicit and reducing reliance on implicit knowledge.

---

### 1.4 Scope

#### 1.4.1 Repository Types Covered
This specification applies to software repositories of varying types, including libraries, applications, tools, and research projects.

#### 1.4.2 Exclusions (e.g. Profile READMEs)
Profile README files and purely decorative documentation are excluded, as they serve different purposes and follow different conventions.

#### 1.4.3 Language and Platform Neutrality
The specification does not assume a specific programming language or platform, and its requirements are intended to be universally applicable.

---

### 1.5 Status Quaestionis (State of the Art)

This section records the **literature- and practice-informed** background from which the normative requirements elsewhere in the document are derived. It is deliberately discursive: its purpose is to explain *why* certain themes recur—interface framing, ordering, separation from deeper docs, rhetorical as well as technical completeness—without yet encoding them as rules. Empirical claims drawn from anecdotes or single-project case studies are stated in qualified form; primary and secondary sources are listed in Appendix E.

#### 1.5.1 Overview of Existing Guidance

##### 1.5.1.1 Official Platform Documentation (GitHub, npm)
Host and registry documentation establishes a **floor** for what a README is expected to contain: identity, how to install or consume the artefact, how to get help, and how licensing and contribution are surfaced. That guidance is invaluable as a **shared rendering context** (badges, relative links, Markdown dialect), but it stops short of a **cross-repository contract**: it does not fix section order, depth, or machine-checkable completeness. The present specification therefore treats platform docs as **necessary context**, not as a substitute for normative structure.

##### 1.5.1.2 Community Guides (Make a README, Open Source Guides)
Curated lists and “how to write a README” essays—often indexed from community-maintained catalogues—supply **templates, checklists, and taste**. They excel at onboarding authors quickly and at propagating **convergent section names** (installation, usage, contributing). Their limitation is the same as any advisory corpus: recommendations **compete** (for example on badge placement or ideal length), and none is binding across organisations. RRS absorbs their **recurring ingredients** while attempting to resolve **ordering and priority** in a single coherent model (see §1.5.3 and §3.5).

##### 1.5.1.3 Academic and Reproducibility Perspectives
Outside software-marketing discourse, README files appear in **reproducibility** and **research-software** guidance as **anchors for method and environment**: they tie an artefact to versions, data locations, and rerun instructions. That lens extends the README’s role beyond “marketing plus quickstart” toward **knowledge preservation**—a durable statement of what the repository is for and how a future reader can re-establish a working configuration. This specification’s emphasis on reproducibility (§4.3, §3.2) is compatible with that academic framing while remaining applicable to commercial and library projects that are not papers.

##### 1.5.1.4 Informal Practitioner Knowledge (Forums, Reddit)
Forum threads and Q&A sites surface **ground-truth friction**: permission errors, opaque monorepo layouts, missing environment variables, and “works on my machine” gaps. Practitioners repeatedly argue that a README should spell out **clone, build, run, and test** (or stack-specific equivalents) in **copy-pasteable** form. Such advice is **heterogeneous in quality**, but it consistently reinforces two design pressures: **reduce first-use friction**, and **write for an audience that will not read the rest of the repository** unless the README earns the click.

---

#### 1.5.2 Conceptual Models Identified

Across essays and exemplar repositories, the README is rarely described as “just documentation.” Competing metaphors overlap; the following four have proved the most **stable for synthesis**.

##### 1.5.2.1 README as Landing Page
A widely shared intuition—reinforced by minimalist authoring advice—is that the top of the file should behave like a **landing page**: identity, payoff, and a path to action before secondary detail. The landing-page metaphor explains **why** badge walls without explanation feel weak: they lead with **metadata before meaning**. Even authors who favour badges near the top still presuppose an **immediate** articulation of what the product is and how to try it.

##### 1.5.2.2 README as Interface Specification
A stronger claim, developed with particular clarity in module-oriented open source, is that the README is the **primary public interface** of the repository: the **documentation**, not the implementation internals, defines what “using the module” means. In that view, expecting readers to infer behaviour by **spelunking** source is a failure of abstraction. This metaphor motivates **early usage sections**, runnable examples, and explicit caveats—requirements that sit comfortably beside, but are not identical to, the landing-page emphasis on brevity.

##### 1.5.2.3 README as Onboarding Pipeline
Between discovery and habitual use lies a **sequence of commitments**: skim, qualify fit, install, reach first success, then deepen. Several influential guides describe this as a **funnel** rather than a flat file: information should arrive in **descending order of generality and increasing reader commitment** (awareness, interest, action, trust, continuation). That ordering lens is one of the largest upgrades over a mere checklist of sections: it explains not only *what* to include but *why* a misplaced “architecture essay” before a one-line product definition harms adoption.

##### 1.5.2.4 README as Knowledge Preservation Artifact
Long-lived projects inherit contributors and lose oral context. A README that records **intent, constraints, and operational entry points** becomes part of the project’s **institutional memory**. This model overlaps with the reproducibility literature but stresses **maintainer continuity** as much as scientific rerun: the file should remain intelligible when the original author is unavailable.

---

#### 1.5.3 Structural Convergence

##### 1.5.3.1 Core Section Consensus
Synthesis of the sources surveyed for this specification—including curated article lists, platform guidance, and widely cited essays—shows **remarkable agreement on ingredients**: a clear title and scope statement, how to install or otherwise obtain the software, how to use it at least minimally, how to report problems or seek support, contribution expectations where relevant, and licensing. Debates tend not to concern *whether* these elements exist but **how early**, **how deep**, and **where overflow should live**.

##### 1.5.3.2 Divergence in Ordering
The same ingredients arranged in different orders produce **different failure profiles**. Putting exhaustive API tables before a newcomer understands the problem domain optimises for the wrong reader; burying installation three screens down optimises for nobody. Contemporary practice increasingly treats **sequence as part of quality**: identity and proof-of-value first, **minimal path to first success** next, then deeper qualification material, then routing to ancillary documents. That logic is developed normatively in §3.5 and §2.2; here it suffices to note that **ordering rules** are the main formal lever by which this specification reduces variance across repositories.

##### 1.5.3.3 Variability by Project Type
Libraries, CLIs, end-user applications, and research artefacts differ in **which** sections deserve the most vertical space: a CLI foregrounds invocation and options; a library foregrounds API and integration; research READMEs foreground reproducibility and citation. The **convergence** is therefore **modular**: section taxonomy stays stable, but emphasis and optional depth shift. §11 operationalises those shifts without abandoning a shared backbone.

---

#### 1.5.4 Writing and Rhetorical Practices

##### 1.5.4.1 Example-Driven Documentation
Experienced technical authors converge on a simple observation: developers **trust code** more than adjectives. Syntax-highlighted snippets, terminal transcripts, and **runnable** minimal examples reduce ambiguity in a way prose alone cannot. The promotional burden is thus carried by **demonstration**—what the thing does and how little code is required to see it—rather than by superlatives. This specification’s example and quickstart requirements (§3.2, §4.2) follow that consensus.

##### 1.5.4.2 Scan-Oriented Formatting
Browser-based reading rewards **chunked** text: informative headings, short paragraphs, lists where appropriate, and a visible hierarchy that allows **diagonal reading**. The README is competing with dozens of other tabs; **scanability** is not a cosmetic preference but a **usability constraint**. Later sections on typography and spacing (§5) encode minimum expectations compatible with that practice.

##### 1.5.4.3 Benefit-Oriented Feature Framing
Feature lists are easy to write and hard to read when they mirror internal module names. **Benefit-oriented** framing—what pain is removed, for whom, under which constraints—aligns the middle of the funnel with the reader’s **qualification** task (“does this fit my problem?”). It pairs naturally with screenshots or short animations for UI-led projects, where **seeing** the outcome substitutes for a paragraph of adjectives.

---

#### 1.5.5 Visual and Interaction Patterns

##### 1.5.5.1 Screenshots and GIFs
Visual evidence lowers the cost of imagining adoption. A well-chosen screenshot answers “what does it look like in practice?” faster than a feature bullet list; short GIFs or video links address interaction-heavy tools. The risk—file size, staleness, accessibility—motivates pairing media with **alt text** and treating visuals as **supporting** evidence rather than the sole description of behaviour (§5.4).

##### 1.5.5.2 Badge Usage
Badges are optional trust signals: they are **not** mandatory, yet they are **encouraged** when chosen carefully and kept sparse. Effectiveness depends on restraint, relevance, and **placement** — a small cluster after the title but before the summary paragraph (for the highest-signal badges) and, where needed, additional badges in the body (especially under **Project status**, §3.3.5) rather than a single “wall” at the top (see §5.6). Authoritative essays note that badges **cut both ways**: a failing CI badge is a honesty device, not decoration. Readers should infer **signal**, not noise.

##### 1.5.5.3 Layout and Hierarchy
Whitespace, section rhythm, and predictable heading levels are **cognitive affordances**. Repositories that treat the README as a designed surface—not a dump of whatever Markdown someone last pasted—tend to keep related material together and to **repeat** navigation patterns (for example a compact “table of contents” only when length justifies it). The specification’s layout rules (§5.5) aim to preserve that clarity without mandating a single visual style.

##### 1.5.5.4 Progressive Disclosure
Information is revealed in layers, allowing users to engage at increasing levels of detail. Empirical authoring guidance (synthesised from community practice and curated studies) often describes **three tiers**: (1) the **first screen** — title, one-line value proposition, minimal proof (snippet, screenshot, or transcript), and a clear next action; (2) **adoption essentials** — motivation, features, installation, quickstart, and pointers to help or full documentation; and (3) **deeper evaluation** — configuration, architecture (or links thereto), status, limitations, contributing, and license. **Concision arises from prioritisation across tiers**, not from omitting material that belongs in tier (2) or (3); when a file grows unwieldy, authors SHOULD **split** detail into linked docs rather than delete operational content.

This tiered model is precisely where **minimalist** “short top-of-file” advice and **self-sufficient interface** advice meet: the first screen stays lean, but tiers (2) and (3) remain **obligated** unless explicitly and usefully handed off (§10.2). The README is a **funnel**, not a dump—and not a truncated stub that silently externalises everything inconvenient.

---

#### 1.5.6 Tooling Ecosystem

##### 1.5.6.1 Generators and Templates
Scaffolding tools lower the cost of **consistent headings** and boilerplate (license blocks, contribution links). They help teams that would otherwise ship an empty file. Their hazard is **template rot**: identical sections left blank or filled with placeholders. Generators are therefore allies of standardisation only when paired with **review** and, where possible, **automation** that detects empty sections or stale examples.

##### 1.5.6.2 Dynamic Content Systems
Some READMEs incorporate dynamically generated elements such as badges and statistics. Many widgets in the broader ecosystem (for example animated GitHub statistics cards or profile-oriented SVG generators) are optimised for **user profile READMEs** rather than project repositories. This specification applies to **repository** READMEs (§1.4.2); authors SHOULD prefer **stable, high-signal** badges and avoid novelty widgets that add noise or external runtime dependencies without aiding adoption decisions.

##### 1.5.6.3 Linters and Validators
Linting shifts README quality from **taste** toward **regression-tested** expectations: section presence, link health, heading order, and (in principle) readability metrics. The emergence of such tools motivated RRS’s machine-validation appendix (Appendix C) and the reference validator package: **what can be checked in CI** should be, if teams wish to prevent slow drift.

##### 1.5.6.4 Media Creation Tools
GIF capture, terminal recording, and automated screenshot pipelines reduce the **effort barrier** to keeping visuals current. The research consensus is not “always animate,” but “prefer **accurate** media over **pretty** stale media”; tooling makes the honest path cheaper.

---

#### 1.5.7 Empirical Observations

##### 1.5.7.1 Impact on Adoption and Engagement
Reported case studies—most famously documentation-focused work on high-visibility projects—suggest that README and docs investment can move **conversion-style** metrics (for example visitor-to-star rates) sharply **relative to a baseline**, sometimes without a major feature release. Such numbers are **context-dependent** and MUST NOT be interpreted as guarantees; confounders abound (press attention, ecosystem tailwinds). Nevertheless, the directional claim survives scrutiny: the README behaves as a **measurable adoption surface**, not ornament.

##### 1.5.7.2 Common Failure Modes
Qualitative inspection of large corpora and thread archives surfaces recurring failures: **metadata-first** openings, **missing** install or test instructions, **stale** badges, **orphan** links to docs that moved, and **mis-ordered** content that forces a newcomer to read internal philosophy before learning what the program does. Several of these map directly to anti-patterns catalogued in §8; here they are cited as **observed** outcomes of unstructured authoring rather than as normative prohibitions.

##### 1.5.7.3 Correlation with Project Maturity
Mature projects do not always ship excellent READMEs, but **sustained maintenance** correlates with **living** top-level documentation: changelogs, issue templates, and README updates that move in tandem with releases. The correlation is partly causal (healthy engineering hygiene) and partly selective (projects that care about contributors invest in entry surfaces). Either reading supports treating README quality as a **proxy signal** visitors use under uncertainty.

---

#### 1.5.8 Gaps in Current Practice

##### 1.5.8.1 Lack of Normative Standards
Despite decades of informal guidance, the ecosystem still lacks a **single, versioned, testable** standard a team can cite in policy: “our default README conforms to RRS level X.” Without such a reference, onboarding checklists **diverge** across teams and drift within them.

##### 1.5.8.2 Weak Enforcement Mechanisms
Human review catches gross omissions but scales poorly; **ad hoc** review also encodes reviewer taste inconsistently. Machine checks—when available—tend to be **project-local** regexes or bespoke scripts. A shared validator vocabulary (rule IDs, severities, exit codes) closes that gap; Appendix C sketches how.

##### 1.5.8.3 Inconsistent Quality Across Ecosystems
Language communities inherit different **default templates** (Rust’s `cargo new` output differs from Node’s `npm init`). Cross-language polyrepos therefore impose **extra cognitive load** on readers who hop ecosystems daily. A neutral specification cannot erase those defaults, but it can **stabilise expectations** so that “what belongs above the fold” is predictable even when syntax differs.

---

#### 1.5.9 Synthesis and Implications

##### 1.5.9.1 Need for Formal Specification
The foregoing strands—platform floors, essay-level design patterns, academic reproducibility, practitioner friction reports, and tooling—point to the same conclusion: README quality is **too important to leave entirely implicit**. A formal specification does not replace taste, but it **coordinates** taste: it gives authors, reviewers, and machines a **shared target**.

##### 1.5.9.2 Requirements for a Normative Model
Any viable model must integrate **structure** (sections, order), **content** (what must be true of the prose and examples), **presentation** (Markdown and media constraints), and **repository context** (how the README relates to `CONTRIBUTING`, `LICENSE`, architecture docs, and manifests). Siloing any one dimension produces lopsided READMEs that pass a heading lint but still fail readers.

##### 1.5.9.3 Design Principles Derived from Study
Synthesising the research trajectory that informed this document, a high-quality repository README behaves as a **conversion-oriented technical front door**. In sequence, it should help a newcomer answer: **what is this; why should I care; what does it look like in use; how do I try it now; can I trust it; where do I go next**—without pretending to be the entire manual. The specification is grounded in **clarity, reproducibility, scanability, and structured onboarding**. A complementary **methodological** stance—**README-driven development**—treats authoring the README (or its outline) **before** or **alongside** early code as a way to force coherent public scope and API decisions. This specification **does not require** that workflow; it cites it as **rationale** for why teams sometimes ship better surfaces when the README is a **design artefact**, not an afterthought.

##### 1.5.9.4 Minimalist top-of-file vs self-sufficient module README
Two influential stances bracket common practice. **Yegor Bugayenko** argues for **short, structured READMEs** that function chiefly as a **polished entry surface**, deferring depth to linked documentation (`yegor_elegant_readme`, Appendix E). **Stephen Whitmore** frames the README as the **primary module interface**, arguing it should carry enough orientation and usage detail that consumers need not spelunk the repository (`art_of_readme`, Appendix E). These views are **tension, not contradiction**: RRS adopts **tiered disclosure** (§1.5.5.4) — the first screen stays lean, while **normative required sections** (§3.2) and **documentation architecture** (§10.2) ensure operational completeness remains **reachable in-file or via explicit links**, not silently offloaded. Architecture essays (for example on `ARCHITECTURE.md`) reinforce the same boundary: the README orients and qualifies; **deeper** structural explanation belongs where repeat contributors expect it—unless the project is small enough that a compact in-README architecture section truly serves the reader instead of overwhelming them.

---

## 2. Conceptual Model

### 2.1 README as Multi-Role Artifact

#### 2.1.1 Documentation
A README constitutes the minimal, authoritative description of a repository's purpose and use. It MUST provide sufficient information for a competent reader to understand what the project does and how to operate it at a basic level, without requiring inspection of source code.

#### 2.1.2 Landing Page
A README functions as the repository's entry surface and MUST enable rapid orientation. It SHOULD communicate identity, scope, and value within the first screenful, allowing a visitor to decide quickly whether further engagement is warranted.

#### 2.1.3 Onboarding Flow
A README acts as a guided path toward initial use and MUST reduce friction between discovery and execution. It SHOULD present a minimal sequence of steps leading to first success, ordered to minimize cognitive load and external dependencies.

#### 2.1.4 Trust Signal
A README communicates credibility through explicit and implicit signals, including clarity, completeness, status disclosure, and links to governance artifacts. It SHOULD make the project's maintenance state and support channels discoverable without ambiguity.

#### 2.1.5 Reader outcomes (orientation through trust)
Independently of the role labels in §2.1.1–§2.1.4, a compliant README SHOULD enable four **reader outcomes** in sequence: **orientation** (what the artefact is); **qualification** (whether it fits the reader’s problem, stack, and constraints); **activation** (how to reach first success with minimal friction); and **trust-building** (evidence of maintenance, licensing, support paths, and honest limits). This framing is **logically equivalent** to the cognitive funnel in §2.2; it is retained because many external guides and studies use this vocabulary when discussing README effectiveness.

---

### 2.2 Cognitive Funnel Model

#### 2.2.1 Awareness → Interest → Action → Trust → Continuation
User interaction with a README follows a staged progression from initial awareness to continued use. A compliant README MUST be structured to support this progression by presenting information in descending order of generality and increasing commitment.

#### 2.2.2 Mapping Sections to Funnel Stages
Sections near the top MUST address awareness and interest by defining what the project is and why it is useful. Installation and quickstart sections MUST enable action by facilitating immediate use. Status, support, and contribution sections SHOULD establish trust and enable continuation beyond first use.

#### 2.2.3 First-screen comprehension heuristic
Authors SHOULD design the opening of the README so that a **first-time visitor** can answer “what is this, and is it worth my attention?” **without scrolling** — a practical heuristic used in industry writing is on the order of **tens of seconds** of reading time for that decision. This is **not** a machine-verifiable time limit; it is guidance for human review and for ordering content so that title, summary, proof, and primary call-to-action precede deep detail.

---

### 2.3 User Personas

#### 2.3.1 First-time Visitor
The first-time visitor seeks rapid orientation and MUST be able to determine relevance without prior context. The README MUST therefore define the project succinctly and provide an immediate demonstration or example.

#### 2.3.2 Evaluator
The evaluator assesses suitability for a specific use case and requires clarity on capabilities, constraints, and compatibility. The README SHOULD provide enough detail to support this assessment without requiring full documentation traversal.

#### 2.3.3 User
The user aims to execute the software and achieve a concrete outcome. The README MUST enable this by providing accurate installation instructions, a reliable quickstart, and representative usage examples.

#### 2.3.4 Contributor
The contributor seeks to modify or extend the project and requires access to development conventions and entry points. The README SHOULD indicate where contribution guidelines and development documentation are located.

#### 2.3.5 Maintainer (Future Self)
The maintainer, including the original author at a later time, relies on the README as a stable reference of intent and usage. The README SHOULD therefore be explicit, current, and resistant to knowledge loss.

---

### 2.4 Interaction Model

#### 2.4.1 Scan vs Read Behavior
Users primarily scan rather than read linearly, especially on initial contact. A README MUST support scanning through clear headings, short paragraphs, and visible anchors such as code blocks or examples.

#### 2.4.2 Entry Points
Users may enter the README at arbitrary sections via search, deep links, or scrolling. Each major section SHOULD therefore be locally comprehensible and not rely excessively on prior sections for interpretation.

#### 2.4.3 Navigation Patterns
Navigation within a README relies on heading structure and, where present, a table of contents or quick links. A compliant README SHOULD use consistent and descriptive headings to enable both manual scanning and automated outline generation.

---

## 3. Structural Specification

### 3.1 Overview of Section Taxonomy

#### 3.1.1 Required Sections
Required sections define the minimal structure necessary for a README to be considered compliant. These sections MUST be present and MUST satisfy the content requirements defined in this specification.

#### 3.1.2 Recommended Sections
Recommended sections enhance usability and completeness but are not strictly mandatory. Their omission SHOULD be justified by project simplicity or irrelevance.

#### 3.1.3 Optional Sections
Optional sections provide additional context or specialization and MAY be included where appropriate. Their inclusion MUST NOT degrade clarity or introduce redundancy.

#### 3.1.4 Forbidden/Discouraged Content
Certain content patterns are discouraged or forbidden due to their negative impact on usability, including misleading descriptions, decorative noise, and structurally disruptive elements. Such patterns are formally defined in Section 8.

---

### 3.2 Required Sections (Normative)

#### 3.2.1 Title Section

##### 3.2.1.1 Naming Requirements
The README MUST begin with a clear and unambiguous project title. The title MUST uniquely identify the project within its domain. For repositories containing a primary manifest (for example `package.json`, `Cargo.toml`, or `go.mod`), the README title MUST match the `name` field defined in that manifest to prevent metadata dissociation.

##### 3.2.1.4 Banner and Logo Placement
If the README includes a project logo or banner, it MUST be placed immediately after the H1 title and before the summary paragraph. Banners SHOULD not be placed inside their own H2 section.

##### 3.2.1.2 Subtitle / Tagline Requirements
A subtitle or tagline SHOULD immediately follow the title and MUST provide a concise description of the project's purpose. It SHOULD be intelligible to readers unfamiliar with the project.

##### 3.2.1.3 Searchability Constraints
The title and subtitle SHOULD include domain-relevant terms to support discoverability via search engines and repository platforms.

---

#### 3.2.2 Summary / Value Proposition

##### 3.2.2.1 One-Sentence Rule
The README MUST include a concise summary that describes what the project is, who it is for, and what benefit it provides. This summary SHOULD be expressed in one sentence where possible and MUST NOT exceed **120 characters** to ensure compatibility with package manager manifests and search engine snippets.

##### 3.2.2.2 Satisfaction Criteria
The summary requirement is satisfied when **any** of the following conditions holds:

1. **Inline summary** — A paragraph **or blockquote** that immediately follows the H1 title (ignoring badge-only image paragraphs and standalone images that may appear between the title and the summary). Both `paragraph` and `blockquote` AST node types are accepted; badge-only paragraphs (containing nothing but images or image-wrapping links) are skipped and do not consume the summary slot.

2. **Explicit section** — A non-empty H2 section whose heading matches the canonical names "Summary", "Value Proposition", "About", or "Overview" appears among the document's top-level sections, regardless of any content that precedes it.

When both an inline summary and an explicit summary section are present, the requirement is satisfied by either; no diagnostic is emitted.

##### 3.2.2.3 Target Audience Identification
The summary MUST implicitly or explicitly identify the intended audience or use case. Ambiguous or overly generic descriptions are non-compliant.

##### 3.2.2.4 Benefit Specification
The summary SHOULD emphasize the primary benefit or distinguishing characteristic of the project rather than internal implementation details.

---

#### 3.2.3 Proof / Demonstration

##### 3.2.3.1 Code Snippet Requirements
The README MUST include at least one concrete example demonstrating usage. This example SHOULD be minimal and directly executable where applicable.

Code examples MUST NOT include command prompts (for example `$`, `>`, or `%`) before the command itself. These characters interfere with copy-paste functionality and introduce user friction.

##### 3.2.3.2 Screenshot / GIF Requirements
Where visual output or interaction is relevant, the README SHOULD include a screenshot or animated demonstration. Visual elements MUST be purposeful and directly related to functionality.

##### 3.2.3.3 Output Inclusion
Examples SHOULD include expected output or observable results, enabling users to verify correct execution.

When a command and its output are shown in the same block, the output SHOULD be commented out (for example, `command # output`) so that the block remains copy-pasteable as a valid executable command.

---

#### 3.2.4 Installation

##### 3.2.4.1 Environment Requirements
The README MUST specify prerequisites required to install or run the project, including runtime environments, dependencies, or system constraints. This requirement is waived for **Documentation-only** repositories (§11.1.4).

##### 3.2.4.2 Package Manager Instructions
Installation instructions MUST be explicit and SHOULD include commands for relevant package managers or distribution methods.

Placeholders that require user substitution (for example branch names, keys, or local paths) MUST be formatted in `UPPERCASE` (for example, `git checkout -b BRANCH-NAME`). Authors SHOULD avoid using `<angle-brackets>` for placeholders as they may conflict with Markdown parsing or platform-specific variables.

##### 3.2.4.3 Platform Variants
Where applicable, installation instructions SHOULD address platform-specific differences or constraints.

##### 3.2.4.4 Known installation or environment friction
Where recurring setup failures are known (permissions, native bindings, SSL proxies, monorepo workspace layouts, required environment variables, and similar), the README SHOULD surface **concise remedies or links** near installation or quickstart — not only in external docs — because reducing first-use friction has disproportionate impact on adoption. This requirement is **not** an invitation to duplicate issue trackers; it asks authors to lift **high-frequency** blockers into the primary path.

---

#### 3.2.5 Quickstart

##### 3.2.5.1 Minimal Path to First Success
The README MUST provide a quickstart section that enables users to achieve first success with minimal effort. This requirement is waived for **Documentation-only** repositories (§11.1.4).

##### 3.2.5.2 Copy-Paste Guarantee
Instructions in the quickstart SHOULD be copy-pasteable and MUST avoid implicit steps or assumptions.

##### 3.2.5.3 Expected Result Definition
The quickstart MUST define what constitutes successful execution, either through output, behavior, or observable effect.

---

#### 3.2.6 Usage

##### 3.2.6.1 Task-Oriented Structure
The usage section MUST be organized around common tasks or use cases rather than internal architecture.

##### 3.2.6.2 Common Scenarios
The README SHOULD include examples covering typical usage scenarios.

##### 3.2.6.3 Progressive Complexity
Usage documentation SHOULD progress from simple to more advanced scenarios, enabling gradual learning.

---

#### 3.2.7 Documentation / Further Reading

##### 3.2.7.1 External Docs Linking
The README MUST link to more detailed documentation where available.

##### 3.2.7.2 Internal Docs Structure
Links to internal documentation SHOULD use relative paths and remain stable across repository contexts.

##### 3.2.7.3 API Reference Delegation
The README SHOULD not contain exhaustive API documentation and MUST delegate such detail to dedicated references.

---

#### 3.2.8 Support / Help

##### 3.2.8.1 Issue Tracking
The README MUST indicate how to report bugs or issues.

##### 3.2.8.2 Discussion Channels
Where applicable, the README SHOULD provide channels for discussion or questions.

##### 3.2.8.3 Security Reporting
If relevant, the README SHOULD include instructions for reporting security vulnerabilities.

---

#### 3.2.9 License

##### 3.2.9.1 License Declaration
The README MUST clearly state the project's license using a valid **SPDX identifier** (for example `MIT`, `Apache-2.0`, or `GPL-3.0-or-later`) from the [SPDX License List](https://spdx.org/licenses/) to ensure machine-readability by automated compliance tools.

##### 3.2.9.2 Link to License File
A link to the full license text MUST be provided.

##### 3.2.9.3 Copyright Owner Identification
Any license or copyright notice — whether in the README itself, a LICENSE file, or both — MUST name the copyright owner explicitly. A copyright line that reads `Copyright (c) <year>` without identifying the owner (individual, organization, or legal entity) is legally ambiguous and SHALL be treated as non-compliant. Compliant forms include:

- `Copyright (c) 2026 Jane Doe`
- `Copyright (c) 2026 Acme Corp.`
- `Copyright (c) 2026 The ProjectName Authors`

Omitting the owner renders the copyright assertion void in most jurisdictions and undermines the trust signal the license is intended to provide.

---

#### 3.2.10 Contact

##### 3.2.10.1 Purpose
The README MUST include a **Contact** section (or equivalent heading such as **Contacts**, **Maintainers**, or **Team**) placed **toward the end** of the document — after primary usage and governance-oriented sections (for example Support and Contributing) and typically immediately before the **License** section.

##### 3.2.10.2 Maintainer Identification
The section MUST name at least one current owner, maintainer, or chief contributor responsible for the project (individual or organisational identity). Pseudonymous contact is acceptable only where it remains a stable, verifiable channel (for example a long-lived organisation inbox or maintainer team alias).

##### 3.2.10.3 Contact Channels
For each listed person or role, the README MUST provide at least one reachable channel: a **mailto** link or visible **e-mail address**, and/or one or more **hyperlinks** to social or forge profiles (for example GitHub, X, LinkedIn, Instagram). Where a social handle is shown, it SHOULD appear together with its URL (for example `@handle` linked to `https://…`) so readers can follow the profile without guessing the platform.

##### 3.2.10.4 HTML Link Behaviour
Where raw HTML is used for external contact or profile links, anchors SHOULD use `target="_blank"` and `rel="noopener noreferrer"`. Standard Markdown links satisfy portability requirements where HTML attributes cannot be expressed.

---

### 3.3 Recommended Sections

#### 3.3.1 Why / Motivation
A README SHOULD include a section explaining the problem the project addresses and the rationale for its existence. This section SHOULD articulate context, limitations of existing approaches, and the intended improvement, thereby enabling evaluators to understand relevance beyond surface functionality.

#### 3.3.2 Features
A features section SHOULD summarize the primary capabilities of the project in a concise and user-oriented manner. Each feature description SHOULD express an outcome or benefit rather than an implementation detail, and the section SHOULD avoid redundancy with the summary.

The **Features** section is also the most natural place for **optional emoji or pictographs** when authors want extra scanability: they are **not** required, but when used, each top-level feature bullet SHOULD begin with **at most one** symbol that is **semantically aligned** with that line (for example a shield for security, a chart for metrics, a package for publishing). Emoji SHOULD remain **sparse** elsewhere in the README so headings and prose are not mistaken for informal chat (§5.7).

#### 3.3.3 Configuration
Where the project exposes configurable parameters, a configuration section SHOULD describe available options, defaults, and their effects. This section SHOULD be structured for reference and clarity, enabling users to adjust behavior without consulting source code.

#### 3.3.4 Examples
A README SHOULD include additional examples beyond the minimal quickstart to demonstrate typical and advanced usage. These examples SHOULD be representative, reproducible, and sufficiently varied to illustrate the project's scope. Authors SHOULD follow the breadth pattern in §4.2.4 when choosing which scenarios to show.

#### 3.3.5 Project Status
A project status section SHOULD explicitly state the current maintenance state, such as active development, beta, stable, or maintenance mode. This section SHOULD also indicate versioning expectations and any known limitations affecting production use.

This section is also a **natural home** for secondary trust badges that would crowd the top of the file — for example continuous integration status, test or coverage summaries, static-analysis or security-scan widgets, and similar machine-generated shields — so readers see narrative status prose together with supporting badges (§5.6.3).

#### 3.3.6 Limitations / Non-goals
A README SHOULD include a section clarifying what the project does not attempt to do. This section SHOULD define scope boundaries and known constraints, reducing misinterpretation and inappropriate use.

#### 3.3.7 Contributing
A contributing section SHOULD indicate whether contributions are welcome and MUST provide a clear entry point to contribution guidelines. It SHOULD summarize expectations and link to detailed instructions where applicable.

#### 3.3.8 Roadmap / Future Work
Where relevant, a roadmap section MAY outline planned features or future directions. This section SHOULD be concise and SHOULD not imply guarantees unless explicitly stated.

#### 3.3.9 Acknowledgements / Thanks
A **Many thanks to**, **Thanks**, **Thank you**, **Acknowledgements**, **Credits**, or equivalent section MAY recognise contributors, sponsors, dependencies, or external influences. Projects are **encouraged** to include such a section when others materially helped the work. Its inclusion SHOULD serve transparency and attribution without distracting from core content.

When both an acknowledgements-style section and the **Contact** section (§3.2.10) are present, the acknowledgements section SHOULD appear **immediately before** Contact so readers see gratitude and attribution before reaching maintainer contact details.

#### 3.3.10 Prior Art / Related Work
A **Prior art**, **Related work**, **Other implementations**, **Related projects**, or similarly titled section is **optional** but **highly recommended**. It SHOULD situate the repository among existing knowledge, standards, and software so readers can judge novelty, correctness, and interoperability.

Where the project implements an algorithm, protocol, or specification published in a journal, standards body, preprint server, or other venue, the README SHOULD use this section (or equivalent prominent prose) to **cite** that work — for example with stable identifiers (DOI, arXiv, RFC number with title or link), bibliographic references, or links to the normative specification.

Where alternative or related implementations exist — including in other programming languages, on other platforms, or within other ecosystems — the README SHOULD **mention** them with enough context (name, ecosystem, or link) for readers to compare or migrate. The section SHOULD remain factual and SHOULD not substitute for the optional **Comparisons** section (§3.4.4) when a dedicated competitive analysis is warranted.

When both this section and **Acknowledgements** (§3.3.9) are present, **Prior art / Related work** SHOULD typically appear **before** Acknowledgements so intellectual lineage precedes gratitude and attribution.

#### 3.3.11 Troubleshooting
A README SHOULD include an explicit Troubleshooting section (or equivalent such as **Known Issues** or **FAQ**) when common failure modes or environment frictions are identified. This section SHOULD follow a structured pattern of **Problem (Observable Symptom)** → **Cause (Root Reason)** → **Solution (Actionable Resolution)**. This structure minimizes the time users spend searching issue trackers for recurring setup or runtime blockers.

#### 3.3.12 Background
A README SHOULD include a **Background** section (or equivalent such as **Motivation** or **Context**) that describes the history, intellectual roots, and technical rationale of the project. While the **Summary** (§3.2.2) explains *what* the project is, the **Background** section provides the deeper narrative of *why* it exists and how it differs from similar efforts.

#### 3.3.13 API Reference
For libraries and frameworks, a README SHOULD include an **API** or **Reference** section that documents the public-facing methods, functions, and interfaces. This section SHOULD provide enough detail for a developer to begin integration without consulting full external documentation, while avoiding exhaustive detail that would belong in a dedicated reference manual.

---

### 3.4 Optional Sections

#### 3.4.1 Architecture Overview
An architecture overview MAY provide a high-level description of system structure, components, and design principles. This section SHOULD remain concise and SHOULD defer detailed explanations to dedicated architecture documents.

#### 3.4.2 FAQ
A frequently asked questions section MAY address recurring issues or misunderstandings. This section SHOULD focus on practical concerns that are not adequately covered elsewhere in the README.

#### 3.4.3 Performance / Benchmarks
Projects where performance is a primary concern MAY include benchmark data or performance characteristics. Such information SHOULD be presented clearly and MUST be reproducible or verifiable.

#### 3.4.4 Comparisons
A comparison section MAY position the project relative to alternatives. This section SHOULD remain factual and avoid subjective or promotional bias.

#### 3.4.5 Screenshots Gallery
Where visual output is central to the project, a gallery of screenshots MAY be included. This section SHOULD complement, rather than replace, the primary demonstration.

#### 3.4.6 Badges Section
A dedicated **Badges** section MAY be included to group trust signals that do not fit cleanly under **Project status**. Whether or not such a section exists, authors SHOULD follow the two-locus placement model in §5.6.2–§5.6.3 rather than concentrating every badge at the very top. Badges SHOULD be limited to those conveying meaningful information and SHOULD not dominate the visual hierarchy.

#### 3.4.7 Demo Links
Links to live demos, sandboxes, or hosted examples MAY be provided. These links SHOULD be stable and clearly labeled.

---

### 3.5 Section Ordering Rules

#### 3.5.1 Mandatory Ordering Constraints
The README MUST begin with the title, summary, and initial proof or demonstration. Installation and quickstart sections MUST appear before extended usage or configuration content. Support information SHOULD appear before the final governance block. The **Contact** section MUST appear toward the end of the document (see §3.2.10.1). The **License** section MUST remain clearly visible toward the end; typical ordering places **Prior art / Related work** (if present, §3.3.10) before **Acknowledgements** (if present), then **Acknowledgements** immediately before **Contact**, then **License** last or nearly last.

#### 3.5.2 Recommended Ordering Patterns
Sections SHOULD follow the cognitive funnel model, progressing from general description to actionable steps and then to detailed reference. This ordering SHOULD minimize the need for backtracking and support incremental understanding.

#### 3.5.3 Cognitive Funnel Alignment
Top-level sections MUST correspond to stages of user engagement, beginning with awareness and culminating in continuation. Information required for early decision-making MUST not be deferred to later sections.

#### 3.5.4 Anti-pattern Ordering
The README MUST NOT begin with non-informative elements such as badge clusters without context. Architectural or internal details MUST NOT precede basic usage information. Excessive front-loading of low-priority content is non-compliant.

---

## 4. Content Requirements

### 4.1 Clarity and Precision

#### 4.1.1 Avoidance of Ambiguity
All descriptions MUST be explicit and unambiguous. The README MUST avoid vague terminology that does not convey concrete meaning or actionable understanding.

#### 4.1.2 Explicitness Requirements
Assumptions about user knowledge or environment MUST be stated where relevant. Hidden prerequisites or implicit steps are not permitted in compliant READMEs.

#### 4.1.3 Implicit evaluator questions
Beyond literal prerequisites, prose SHOULD reduce **adoption uncertainty** for a skeptical technical reader: stack fit (language, runtime, platform), approximate setup effort, maintenance and versioning posture, stability of public APIs or CLIs where relevant, how to validate that outputs are correct, and major **trade-offs** versus alternatives. Answers need not appear as a FAQ; they MAY be woven into summary, features, status, and limitations — but they SHOULD not be left entirely implicit when they materially affect adoption.

---

### 4.2 Example-Driven Documentation

#### 4.2.1 Code Requirements
Code examples MUST be syntactically correct and SHOULD be directly executable. Examples SHOULD use realistic inputs and reflect actual usage patterns.

#### 4.2.2 Output Requirements
Examples SHOULD include expected output or observable results, enabling users to confirm correct behavior.

#### 4.2.3 Real-World Use Cases
Where applicable, the README SHOULD demonstrate real-world scenarios. These examples SHOULD illustrate practical value rather than abstract capability.

#### 4.2.4 Breadth of examples (typical, advanced, distinctive)
When multiple examples are appropriate (see also §3.3.4), authors SHOULD cover at least three **bands**: the **dominant everyday use case**; one **advanced** or edge scenario; and one example that highlights a **distinctive** or impressive capability of the project. The goal is to demonstrate breadth without turning the README into a reference manual.

---

### 4.3 Reproducibility Requirements

Practitioner threads such as [How to Write a README on r/learnprogramming](https://www.reddit.com/r/learnprogramming/comments/vxfku6/how_to_write_a_readme/) repeatedly recommend spelling out **clone, build, run, and test** (or the closest equivalents for the stack) so a newcomer can reproduce the maintainer’s workflow without guesswork (see also `reddit_readme_discussion`, Appendix E).

#### 4.3.1 Environment Specification
The README MUST define the environment required to run the project, including runtime versions and system dependencies where relevant.

#### 4.3.2 Dependency Clarity
All dependencies required for execution MUST be identifiable from the README or clearly linked documentation. Implicit or hidden dependencies are not permitted.

#### 4.3.3 Execution Guarantees
Instructions provided MUST lead to a reproducible outcome under stated conditions. If variability exists, it MUST be documented.

---

### 4.4 Trust Signals

#### 4.4.1 Status Indicators
The README SHOULD communicate project maturity and maintenance status. This information MUST be accurate and up to date.

#### 4.4.2 Maintenance Transparency
Known issues, limitations, and maintenance expectations SHOULD be disclosed. Omission of critical limitations is considered misleading.

#### 4.4.3 Testing Indicators
Where applicable, the README MAY include indicators of testing or validation, provided they convey meaningful information and are current.

---

### 4.5 Language of the README

#### 4.5.1 English as the normative document language
The README **MUST** be authored so that **English is the primary language** of the file: the title, summary, and **every required section** (§3.2) **MUST** be written in English. This requirement exists because repository hosts, package registries, search engines, and the majority of global contributors expect a single _lingua franca_ at the repository’s front door, even when the project’s community includes many native languages.

#### 4.5.2 Rationale — global audience and tooling
English remains the de facto interchange language for open-source collaboration, issue triage, security advisories, and automated documentation pipelines. A README that cannot be parsed or skimmed by an international reader without machine translation fails its role as a **first-contact** artifact. English does not imply cultural dominance of any region; it is specified here strictly as a **practical interoperability** constraint analogous to choosing UTF-8 for encoding.

#### 4.5.3 Additional languages (bilingual or localized layers)
Sections or paragraphs **MAY** appear in another natural language (for example Chinese, Japanese, Spanish, or Arabic) **in addition to** English, for example under headings such as **中文说明** or **Léeme en español**. Such material **SHOULD NOT** introduce facts, constraints, installation steps, licensing terms, or safety information that are **absent** from the English layer. Where both exist, the English layer remains **authoritative** for compliance with this specification.

For repositories providing full translations of the primary documentation, the standard naming convention **SHOULD** follow the pattern `README.{lang}.md` (for example `README.zh-CN.md` or `README.fr.md`), where `{lang}` is a valid BCP 47 language identifier.

#### 4.5.4 Proper nouns, code, and identifiers
Project names, commands, API identifiers, registry coordinates, and citations **MAY** use non-English forms when they are stable external symbols (for example `npm`, _Kyiv_, or a paper title in French). This exception does not waive §4.5.1 for surrounding explanatory prose.

#### 4.5.5 Machine verification
Automated validators **SHOULD** classify the language of aggregated prose (excluding fenced code blocks) using statistical language identification and **SHOULD** warn or fail when the detected primary language is not English, subject to minimum word-count thresholds to avoid false positives on very short files.

---

### 4.6 Readability and Cognitive Accessibility

#### 4.6.1 Distinction from other documentation
Long-form specifications, RFCs, academic papers, and deeply technical design documents **MAY** assume specialist readers and **MAY** tolerate lower surface readability (long sentences, dense nominalisations, domain jargon). A repository README **MUST NOT** optimise solely for that audience: it is a **conversion and onboarding** surface for evaluators, new contributors, security reviewers, and package consumers who may not have advanced training in the domain. README prose **SHOULD** therefore aim for **higher readability** than internal architecture docs or normative standards published by SDOs.

#### 4.6.2 Cognitive assumptions
README readers **SHOULD** be assumed to be **technically literate** (comfortable with CLIs, version numbers, and hyperlinks) but **not** assumed to have postgraduate reading stamina. Authors **SHOULD** prefer plain explanations, short paragraphs, and concrete examples over abstract theory, while still allowing precise terminology where it aids correctness.

#### 4.6.3 Quantitative metrics (normative targets for tooling)
Where automated measurement is available, validators **SHOULD** evaluate **prose extracted from the Markdown AST** (headings, paragraphs, list items, and table cells, excluding fenced code blocks and optionally normalising URL tokens) using established readability formulae. The following **default thresholds** are tuned for **developer-facing READMEs** (command names, package identifiers, and URLs often depress Flesch Reading Ease without harming usefulness); **stricter presets** **MAY** tighten all numeric gates.

| Metric | Direction | Recommended default (warn if outside) | Strict preset (example) | Notes |
| --- | --- | --- | --- | --- |
| **Flesch Reading Ease** | Higher is easier | **≥ −5** | **≥ 0** | Often negative when inline commands dominate; interpret alongside grade-level scores. |
| **Flesch–Kincaid grade level** | Lower is easier (US school years) | **≤ 22** | **≤ 16** | Values above ~16 approach upper-undergraduate density. |
| **Gunning Fog index** | Lower is easier | **≤ 19** | **≤ 16** | Approximates years of formal education needed to read text once. |
| **SMOG grade** | Lower is easier | **≤ 20** (if **≥ 10** sentences analysed) | **≤ 16** | Originally normed on ≥30 sentences; validators **SHOULD** skip or down-rank SMOG when samples are short. |
| **Dale–Chall** (grade equivalent) | Lower is easier | **≤ 13.0** | **≤ 9.5** | Uses familiar-word lists; higher scores correlate with uncommon vocabulary. |

Projects **MAY** override numeric limits in configuration when justified (for example research repositories with unavoidable terminology), but **SHOULD** document the waiver in repository policy.

#### 4.6.4 Minimum sample size
Automated readability scores **SHOULD** be computed only when extracted prose meets a **minimum word count** (reference validators typically use **≥ 100** words for grade-level metrics and **≥ 80** words for language detection). Below those counts, tools **SHOULD** abstain rather than emit noisy diagnostics.

#### 4.6.5 Relationship to accessibility (WCAG)
Readability scores are **not** a substitute for WCAG conformance (structure, headings, link text, alt attributes). They **complement** accessibility by reducing cognitive load for **all** readers, including users with dyslexia or non-native English proficiency.

#### 4.6.6 Reference implementation
Reference validators **SHOULD** implement the metrics using a maintained statistical library (for example **`text-readability`** on npm, which exposes Flesch, Flesch–Kincaid, Gunning Fog, SMOG, Dale–Chall, and related helpers) combined with a compact language classifier (for example **`franc`**) for §4.5.5.

---

## 5. Visual and Formatting Specification

### 5.1 Markdown Compliance

#### 5.1.1 GitHub Flavored Markdown
A README MUST be valid GitHub Flavored Markdown (GFM) and render correctly in common contexts such as repository views and package registries. Non-standard extensions MUST NOT be required for correct interpretation of core content.

#### 5.1.2 Heading Structure
Headings MUST form a clear hierarchical structure using ordered levels. Top-level sections SHOULD use second-level headings, and deeper nesting SHOULD remain shallow to preserve readability and navigability. Authors MUST NOT skip header levels (for example, moving from H2 directly to H4). Every header at the same level on a page MUST be unique. There SHOULD be text content between a header and its subheader to provide transition and context.

#### 5.1.3 Section Anchors
Headings SHOULD be written to produce stable, predictable anchor links. Section titles MUST avoid unnecessary punctuation or ambiguity that would hinder linking or navigation.

#### 5.1.4 Alerts (GitHub Standard)
The README SHOULD use GitHub-standard alerts to emphasize information that justifies breaking the flow of content. Alerts MUST follow the syntax `> [!TYPE]` and be restricted to the following types:
- `[!NOTE]` — Additional context or caveats.
- `[!TIP]` — Recommendations, best practices, or hints.
- `[!IMPORTANT]` — Key information required to achieve a goal.
- `[!WARNING]` — Potential risks to be aware of.
- `[!CAUTION]` — Dangerous or destructive actions (security/data risk).

Authors SHOULD use alerts sparingly, typically no more than one per section and never consecutively.

#### 5.1.5 Keyboard Shortcuts
When referring to keyboard shortcuts, authors SHOULD use the `<kbd>` tag (for example, `<kbd>Ctrl</kbd>+<kbd>S</kbd>`). Modifier keys SHOULD be spelled out based on the operating system (for example, `Command` for Mac and `Ctrl` for Windows/Linux).

---

### 5.2 Typography and Emphasis

#### 5.2.1 Bold / Italic Usage
Emphasis SHOULD be used sparingly to highlight key concepts or terms. To preserve scannability and accessibility, bolding SHOULD be limited to no more than five contiguous words. BoldING MUST NOT be applied to words that already have secondary formatting, such as all-caps placeholders. Emphasis MUST NOT be the sole method of conveying critical meaning.

#### 5.2.2 Inline Code Usage
Identifiers, commands, file names, and code fragments MUST be formatted using inline code. This formatting SHOULD distinguish executable or literal content from explanatory prose.

#### 5.2.3 Line Length and Paragraph Size
Paragraphs SHOULD be concise and limited in length to support scanning. Long blocks of text MUST be avoided, and sentences SHOULD remain clear and direct.

---

### 5.3 Code Blocks

#### 5.3.1 Syntax Highlighting
Code blocks MUST specify a language identifier where applicable to enable syntax highlighting. This improves readability and reduces ambiguity. Lines in code blocks SHOULD be limited to approximately 60 characters to avoid horizontal scrolling in browser-based repository views.

#### 5.3.2 Length Constraints
Code examples SHOULD be minimal and focused. Excessively long code blocks MUST be avoided unless necessary to demonstrate a complete and essential workflow.

#### 5.3.3 Output Pairing
Where relevant, code blocks SHOULD be paired with expected output or observable results. This pairing enables verification and improves comprehension.

---

### 5.4 Images and Media

#### 5.4.1 Screenshot Requirements
Screenshots SHOULD be included where they clarify behavior or output. Images MUST be directly relevant to the content and SHOULD not be decorative.

#### 5.4.2 GIF Usage
Animated GIFs MAY be used to demonstrate interactions or workflows. They SHOULD be short, focused, and optimized to minimize file size and loading time.

#### 5.4.3 Alt Text Requirements
Every image MUST include meaningful alternative text providing a textual equivalent of the visual information. Alt text MUST satisfy the following:
- **Length.** Between 40 and 150 characters.
- **Prefix.** SHOULD begin with content type (for example, "Screenshot of..." or "Diagram showing...").
- **Content.** Focus on the core idea or meaning rather than a literal description of pixels.
- **Punctuation.** MUST end with a punctuation mark (generally a period).
- **Redundancy.** MUST NOT start with "Image of..." or "Graphic showing...", as these are redundant for screen readers.

#### 5.4.4 Relative Paths
Images stored within the repository MUST be referenced using relative paths. This ensures portability across branches and forks.

---

### 5.5 Layout and Spacing

#### 5.5.1 Section Separation
Sections MUST be visually separated using headings and spacing. Adequate whitespace SHOULD be used to prevent visual crowding.

#### 5.5.2 Visual Hierarchy
The README MUST present a clear visual hierarchy that reflects the logical structure of the content. Headings, code blocks, and spacing SHOULD guide the reader's attention.

#### 5.5.3 Readability Constraints
Formatting MUST prioritize readability over stylistic decoration. Elements that obscure structure or distract from content are not permitted.

#### 5.5.4 Hosting and rendered size limits
On GitHub, **very large** README sources can exceed platform rendering limits: content beyond approximately **500 KiB** of the rendered document may be **truncated** in the default repository view. Authors SHOULD therefore treat the README as a **front door** that links outward for exhaustive logs, huge tables, generated API dumps, and similar material. This constraint aligns with the machine-validation hint `recommended_max_rendered_size_kib` in Appendix C.2.

---

### 5.6 Badges

#### 5.6.1 Non-requirement, encouragement, and scoring
Badges are **not** mandatory. They are nevertheless **encouraged** when they are **wise and sparing**: each badge SHOULD answer a question a reasonable visitor would ask (version, license, package index, key compliance) and SHOULD remain accurate.

A reference validator MAY apply a **small positive scoring adjustment** when the README includes at least one badge **and** both (a) the **header cluster** (§5.6.2) respects the recommended maximum count and (b) the **total** badge count across the document stays within configured limits (§5.6.5), so that restrained, well-placed badges are rewarded without mandating them.

#### 5.6.2 Header cluster — after title, before the summary
The first natural position for badges is **immediately after the H1 project title** (or title line and optional one-line tagline, if used) and **before** the introductory summary paragraph — that is, still within the identity block but **not** ahead of the title (which remains non-compliant; see §3.5.4 and §8.3.1).

Badges in this cluster MUST be **newline-delimited** (each on its own line in the Markdown source) to prevent horizontal scrolling and ensure predictable rendering across different viewport sizes.

Only the **most important** badges SHOULD appear in this cluster — for example release or package version, SPDX or registry license, primary package-manager or registry link, and at most one or two other high-signal shields. The cluster SHOULD contain **at most about five** images; exceeding that without moving lower-priority badges elsewhere SHOULD be treated as a formatting concern by validators.

#### 5.6.3 Body placement — Project status and beyond
**Less important** or frequently updating badges (CI build status, test pass matrices, coverage percentage, code-quality or security-scan summaries, dependency freshness, and similar) SHOULD **not** all compete for space in the header cluster. They SHOULD appear **later in the document**, where the **Project status** section (§3.3.5) is the most natural fit, optionally alongside a short prose description of maintenance state.

Additional badges MAY appear under other body headings (for example a dedicated **Badges** section per §3.4.6) when that improves scanability, provided the overall document still respects §5.6.5.

#### 5.6.4 Allowed badge types
Badges MAY be used to convey status information such as version, build status, or license. Each badge MUST provide meaningful and accurate information.

#### 5.6.5 Overall density and badge walls
The **total** number of badges in the README MUST remain bounded so the file does not become a decorative shield farm. Excessive badge usage that overwhelms the visual layout — especially a **wall of badges** before the reader has seen title, summary, and proof — is non-compliant (§8.3.1). Validators SHOULD enforce both a **per-document** maximum (configurable) and the **header-cluster** cap in §5.6.2.

---

### 5.7 Emoji and pictographs

#### 5.7.1 Non-requirement, encouragement, and scoring
Emoji and related Unicode pictographs are **not** mandatory. They MAY be used when they **genuinely aid scanning** or convey a concept faster than words alone. They SHOULD be applied **wisely and sparingly** across the whole document.

A reference validator MAY apply a **small positive scoring adjustment** when emoji use stays within configured limits **and** the **Features** section (§3.3.2) uses a **consistent** pattern of at most one meaningful leading pictograph per top-level bullet, so that restraint is rewarded without requiring emoji.

#### 5.7.2 Natural fit — the Features section
The **Features** section SHOULD be the primary home for intentional emoji: each top-level capability line MAY start with a single pictograph chosen for **semantic fit** (the symbol SHOULD suggest the feature’s theme, not arbitrary decoration). Mixing lines that start with emoji and lines that do not in the same list SHOULD be avoided once emoji are introduced (uniformity aids reading).

#### 5.7.3 Density and placement elsewhere
Outside **Features**, emoji SHOULD appear rarely — for example an occasional call-out — and MUST NOT dominate headings, the summary, or dense technical tables. A validator SHOULD flag **over-concentration** of pictographs relative to document length using configurable thresholds.

#### 5.7.4 Accessibility and tone
Emoji are not universally rendered or perceived the same way across platforms, cultures, and assistive technologies. Authors SHOULD prefer plain language where clarity would otherwise depend on a specific glyph, and MUST NOT rely on emoji alone to convey safety-critical or contractual meaning.

---

### 5.8 Navigation Enhancements

#### 5.8.1 Table of Contents
A table of contents SHOULD be included for longer READMEs. If the README exceeds **100 lines** in source length, a table of contents MUST be provided to support navigation. It MUST reflect the actual heading structure and provide accurate links.

#### 5.8.2 Quick Links Sections
Quick navigation links MAY be included to highlight key sections. These links SHOULD be concise and positioned to improve usability.

#### 5.8.3 Anchor Links
Internal links SHOULD reference section anchors consistently. Broken or unstable links are not permitted.

---

## 6. Writing Style Specification

### 6.1 Tone

#### 6.1.1 Technical Precision
The README MUST use precise and unambiguous language. Statements SHOULD be verifiable and grounded in actual functionality. Authors SHOULD prioritize clarity and utility over perfect adherence to complex grammatical rules; a README that is technically accurate and easy to follow is superior to one that is linguistically dense but difficult to parse.

#### 6.1.2 Neutral Confidence
The tone SHOULD be confident and informative without exaggeration. Promotional language that lacks substance is not permitted.

#### 6.1.3 Avoidance of Marketing Hyperbole
Terms that do not convey measurable or observable meaning MUST be avoided. Claims SHOULD be supported by examples or evidence.

---

### 6.2 Sentence Structure

#### 6.2.1 Short Sentences
Sentences SHOULD be concise and direct. Complex constructions SHOULD be avoided where simpler alternatives suffice.

#### 6.2.2 Active Voice
Active voice MUST be used for all procedural steps and instructions (for example, "Install the dependency" instead of "The dependency should be installed"). Active voice SHOULD be preferred elsewhere to improve general clarity and readability. Passive constructions SHOULD be used only when the object being acted upon is more important than the actor.

#### 6.2.3 Declarative Statements
Statements SHOULD be declarative and informative. Instructions MUST be clear and actionable.

---

### 6.3 Vocabulary

#### 6.3.1 Domain-Specific Terminology
Technical terms SHOULD be used where appropriate and MUST be consistent. Terms that may be unfamiliar SHOULD be defined or contextualized.

#### 6.3.2 Avoidance of Buzzwords
Vague or fashionable terminology that does not add meaning MUST be avoided. Language SHOULD remain functional and precise.

#### 6.3.3 Concrete claims over empty intensifiers
Marketing-style intensifiers that do not convey verifiable properties — for example **“powerful,” “revolutionary,” “cutting-edge,” “robust,” “elegant,” “enterprise-grade,”** or similar — SHOULD be avoided in favour of **observable claims** (what the software does, for whom, under which constraints, with what measurable outcome). The same rhetorical rule applies to **feature bullets**: each line SHOULD read like a **user-visible benefit** or capability, not a generic compliment that could apply to many unrelated projects (see §8.2.1).

#### 6.3.4 Inclusive Language
The README MUST use inclusive and respectful language that avoids bias, stereotypes, or exclusionary terminology. Authors SHOULD follow established best practices for bias-free communication (for example, avoiding "master/slave", "whitelist/blacklist", or gendered pronouns where neutral forms suffice). Words SHOULD be chosen to be anti-racist, empathetic, and accessible to a global audience.

---

### 6.4 Formatting for Scanability

#### 6.4.1 Bullet Lists
Bullet lists MAY be used when they improve clarity, particularly for enumerations of more than three items. Lists MUST remain concise and structured.

#### 6.4.2 Section Chunking
Content SHOULD be divided into logical sections with clear headings. Each section MUST convey a single primary idea.

#### 6.4.3 Highlighting Key Concepts
Key terms or phrases MAY be emphasized to support scanning. Emphasis MUST remain consistent and restrained.

---

### 6.5 Language and Readability (Cross-Reference)

Normative requirements for **English as the primary README language**, **non-English addenda**, and **quantitative readability targets** are defined in **§4.5** and **§4.6**. Writing-style guidance in §6.1–§6.4 **SHOULD** be interpreted consistently with those sections: tone and vocabulary choices **SHOULD** keep automated readability scores within configured limits where measurement is available.

---

## 7. Advanced Enhancements

### 7.1 Visual Enhancements

#### 7.1.1 Logos
A README MAY include a logo or visual identity element to reinforce recognition and branding. Such elements SHOULD be placed near the top of the document and MUST not displace or obscure the title or summary.

#### 7.1.2 Animations
Animations, including GIFs, MAY be used to demonstrate workflows or interactions that are difficult to convey through static images. They SHOULD be concise, performant, and directly relevant to the functionality being illustrated.

#### 7.1.3 Interactive Media
Interactive elements, such as embedded demos or external sandbox links, MAY be provided to allow users to experiment with the project. These elements SHOULD be clearly labeled and MUST not replace essential textual instructions.

#### 7.1.4 Call to Action (CTA)
A README MAY include a Call to Action (CTA) — such as "Get Started", "Try it now", or "Join our Discord" — typically placed near the end of the summary or after a major instructional block. CTAs SHOULD only be included when they lead to a high-value internal or external resource that directly progresses the user journey. Authors SHOULD avoid redundant or multiple CTAs that compete for attention.

---

### 7.2 Dynamic Content

#### 7.2.1 Generated Badges
Badges generated from external services MAY be included to display real-time information such as build status or versioning. These badges MUST be reliable and SHOULD degrade gracefully if external services are unavailable. Authors SHOULD prefer placing volatile CI, test, and quality badges in the **body** (for example under **Project status**, §3.3.5) rather than expanding the **header cluster** beyond the guidance in §5.6.2. A badge that shows a **failing** or **unknown** state is still a trust signal: it communicates **risk** to the reader and MUST NOT be treated as decorative; maintainers SHOULD either fix the underlying issue or remove misleading shields.

#### 7.2.2 Live Data Widgets
Dynamic widgets displaying statistics or activity MAY be used in contexts where such information provides value. Their inclusion MUST be justified and SHOULD not distract from core content.

#### 7.2.3 CI-Driven Updates
Automation MAY be used to update sections of the README, such as version numbers or generated tables. Automated updates MUST preserve readability and MUST NOT introduce instability or inconsistency.

---

### 7.3 Tooling Ecosystem

#### 7.3.1 README Generators
Tools that generate README templates MAY be used to establish initial structure. Generated content MUST be reviewed and adapted to meet the requirements of this specification.

#### 7.3.2 Linters and Validators
Automated tools SHOULD be used to validate compliance with this specification. Such tools MAY enforce section presence, formatting rules, and link integrity.

#### 7.3.3 Template Systems
Reusable templates MAY be employed to standardize README creation across projects. Templates MUST remain flexible and SHOULD not enforce irrelevant sections.

---

## 8. Anti-patterns

### 8.1 Structural Anti-patterns

#### 8.1.1 Missing Sections
A README that omits required sections is non-compliant. Missing installation, usage, or license information significantly reduces usability and MUST be avoided.

#### 8.1.2 Misordered Sections
Sections presented in an order that contradicts the cognitive funnel degrade comprehension. Placing advanced or internal details before basic usage is not permitted.

#### 8.1.3 Overloaded README
A README that attempts to include all documentation within a single file becomes difficult to navigate and maintain. Excessive length without proper structuring or delegation is discouraged.

#### 8.1.4 Structural Inconsistency
Skipping header levels (for example, using H4 immediately after H2) or using duplicate headers at the same level disrupts document navigation and table-of-contents generation. Such structural gaps are non-compliant (§5.1.2).

#### 8.1.5 Manifest Dissociation
A README title that does not match the project name in the primary manifest (for example `package.json`) creates ambiguity and trust issues. This dissociation is non-compliant for projects with explicit metadata (§3.2.1.1).

---

### 8.2 Content Anti-patterns

#### 8.2.1 Vague Descriptions
Descriptions that fail to convey concrete meaning or actionable understanding are not acceptable. Statements lacking specificity reduce clarity and trust.

#### 8.2.2 Missing Examples
The absence of examples prevents users from understanding how to use the project. A compliant README MUST include demonstrative content.

#### 8.2.3 Hidden Requirements
Unstated prerequisites or implicit assumptions create barriers to use. All necessary conditions for execution MUST be explicitly documented.

#### 8.2.4 Non-English or mixed-language gatekeeping
A README whose **primary** prose is not English, or that buries installation, licensing, or safety information only in a non-English section without an equivalent English exposition, is non-compliant with §4.5. Using another language **only** for decorative slogans while substantive content remains English is permitted; the anti-pattern is **information asymmetry** across languages.

#### 8.2.5 Academic or specification-style density in a README
Prose that consistently scores **far beyond** the configured Flesch–Kincaid, Gunning Fog, SMOG, or Dale–Chall limits (§4.6.3) behaves like an internal white paper pasted into the repository’s storefront. It **SHOULD** be refactored or moved to dedicated documentation, with the README retaining a clearer, shorter summary and links.

---

### 8.3 Visual Anti-patterns

#### 8.3.1 Badge Spam
Excessive use of badges overwhelms the visual hierarchy and obscures essential information. Badge usage MUST remain restrained and purposeful. In particular, stacking many shields **before** the title or summary, or placing more than a handful of badges **between** the title and the summary paragraph instead of moving them to **Project status** or the body (§5.6.2–§5.6.3), constitutes the **badge wall** anti-pattern.

#### 8.3.2 Emoji overload
Sprinkling emoji throughout every heading, list, and paragraph — or using many pictographs unrelated to the adjacent text — creates noise, weakens professional tone, and can impede accessibility. Such **emoji soup** MUST be avoided; density SHOULD follow §5.7.3, and intentional emoji SHOULD concentrate in **Features** (§5.7.2) when used at all.

#### 8.3.3 Decorative Images
Images that do not contribute to understanding or usability are not permitted. Visual elements MUST serve a clear explanatory function.

#### 8.3.4 Poor Formatting
Inconsistent headings, lack of spacing, or misuse of emphasis reduces readability. Formatting MUST support structure and comprehension.

#### 8.3.5 Code Block Pollution
Including shell prompt characters (for example `$`, `>`, or `%`) in code blocks that are intended for copying and execution is non-compliant (§3.2.3.1). These characters interfere with CLI operations and increase user error.

#### 8.3.6 Placeholder Ambiguity
Using `<angle-brackets>` for placeholders in commands is discouraged as they may be misinterpreted as HTML tags or system variables. Failure to use `UPPERCASE` for user-replaceable fields is non-compliant (§3.2.4.2).

---

### 8.4 Maintenance Anti-patterns

#### 8.4.1 Outdated Instructions
Instructions that no longer reflect the current state of the project undermine trust and usability. The README MUST be kept up to date.

#### 8.4.2 Broken Links
Links to documentation, resources, or examples that do not resolve are not acceptable. Link integrity MUST be maintained.

#### 8.4.3 Missing Status
Failure to communicate the project's maintenance state creates uncertainty. A compliant README SHOULD disclose status explicitly.

---

## 9. Validation and Compliance

### 9.1 Compliance Levels

#### 9.1.1 Minimal Compliance
A README is minimally compliant if all required sections defined in this specification are present and contain sufficient information to enable basic understanding and execution. Minimal compliance ensures functional usability but does not guarantee optimal clarity or completeness.

#### 9.1.2 Recommended Compliance
A README achieves recommended compliance when it includes both required and recommended sections, follows ordering rules, and satisfies content and formatting requirements. At this level, the README supports efficient evaluation, onboarding, and continued use.

#### 9.1.3 Strict Compliance
Strict compliance is achieved when a README adheres fully to all requirements and recommendations, including visual, structural, and stylistic guidelines. A strictly compliant README demonstrates high clarity, reproducibility, and maintainability, and is suitable for automated validation.

---

### 9.2 Validation Checklist

#### 9.2.1 Section Presence
Validation MUST confirm the presence of all required sections and SHOULD verify the inclusion of recommended sections where applicable. Each section MUST contain meaningful content and not merely placeholders.

#### 9.2.2 Content Quality
Validation SHOULD assess clarity, completeness, and reproducibility. Instructions MUST be actionable, examples MUST be correct, and descriptions MUST be specific.

#### 9.2.3 Formatting Rules
Validation SHOULD verify compliance with formatting requirements, including heading structure, code block usage, and image handling. Inconsistent or incorrect formatting is considered non-compliant.

#### 9.2.4 Language and readability
Validation **SHOULD** confirm that aggregated prose is classified as English (§4.5.5) and **SHOULD** measure readability statistics (§4.6.3) when prose length exceeds configured minima. Violations **SHOULD** map to the **content** quality domain in weighted scoring.

---

### 9.3 Automated Validation

#### 9.3.1 Linting Rules
Automated linters MAY be used to enforce structural and formatting rules. Such tools SHOULD detect missing sections, invalid links, and improper heading hierarchies.

#### 9.3.2 CI Integration
Validation tools SHOULD be integrated into continuous integration pipelines. Non-compliant README files SHOULD trigger warnings or failures depending on enforcement level.

#### 9.3.3 Schema Definitions
A machine-readable schema MAY be defined to represent this specification. Such a schema SHOULD enable automated checking of section presence, ordering, and content constraints.

---

## 10. Repository Context Integration

### 10.1 Related Files

#### 10.1.1 CONTRIBUTING.md
A repository SHOULD include a CONTRIBUTING file that defines how contributions are made. The README MUST link to this file where contributions are encouraged.

#### 10.1.2 LICENSE
A LICENSE file MUST be present in the repository. The README MUST reference this file and clearly state the applicable license. The LICENSE file itself MUST contain a valid copyright notice that names the copyright owner — omitting the owner renders the notice legally void (see §3.2.9.3).

#### 10.1.3 CODE_OF_CONDUCT.md
Where applicable, a code of conduct SHOULD be provided. The README SHOULD link to this document to communicate community expectations.

#### 10.1.4 ARCHITECTURE.md
For complex projects, an architecture document MAY be included. The README SHOULD reference this file instead of embedding detailed architectural explanations.

#### 10.1.5 package.json (and equivalent manifests)
When the repository contains a `package.json` file (or an equivalent package manifest such as `Cargo.toml`, `pyproject.toml`, `go.mod`, etc.), the README MUST be consistent with the metadata declared therein. Specifically:

- **Name.** The `name` field MUST appear in the README title (H1) or summary paragraph. A README that titles itself differently from the published package name creates a discoverability gap and erodes user trust.
- **Description.** The `description` field SHOULD be consistent with the summary paragraph or introductory text of the README. Minor wording differences are acceptable, but the core meaning MUST NOT contradict.
- **License.** The `license` field MUST match the license stated in the README's License section and in the `LICENSE` file. A three-way mismatch between `package.json`, `LICENSE`, and the README constitutes a compliance violation (see also §10.1.2).
- **Engines / runtime constraints.** When `engines` (or equivalent fields) declares minimum runtime versions, the README SHOULD reflect these constraints in its installation or prerequisites section, or via relevant badges. Users who encounter version errors at install-time because the README omitted this information face an unnecessary friction point.
- **Version.** The `version` field SHOULD be consistent with any version references, badges, or changelogs mentioned in the README.

Discrepancies between the package manifest and the README erode trust, confuse users who consult both sources, and may cause downstream tooling (registry pages, documentation generators) to display contradictory information. Automated validation tools SHOULD flag such mismatches.

#### 10.1.6 Third-party dependencies
When the repository declares external third-party packages (for example via the `dependencies` field of `package.json`, or via equivalent sections in other package manifests such as `Cargo.toml`, `requirements.txt`, or `go.mod`), the README MUST clearly disclose that the project relies on external software, and MUST list every such direct dependency by its declared package identifier (the same name used in the manifest).

Each listed dependency MUST be a hyperlink to a canonical package registry page (for npm packages, `https://www.npmjs.com/package/…`) or to the upstream source repository URL on a forge such as GitHub. Plain-text package names without a URL are insufficient. When authors use raw HTML for these links, the anchor MUST include `target="_blank"` and SHOULD include `rel="noopener noreferrer"` so registry and repository pages open in a new browsing context. Standard Markdown link syntax (`[label](https://…)`) satisfies the linking requirement where HTML `target` cannot be expressed; site generators and hosts that rewrite external links MAY apply `target` behaviour separately.

When **more than three** distinct external dependencies are declared, the README MUST present them as a **bullet list** (or equivalent explicit list structure such as an ordered list), with **one dependency per list item**, not as a single prose paragraph. Three or fewer dependencies MAY be listed inline in a short paragraph, still with each identifier hyperlinked as above.

Readers MUST be able to discover which third-party components the project depends on without opening the manifest alone. Omitting this information obscures supply-chain, licensing, and security posture. Development-only packages (`devDependencies` and their equivalents) MUST be listed as well, unless the README explicitly scopes a subsection to production-only dependencies and separately documents development tooling with the same identifier-level clarity.

Automated validators SHOULD read the repository's primary manifest (typically `package.json` at the repository root) and verify that each direct external dependency appears with a qualifying link, that list formatting meets the paragraph-versus-list rule, and that raw HTML anchors to registries or forges declare `target="_blank"` as required. Validators MAY exclude manifest entries that are clearly workspace-local (for example `workspace:` protocol specifiers) from this requirement.

---

### 10.2 Documentation Architecture

#### 10.2.1 README vs Docs
The README MUST serve as an entry point rather than a comprehensive documentation system. Detailed content SHOULD be delegated to dedicated documentation files.

#### 10.2.2 Splitting Strategies
When a README becomes excessively long or complex, content SHOULD be split into modular documents. The README MUST retain a clear overview and link to these documents.

#### 10.2.3 Linking Conventions
Links between documentation files MUST be consistent and SHOULD use relative paths where applicable. Navigation between documents SHOULD be predictable and stable.

---

## 11. Adaptation Guidelines

### 11.1 By Project Type

#### 11.1.1 Libraries
For libraries, the README SHOULD emphasize installation, API usage, and integration scenarios. Examples SHOULD demonstrate typical developer workflows.

#### 11.1.2 CLI Tools
For command-line tools, the README SHOULD prioritize command syntax, options, and output examples. Quickstart instructions MUST enable immediate execution.

#### 11.1.3 Applications
For applications, the README SHOULD highlight functionality, screenshots, and user workflows. Installation and setup instructions MUST address deployment contexts.

#### 11.1.4 Research Projects
For research projects, the README SHOULD emphasize reproducibility, data sources, and experimental setup. Instructions MUST enable replication of results.

#### 11.1.5 Documentation Repository
A Documentation Repository (for example a project containing only specifications, meeting notes, or prose) is a specialized project type where **execution** is not the primary goal. Such repositories are **exempt** from mandatory **Installation** (§3.2.4) and **Quickstart** (§3.2.5) sections. To be compliant, they MUST instead provide a clear **Overview** and **Contribution** entry points.

---

### 11.2 By Audience

#### 11.2.1 Developers
When targeting developers, the README SHOULD focus on integration, configuration, and extensibility. Technical clarity MUST be prioritized.

#### 11.2.2 End Users
For end-user audiences, the README SHOULD emphasize usability, features, and interaction. Technical detail SHOULD be minimized where unnecessary.

#### 11.2.3 Contributors
For contributors, the README SHOULD provide entry points to development workflows and guidelines. It MUST clearly indicate where further information can be found.

---

## 12. Future Work and Extensions

### 12.1 Machine-Readable README Schemas
Future work MAY include formal schema definitions that enable automated generation and validation of README files. Such schemas SHOULD align with this specification.

### 12.2 Integration with Package Registries
Integration with package registries MAY allow enhanced rendering and validation of README files. Standardization efforts SHOULD consider these environments.

### 12.3 AI-Assisted README Generation
AI systems MAY assist in generating README content based on code and metadata. Such systems MUST adhere to the requirements defined in this specification.

### 12.4 Standardization Efforts
Further standardization MAY emerge through community adoption and tooling integration. This specification SHOULD evolve in response to such developments.

---

## Appendices

### A. Reference Templates

#### A.1 Minimal Compliant Template
A minimal template SHOULD include all required sections with concise content. It MUST enable basic understanding and execution.

#### A.2 Full Featured Template
A full template SHOULD include required and recommended sections, structured according to this specification. It SHOULD serve as a reference for comprehensive READMEs.

#### A.3 Domain-Specific Variants
Templates MAY be adapted for specific domains such as libraries, CLI tools, or research projects. Variants MUST remain consistent with core requirements.

---

### B. Example Fully Compliant README

#### B.1 Annotated Example

Below is a canonical, fully compliant README that satisfies the requirements of this specification.

---

# Salve — Locale-aware Greeting Engine for Modern Applications

Salve is a lightweight, extensible engine for generating culturally and temporally appropriate greetings in applications, based on locale, calendar data, and contextual signals.

```javascript
import { greet } from "salve";

greet({
  locale: "en-GB",
  timeZone: "Europe/Brussels",
  date: new Date()
});
// → "Good morning"
```

---

## Installation

```bash
npm install salve
```

Salve requires Node.js ≥ 18 or a compatible runtime (Deno, Bun, or modern browsers with ES modules).

---

## Quickstart

```javascript
import { greet } from "salve";

const message = greet({
  locale: "fr-FR",
  timeZone: "Europe/Paris"
});

console.log(message);
```

Expected output:

```text
Bonjour
```

---

## Usage

### Basic Greeting

```javascript
greet({ locale: "en-US" });
// → "Hello"
```

> [!TIP]
> Use the static `greet` method for standard one-off greetings where state persistence is not required.

### Time-aware Greeting

```javascript
greet({
  locale: "en-US",
  timeZone: "America/New_York",
  date: new Date("2026-04-09T08:00:00")
});
// → "Good morning"
```

### Custom Data Packs

To load a custom pack, replace `PACK-NAME` with the identifier found in the [Data Pack Registry](https://...):

```javascript
greet({
  locale: "el-GR",
  packs: ["PACK-NAME"]
});
```

---

## Why Salve

Most applications use static or naive greeting logic that ignores cultural context, time, and calendar traditions. Salve separates greeting logic from UI code and enables context-aware greetings through modular data packs and deterministic rules.

---

## Features

- 🌍 **Locale-aware** — Supports BCP 47 identifiers.
- 🕒 **Temporal Precision** — Timezone-sensitive output.
- 🔌 **Extensible** — Pluggable calendar and name-day systems.
- 📦 **Lightweight** — Minimal core with optional datasets.
- 🚀 **Polyglot** — Compatible with Node, Deno, Bun, and browsers.

---

## Configuration

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `locale` | `string` | system locale | BCP 47 locale identifier |
| `timeZone` | `string` | system TZ | IANA timezone |
| `packs` | `string[]` | `[]` | Optional data packs |

---

## Examples

- [Basic usage](./examples/basic.ts)
- [Advanced calendar usage](./examples/calendar.ts)

---

## Project Status

Salve is currently in **beta**. The API is stable, but additional data packs and locale support are under active development.

---

## Limitations

Salve does not currently include full CLDR datasets by default and does not attempt automatic inference of user intent beyond explicit parameters.

---

## Documentation

Full documentation is available at:
[https://example.com/salve/docs](https://example.com/salve/docs)

---

## Support

- Bug reports: [https://github.com/example/salve/issues](https://github.com/example/salve/issues)
- Discussions: [https://github.com/example/salve/discussions](https://github.com/example/salve/discussions)

---

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## License

MIT License — see [LICENSE](./LICENSE)

---

#### B.2 Compliance Mapping

This subsection maps the example README to the specification requirements.

The example satisfies all **required sections**, including title, summary, demonstration, installation, quickstart, usage, documentation, support, and license. Each section contains explicit, actionable content and avoids placeholders.

It also includes **recommended sections**, such as motivation, features, configuration, examples, project status, limitations, and contributing, demonstrating recommended compliance level.

Formatting adheres to **visual and Markdown requirements**, including structured headings, syntax-highlighted code blocks, relative links, and tabular configuration. Code examples are minimal, executable, and paired with expected output where applicable.

The document follows the **cognitive funnel ordering**, beginning with identity and demonstration, progressing through installation and quickstart, and concluding with reference, support, and governance sections.

No anti-patterns are present. The README avoids excessive badges, vague language, redundant sections, or decorative noise.

---

### C. Validation Checklist Summary

This appendix (subsections **C.1** onward) collects the human checklist, machine validation schema, validator design, CLI and API sketches, scoring model, and related implementation guidance for README linting and CI. For **informative-only** notes on optional **token-size heuristics** in validator output—which MUST NOT affect compliance level, primary score, or exit semantics—see [C.23 Token Estimation and Document Size Informatics (Informative)](#c23-token-estimation-and-document-size-informatics-informative).

#### C.1 Human Checklist
A checklist SHOULD be provided to guide manual review of README compliance. It MUST cover structure, content, and formatting.

#### C.2 Machine Validation Schema

The following YAML schema is a normative, machine-readable representation of the core validation model implied by Section 9.3. It is intended as a practical basis for README linting, CI enforcement, and future CLI tooling. It does not attempt full semantic validation of prose quality, but it does formalize structure, ordering, presence rules, selected formatting constraints, and section-level metadata.

This schema is intentionally expressed in YAML rather than JSON, because the specification favors human-readable configuration and inspection. The schema is divided into five layers: document metadata, section taxonomy, ordering rules, content rules, and rendering or formatting constraints. A validator MAY implement this schema directly, or MAY compile it into an internal rule engine.

```yaml
schema:
  id: rrs-readme-schema
  title: Repository README Specification Validation Schema
  version: 0.1.0
  status: draft
  description: >
    Machine-readable validation schema for repository README files conforming
    to the Repository README Specification (RRS).
  normative_language:
    must: absolute requirement
    should: strong recommendation
    may: optional behavior

document:
  target_file_names:
    - README.md
    - readme.md
  preferred_file_name: README.md
  encoding: utf-8
  markup:
    required: github_flavored_markdown
    disallow_nonstandard_required_extensions: true
  rendering_contexts:
    - github
    - npm
  limits:
    recommended_max_rendered_size_kib: 500

compliance_levels:
  minimal:
    description: >
      Requires all mandatory sections and basic structural validity.
    requires:
      - required_sections_present
      - required_ordering_constraints
      - core_content_present
  recommended:
    description: >
      Requires minimal compliance plus recommended sections and formatting quality.
    requires:
      - minimal
      - recommended_sections_present_when_applicable
      - formatting_constraints
      - navigation_quality
  strict:
    description: >
      Requires recommended compliance plus all enforced stylistic, ordering,
      and media constraints supported by the validator.
    requires:
      - recommended
      - strict_order_validation
      - enhanced_content_validation
      - link_integrity
      - media_accessibility

section_taxonomy:
  required_sections:
    - id: title
      heading_required: false
      description: >
        Top-of-file project title. Usually H1.
      must_appear_first_noncomment_block: true
      allowed_markdown_nodes:
        - heading
      heading_level:
        exact: 1

    - id: summary
      heading_required: false
      description: >
        Short value proposition immediately following the title.
      required_after: title
      allowed_markdown_nodes:
        - paragraph
        - blockquote
      min_paragraphs: 1
      max_paragraphs: 2
      content_rules:
        must_describe:
          - what_the_project_is
          - intended_user_or_use_case
          - primary_benefit

    - id: proof
      heading_required: false
      description: >
        Immediate proof element near the top of the README.
      required_after: summary
      allowed_markdown_nodes:
        - fenced_code_block
        - image
        - paragraph
      min_items: 1
      content_rules:
        at_least_one_of:
          - executable_code_example
          - screenshot
          - gif
          - terminal_output_example

    - id: installation
      heading_required: true
      canonical_headings:
        - Installation
      heading_level:
        min: 2
        max: 3
      must_exist: true
      content_rules:
        must_include_one_of:
          - shell_install_command
          - package_registry_install_instructions
          - platform_install_steps
        should_include:
          - prerequisites
          - runtime_version

    - id: quickstart
      heading_required: true
      canonical_headings:
        - Quickstart
        - Getting Started
      heading_level:
        min: 2
        max: 3
      must_exist: true
      content_rules:
        must_include:
          - minimal_executable_flow
          - success_condition
        should_include:
          - expected_output

    - id: usage
      heading_required: true
      canonical_headings:
        - Usage
        - Examples
      heading_level:
        min: 2
        max: 3
      must_exist: true
      content_rules:
        must_include:
          - at_least_one_task_or_scenario
        should_include:
          - progressive_examples
          - common_use_cases

    - id: documentation
      heading_required: true
      canonical_headings:
        - Documentation
        - Further Reading
        - Docs
      heading_level:
        min: 2
        max: 3
      must_exist: true
      content_rules:
        must_include:
          - at_least_one_doc_link_or_reference

    - id: support
      heading_required: true
      canonical_headings:
        - Support
        - Help
        - Questions
      heading_level:
        min: 2
        max: 3
      must_exist: true
      content_rules:
        must_include_one_of:
          - issue_tracker_link
          - discussion_link
          - contact_route
        should_include:
          - security_reporting_route

    - id: license
      heading_required: true
      canonical_headings:
        - License
      heading_level:
        min: 2
        max: 3
      must_exist: true
      content_rules:
        must_include:
          - license_name_or_identifier
        should_include:
          - link_to_license_file

  recommended_sections:
    - id: why
      canonical_headings:
        - Why
        - Motivation
        - Why this project exists
    - id: features
      canonical_headings:
        - Features
        - Key Features
        - Highlights
    - id: configuration
      canonical_headings:
        - Configuration
        - Options
        - Settings
    - id: examples
      canonical_headings:
        - Examples
        - More Examples
    - id: project_status
      canonical_headings:
        - Project Status
        - Status
        - Stability
    - id: limitations
      canonical_headings:
        - Limitations
        - Non-goals
        - Constraints
    - id: contributing
      canonical_headings:
        - Contributing
        - Contribution
    - id: roadmap
      canonical_headings:
        - Roadmap
        - Future Work
    - id: acknowledgements
      canonical_headings:
        - Acknowledgements
        - Acknowledgments
        - Credits
        - Thanks
    - id: prior_art
      canonical_headings:
        - Prior art
        - Prior Art
        - Related work
        - Related Work
        - Other implementations
        - Other Implementations
        - Related projects
        - Related Projects
        - Similar projects
        - Similar Projects

  optional_sections:
    - id: architecture
      canonical_headings:
        - Architecture
        - Architecture Overview
    - id: faq
      canonical_headings:
        - FAQ
        - Frequently Asked Questions
    - id: benchmarks
      canonical_headings:
        - Benchmarks
        - Performance
    - id: comparisons
      canonical_headings:
        - Comparisons
        - Alternatives
    - id: screenshots
      canonical_headings:
        - Screenshots
        - Gallery
    - id: badges
      canonical_headings:
        - Badges
    - id: demo
      canonical_headings:
        - Demo
        - Live Demo

ordering:
  required_sequence:
    - title
    - summary
    - proof
    - installation
    - quickstart
    - usage
  terminal_sections:
    - documentation
    - support
    - license
  ordering_rules:
    - id: no_badge_wall_before_identity
      description: >
        Badge clusters must not appear before the title or summary.
      severity: error
    - id: installation_before_advanced_reference
      description: >
        Installation and Quickstart must precede advanced sections such as
        architecture, FAQ, benchmarks, or roadmap.
      severity: error
    - id: license_near_end
      description: >
        License must appear in the final third of the document unless the
        document is unusually short.
      severity: warning
    - id: support_near_end
      description: >
        Support should appear after primary usage information.
      severity: warning

content_rules:
  top_of_file:
    max_nonempty_blocks_before_value_clarity: 5
    must_establish:
      - identity
      - purpose
      - benefit
  summary:
    recommended_max_sentences: 2
    disallow_generic_only_claims:
      - powerful
      - robust
      - cutting-edge
      - revolutionary
      - enterprise-grade
  examples:
    at_least_one_code_block_required: true
    recommended_max_lines_per_example: 15
    require_language_tag_on_fenced_code: true
    should_include_expected_output: true
  installation:
    require_actionable_commands: true
    disallow_placeholder_commands: true
  quickstart:
    require_copy_pasteable_path: true
    require_success_condition: true
  links:
    internal_links_should_be_relative: true
    external_links_must_use_https_when_available: true
  license:
    must_reference_existing_license_file_when_present: true

formatting_rules:
  headings:
    require_single_h1: true
    max_heading_depth_recommended: 4
    disallow_skipped_heading_levels: false
    heading_text_must_not_be_empty: true
  paragraphs:
    recommended_max_sentences_per_paragraph: 4
  emphasis:
    excessive_bold_ratio_warning_threshold: 0.15
    excessive_italic_ratio_warning_threshold: 0.10
  lists:
    discourage_consecutive_long_lists: true
  code_blocks:
    require_language_tag: true
    discourage_blocks_over_lines: 30
  tables:
    allow_configuration_tables: true
    discourage_large_unexplained_tables: true

media_rules:
  images:
    alt_text_required: true
    repository_local_paths_should_be_relative: true
    decorative_only_images_disallowed: true
  gifs:
    allowed: true
    must_be_functionally_relevant: true
    recommended_max_count: 3
  badges:
    allowed: true
    recommended_max_count: 6
    allowed_categories:
      - build
      - test
      - coverage
      - version
      - license
      - downloads
      - docs
    disallowed_as_primary_content: true

navigation:
  toc:
    recommended_for_min_heading_count: 8
    must_match_existing_headings: true
  anchor_links:
    must_resolve: true
  quick_links:
    allowed: true
    recommended_max_links: 8

link_validation:
  internal:
    must_resolve_to_existing_paths_or_anchors: true
  external:
    should_be_checked: true
    allow_ignore_patterns:
      - "^mailto:"
      - "^#"

project_context:
  should_reference_related_files:
    - CONTRIBUTING.md
    - LICENSE
    - CODE_OF_CONDUCT.md
    - ARCHITECTURE.md
  related_file_rules:
    contributing:
      if_repository_has_file: CONTRIBUTING.md
      then_readme_should_link: true
    license:
      if_repository_has_file: LICENSE
      then_readme_must_link: true

anti_patterns:
  errors:
    - missing_required_section
    - missing_installation
    - missing_quickstart
    - missing_license
    - no_demonstration
    - badge_wall_before_title
    - decorative_image_without_explanatory_value
    - broken_internal_anchor
    - hidden_prerequisites
  warnings:
    - vague_summary
    - too_many_badges
    - oversized_code_example
    - outdated_status_language
    - missing_project_status
    - architecture_before_usage
    - overloaded_readme
    - broken_external_link

validator_hints:
  parsing:
    heading_detection: markdown_ast
    code_fence_detection: markdown_ast
    image_detection: markdown_ast
    link_detection: markdown_ast
  semantic_checks:
    summary_quality:
      heuristic: true
    prerequisite_detection:
      heuristic: true
    success_condition_detection:
      heuristic: true
    example_output_detection:
      heuristic: true
  scoring:
    enabled: true
    weights:
      required_sections_present: 30
      ordering_compliance: 15
      example_quality: 15
      installation_quality: 10
      quickstart_quality: 10
      formatting_quality: 10
      accessibility_and_media: 5
      link_integrity: 5

reporting:
  output_formats:
    - text
    - json
    - yaml
  include:
    - compliance_level
    - passed_rules
    - failed_rules
    - warnings
    - score
    - suggested_fixes
```

Some rules are strictly machine-checkable, such as section presence, heading depth, code-fence language tags, relative image paths, and badge count. Other rules, such as whether a summary is too vague or whether a quickstart genuinely leads to first success, are only partially machine-checkable and therefore appear as heuristic checks. A validator SHOULD distinguish clearly between hard failures and heuristic warnings.

The schema assumes AST-based Markdown parsing rather than raw regular-expression matching, as that is the more reliable basis for a future npm package or CLI validator.

---

#### C.3 Validator Design

##### C.3.1 Purpose and Scope
The validator defined in this appendix is a reference implementation model for automated enforcement of the Repository README Specification. Its purpose is to inspect a repository README, determine compliance against the normative and recommended rules of this specification, emit structured diagnostics, and integrate predictably into local development workflows and continuous integration pipelines.

The validator is not intended to judge literary merit in a fully semantic sense. Its primary role is to enforce structural correctness, detect common anti-patterns, validate navigational and formatting integrity, and apply bounded heuristics for content quality where such checks are feasible and explainable.

##### C.3.2 Design Principles
The validator SHALL be deterministic, explainable, and conservative in its claims. It MUST distinguish clearly between hard violations of normative requirements and heuristic findings that merely suggest reduced quality or probable non-compliance.

The validator SHOULD be usable in three modes: interactive local use, CI enforcement, and machine-readable batch analysis. It SHOULD therefore provide human-readable output, stable exit semantics, and structured report formats suitable for further tooling.

The validator MUST treat README validation as a layered process. Syntactic and structural validation SHALL precede higher-level checks, and repository-context checks SHALL be performed only after the README itself has been parsed successfully.

---

#### C.4 Validation Architecture

##### C.4.1 Processing Pipeline
The validator SHOULD process a repository in a fixed sequence of phases. Each phase MUST produce artifacts that can be reused by later phases and SHOULD fail gracefully where partial analysis remains possible.

The canonical processing pipeline consists of file discovery, file loading, Markdown parsing, section extraction, rule evaluation, repository-context inspection, scoring, diagnostic aggregation, and report rendering. Later phases MUST NOT reimplement the work of earlier phases.

###### C.4.1.1 File Discovery Phase
The validator first determines which file is to be treated as the repository README. This phase resolves target files, configuration overrides, and repository root assumptions.

###### C.4.1.2 Parse Phase
The validator parses the README as Markdown into an abstract syntax tree. This phase MUST preserve heading structure, code fences, links, images, list items, and textual blocks.

###### C.4.1.3 Structural Analysis Phase
The validator identifies section boundaries, top-of-file blocks, heading hierarchy, and ordering relationships. This phase derives the semantic skeleton required for most rules.

###### C.4.1.4 Rule Evaluation Phase
Rules are executed against the parsed and analyzed representation. Each rule MUST produce zero or more diagnostics and MAY emit machine-readable evidence.

###### C.4.1.5 Repository Context Phase
The validator inspects the surrounding repository for related files such as `LICENSE`, `CONTRIBUTING.md`, or `CODE_OF_CONDUCT.md`. These findings are then used to evaluate context-sensitive rules.

###### C.4.1.6 Reporting Phase
The validator aggregates all findings into a normalized diagnostics model and renders them according to the requested output format. This phase also determines the final compliance level and process exit code.

---

#### C.5 Rule Engine

##### C.5.1 Rule Model
The rule engine SHALL evaluate a collection of rules defined as independent units with stable identifiers, declared severity, applicability conditions, and evaluation logic. Each rule MUST be referentially transparent with respect to the analysis context supplied to it.

A rule MUST declare at least the following properties: identifier, title, description, severity, category, compliance level, applicability predicate, and evaluation function. A rule MAY also declare autofix capability, dependencies, and machine-readable metadata for documentation and suppression.

##### C.5.2 Rule Categories
Rules SHOULD be divided into coherent categories so that both users and tooling can reason about them predictably. At minimum, the validator SHOULD define structural rules, ordering rules, content rules, formatting rules, accessibility rules, repository-context rules, and heuristic quality rules.

Structural rules determine whether required sections exist and are identifiable. Ordering rules determine whether sections appear in a cognitively appropriate sequence. Content rules inspect whether a section contains expected kinds of information. Formatting rules inspect Markdown and presentation constraints. Accessibility rules inspect images, alt text, and related concerns. Repository-context rules relate the README to the rest of the repository. Heuristic quality rules estimate vagueness, missing success conditions, or probable hidden prerequisites.

##### C.5.3 Rule Execution Semantics
Rules MUST execute against a shared immutable validation context. They MAY read from the parsed AST, section index, repository inventory, and configuration object, but MUST NOT mutate global analysis state.

Rules SHOULD be evaluable independently where possible. Where dependency exists, the engine MUST guarantee evaluation order or explicitly skip dependent rules when prerequisite analysis failed.

##### C.5.4 Hard Rules vs Heuristic Rules
Hard rules MUST correspond to machine-checkable requirements or strongly constrained repository facts. Their failure represents definite non-compliance at the selected enforcement level.

Heuristic rules MUST be labeled explicitly as heuristic. Their output SHALL be advisory unless the user opts into stricter enforcement. A heuristic rule MUST explain the basis of its finding in plain language and SHOULD provide evidence or confidence where feasible.

##### C.5.5 Rule Suppression
The validator MAY support rule suppression, but suppression MUST be explicit, local where possible, and auditable. Global suppression SHOULD be discouraged for hard rules and SHOULD require configuration-level acknowledgment.

Suppression mechanisms MAY include inline HTML comments in the README, repository-level configuration excludes, and command-line ignore flags. A suppression MUST reference rule identifiers and SHOULD allow optional justification text.

---

#### C.6 File Discovery Logic

##### C.6.1 Repository Root Resolution
The validator MUST determine a repository root before README discovery. By default, the current working directory SHALL be treated as the root unless overridden by an explicit path argument.

Where version-control metadata such as a `.git` directory is available, the validator MAY use it to confirm root boundaries. In ambiguous cases, explicit user input MUST take precedence.

##### C.6.2 README Target Resolution
By default, the validator SHALL search for `README.md` first, then `readme.md`, and then any configured alternate path. If more than one candidate exists, the validator MUST either select according to deterministic precedence or emit an ambiguity diagnostic.

The preferred default target is the repository root `README.md`. Non-root targets MAY be validated when explicitly requested, but repository compliance SHOULD always privilege the root README.

##### C.6.3 Multi-README Repositories
Some repositories contain multiple README files in subdirectories. The validator MAY support recursive validation of multiple README files, but MUST distinguish between the primary repository README and subsidiary documents.

In batch mode, the validator SHOULD report each README independently and MAY also provide an aggregate repository summary. Rules tied specifically to repository entry-point expectations MUST apply only to the primary README unless configured otherwise.

##### C.6.4 Missing README Handling
If no candidate README is found, the validator MUST emit a fatal diagnostic and exit with a non-success code. This condition SHALL be treated as a hard structural failure.

---

#### C.7 Parsing and Analysis Model

##### C.7.1 Markdown Parser Requirements
The validator MUST use a proper Markdown parser capable of producing a structured AST. Raw regular-expression parsing alone is insufficient for reliable compliance checking and MUST NOT serve as the sole analysis method.

The parser SHOULD preserve source locations for headings, paragraphs, code fences, images, and links. This is necessary for precise diagnostics and possible autofixes.

##### C.7.2 Section Detection
Sections SHALL be identified primarily by heading hierarchy and secondarily by top-of-file block positioning for the title, summary, and proof sections. The validator MUST support the fact that the title, summary, and immediate demonstration may appear before the first second-level heading.

Canonical section recognition SHOULD combine heading matching, synonym tables, and structural position. Section classification MUST remain deterministic.

##### C.7.3 Top-of-File Block Analysis
Because the specification treats the first screenful as disproportionately important, the validator SHOULD analyze the top of the document separately. It MUST determine whether title, summary, and proof are present near the top and whether low-priority material has been improperly front-loaded.

##### C.7.4 Repository File Inventory
The validator SHOULD inventory related repository artifacts, including `LICENSE`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `docs/`, and optionally `ARCHITECTURE.md`. These facts SHALL be made available to repository-context rules.

---

#### C.8 Diagnostics Model

##### C.8.1 Diagnostic Structure
Every finding emitted by the validator MUST conform to a stable diagnostic structure. At minimum, a diagnostic MUST contain rule identifier, severity, message, evidence location, and remediation guidance where applicable.

A recommended normalized diagnostic object contains the fields `id`, `severity`, `category`, `title`, `message`, `path`, `location`, `evidence`, `suggestion`, `compliance_level`, and `heuristic`. It MAY also include `autofix`, `confidence`, and `suppressed`.

##### C.8.2 Severity Levels
The validator SHALL define at least four severity levels: `error`, `warning`, `info`, and `note`. An error represents non-compliance that affects exit status under normal enforcement. A warning represents likely reduced quality or recommended non-compliance. Informational and note-level findings MAY be used for scoring explanation or enhancement opportunities.

Severity MUST be stable per rule unless changed by explicit configuration.

##### C.8.3 Source Locations
Diagnostics SHOULD include precise source locations wherever possible. A location SHOULD reference line and column ranges in the README source and MAY reference associated section identifiers.

Where a diagnostic refers to a missing element rather than an existing span, the location SHOULD point to the nearest relevant anchor, such as the document start or related section heading.

##### C.8.4 Evidence Payloads
Diagnostics MAY include machine-readable evidence supporting the finding. Evidence can include heading text, extracted commands, missing related files, unresolved anchors, or counts of image or badge nodes.

This payload SHOULD be concise and structured so that downstream tooling or IDE integrations can consume it.

---

#### C.9 Exit Codes

##### C.9.1 Exit Code Semantics
The validator MUST use stable exit codes suitable for automation. Exit semantics MUST distinguish successful validation, validation failure, configuration failure, and internal execution failure.

A recommended exit code table is as follows. Exit code `0` indicates success with no errors under the selected enforcement level. Exit code `1` indicates one or more validation errors. Exit code `2` indicates invalid configuration or command-line usage. Exit code `3` indicates parser or input errors, such as unreadable files or unsupported syntax. Exit code `4` indicates internal tool failure.

##### C.9.2 Warning Treatment
Warnings MUST NOT fail the process by default. The validator MAY support modes such as `--strict-warnings` or configuration options that escalate warnings to errors.

##### C.9.3 Threshold-Based Failure
If scoring is enabled, the validator MAY support failure on score thresholds in addition to rule-based failure. Such thresholds MUST be explicit and SHOULD never silently replace hard-rule enforcement.

---

#### C.10 Configuration Format

##### C.10.1 Configuration Principles
Configuration MUST be explicit, portable, and human-readable. YAML is the preferred primary configuration format, though JSON MAY be supported as an alternative representation.

Configuration MUST only relax or specialize behavior in well-defined ways. It MUST NOT silently redefine the meaning of normative rules without a clear declaration of custom policy.

##### C.10.2 Configuration File Discovery
By default, the validator SHOULD search for one of the following files in the repository root: `.readmerc.yml`, `.readmerc.yaml`, `readme-validator.yml`, or a dedicated field inside `package.json` if supported. If multiple files are present, the precedence order MUST be deterministic and documented.

##### C.10.3 Configuration Scope
Configuration MAY define compliance target, enabled rules, disabled rules, severity overrides, section alias mappings, path overrides, badge limits, link-check behavior, and suppression policy. It SHOULD also allow organization-wide presets.

##### C.10.4 Example Configuration
A canonical minimal configuration:

```yaml
extends:
  - rrs:recommended

readme:
  path: README.md

rules:
  missing_project_status:
    severity: warning
  too_many_badges:
    max_count: 5
  link_integrity:
    check_external: false

sections:
  aliases:
    quickstart:
      - Getting Started
    documentation:
      - Docs

reporting:
  format: text
  fail_on_warnings: false
  score_threshold: null
```

##### C.10.5 Presets
The validator SHOULD ship with preset policies such as `minimal`, `recommended`, `strict`, `library`, `cli`, and `research`. Presets MUST expand to explicit rule configurations and SHOULD be inspectable by users.

---

#### C.11 Reporting, Warnings, and Logs

##### C.11.1 Human-Readable Reports
The default report format SHOULD be concise and readable in a terminal. It SHOULD summarize compliance level, total errors, total warnings, score if available, and a grouped list of diagnostics with source locations.

Human-readable output MUST prioritize actionable guidance. It SHOULD tell the user what failed, where it failed, why it matters, and how to fix it.

##### C.11.2 Machine-Readable Reports
The validator MUST support structured output in JSON and SHOULD support YAML. These reports SHOULD include full diagnostic payloads, compliance summary, and score details for downstream automation.

##### C.11.3 Logging Levels
The validator SHOULD implement distinct logging levels such as `quiet`, `normal`, `verbose`, and `debug`. Quiet mode SHOULD suppress non-essential output. Debug mode MAY include parser traces, rule timing, and raw section classification data.

##### C.11.4 Warning Classes
Warnings SHOULD be classed by meaning, not merely by severity. For example, there SHOULD be separate classes for content vagueness, visual overload, likely missing success criteria, broken external links, and missing recommended sections.

This makes reports easier to interpret and supports selective escalation in configuration.

##### C.11.5 Suggested Fixes
Where feasible, warnings and errors SHOULD include suggested fixes. Suggestions MUST be concrete and local. For example, a missing license link diagnostic SHOULD recommend linking `./LICENSE` if that file exists.

---

#### C.12 Scoring Model

##### C.12.1 Purpose of Scoring
Scoring is optional and supplementary. Its purpose is to summarize README quality for dashboards, trend tracking, or repository health views. It MUST NOT obscure hard failures or replace rule-based interpretation.

##### C.12.2 Weighted Scoring
If scoring is enabled, the validator SHOULD compute a weighted aggregate over rule categories or validation domains. Required structural correctness SHOULD carry higher weight than optional visual polish.

##### C.12.3 Score Interpretation
A score MUST be accompanied by an explanation or breakdown. The validator SHOULD expose sub-scores such as structure, onboarding, formatting, accessibility, repository integration, and **content** (including language and readability rules).

##### C.12.4 Positive adjustments for language and readability
When the README is classified as **English-primary** and **all** configured quantitative readability checks pass, a reference validator **MAY** apply a **small positive scoring adjustment** (for example **+1** point on a 0–100 scale), analogous to existing bonuses for restrained badges (§5.6) and consistent feature emoji (§5.7). This adjustment **MUST NOT** mask hard structural failures.

---

#### C.13 Package Layout

##### C.13.1 Monorepo vs Single Package
The validator MAY be shipped as a single npm package or as a small monorepo with separate packages for core rule logic, CLI wrapper, and shared schemas. A modular layout is preferable if the validator is expected to support editor integrations or third-party rule packs.

##### C.13.2 Recommended Package Structure
A recommended package structure is as follows. The `core` layer contains parsers, models, and rule execution. The `cli` layer contains argument parsing and report rendering. The `schemas` layer contains YAML and JSON schema artifacts. The `presets` layer contains configuration presets. The `fixtures` and `tests` layers contain compliance examples and regression tests.

A representative layout:

```text
packages/
  core/
    src/
      ast/
      analysis/
      rules/
      diagnostics/
      scoring/
      config/
    test/
  cli/
    src/
      commands/
      reporters/
      logging/
    test/
  schemas/
    rrs-readme-schema.yml
  presets/
    minimal.yml
    recommended.yml
    strict.yml
    library.yml
    cli.yml
    research.yml
fixtures/
  compliant/
  noncompliant/
docs/
```

##### C.13.3 Public API Surface
The package SHOULD expose both a programmatic API and a CLI. The programmatic API SHOULD allow validation of a path or in-memory README content and return a structured report object.

---

#### C.14 CLI Design

##### C.14.1 Command Model
The CLI SHOULD expose a simple primary command such as `readme-validator check`. It MAY also expose subcommands such as `init`, `explain`, `list-rules`, `print-config`, and `score`.

##### C.14.2 Core Commands
The `check` command validates a target README or repository. The `init` command scaffolds configuration. The `list-rules` command prints rule metadata. The `explain` command explains a rule by identifier. The `score` command emits quality scores. The `print-config` command resolves effective configuration after preset expansion.

##### C.14.3 Example Usage

```bash
readme-validator check
readme-validator check README.md --format json
readme-validator check . --preset strict
readme-validator list-rules
readme-validator explain missing_quickstart
readme-validator init
```

##### C.14.4 Standard Flags
The CLI SHOULD support flags for target path, output format, preset, config path, quiet mode, debug mode, fail-on-warnings, no-external-link-check, and max-badge-count overrides. Flags MUST override configuration file values in a documented precedence order.

---

#### C.15 Rule Packs and Extensibility

##### C.15.1 Built-In Rules
The validator MUST ship with a built-in ruleset implementing the present specification. Built-in rules MUST be versioned with the tool and documented.

##### C.15.2 Third-Party Rule Packs
The validator MAY support external rule packs. Rule-pack APIs MUST be stable, namespaced, and constrained so that third-party extensions cannot silently shadow built-in rule identifiers.

##### C.15.3 Organization Presets
Organizations MAY define custom policy presets on top of the base specification. Such presets SHOULD remain clearly marked as organizational extensions rather than core RRS compliance.

---

#### C.16 Link Checking Strategy

##### C.16.1 Internal Link Checking
Internal links and heading anchors SHOULD always be checked by default. Failures in internal links are high-confidence defects and SHOULD usually be treated as errors.

##### C.16.2 External Link Checking
External link checking SHOULD be supported but MAY be disabled by default for performance or network reliability reasons. External link failures SHOULD usually be warnings unless the user explicitly enables strict external validation.

##### C.16.3 Caching and Retry Policy
If external links are checked, the validator SHOULD support request caching, retry limits, timeout controls, and ignore patterns. It MUST not hang indefinitely on unreachable resources.

---

#### C.17 Performance and Reliability

##### C.17.1 Performance Constraints
The validator SHOULD complete quickly on typical repositories and MUST not require network access unless explicitly requested for external link validation. Parsing and rule evaluation SHOULD scale linearly with document size in ordinary cases.

##### C.17.2 Reliability Constraints
The validator MUST behave predictably on malformed but parseable Markdown and SHOULD emit partial results where possible rather than aborting prematurely. Internal exceptions MUST be surfaced clearly and SHOULD not be mistaken for validation failures.

---

#### C.18 Testing Strategy

##### C.18.1 Fixture-Based Testing
The validator SHOULD include a fixture corpus of compliant and non-compliant READMEs. Each fixture SHOULD encode expected diagnostics and, where relevant, expected compliance levels and scores.

##### C.18.2 Snapshot Testing
Report rendering MAY be tested with snapshots, provided those snapshots are stable and intentionally maintained.

##### C.18.3 Rule Regression Testing
Each rule SHOULD have dedicated regression tests covering positive, negative, and edge-case behavior. Heuristic rules SHOULD include confidence or false-positive tolerance tests where possible.

---

#### C.19 Recommended Initial Rule Set

##### C.19.1 Core Errors
An initial MVP validator SHOULD implement hard errors for missing README, missing title, missing summary, missing proof, missing installation, missing quickstart, missing usage, missing documentation reference, missing support path, missing license section, broken internal anchors, and badge-wall-before-identity.

##### C.19.2 Core Warnings
An initial MVP SHOULD implement warnings for vague summary, missing project status, too many badges, oversized code examples, likely hidden prerequisites, architecture before usage, missing expected output, decorative-only images, **non-English primary prose** (statistical language ID), and **readability threshold breaches** (Flesch Reading Ease, Flesch–Kincaid, Gunning Fog, SMOG when sample size suffices, Dale–Chall), using libraries such as **`franc`** and **`text-readability`**.

##### C.19.3 Deferred Rules
Fine-grained per-section language parity (proving that a Chinese paragraph adds no facts beyond the English text) and semantic duplication detection across languages MAY be deferred to later versions or human review. The validator SHOULD start with high-confidence, high-value checks.

---

#### C.20 Minimal Programmatic API Sketch

A minimal TypeScript-facing API:

```typescript
export interface ValidateOptions {
  rootDir?: string;
  readmePath?: string;
  preset?: string;
  configPath?: string;
  failOnWarnings?: boolean;
  checkExternalLinks?: boolean;
  format?: "text" | "json" | "yaml";
}

export interface Diagnostic {
  id: string;
  severity: "error" | "warning" | "info" | "note";
  category: string;
  title: string;
  message: string;
  path: string;
  location?: {
    line: number;
    column: number;
    endLine?: number;
    endColumn?: number;
  };
  suggestion?: string;
  heuristic?: boolean;
}

export interface TokenEstimation {
  utf8ByteLength: number;
  utf16CodeUnitCount: number;
  estimatedTokens: number;
  estimationMethod: "utf8_byte_length_div_4_ceiling";
  nominalContextWindowTokens: number;
  estimatedContextSharePercent: number;
}

export interface ValidationReport {
  complianceLevel: "none" | "minimal" | "recommended" | "strict";
  score?: number;
  diagnostics: Diagnostic[];
  errors: number;
  warnings: number;
  tokenEstimation: TokenEstimation;
  metadata: {
    readmePath: string;
    preset: string;
    checkedExternalLinks: boolean;
  };
}

export declare function validateReadme(
  options?: ValidateOptions
): Promise<ValidationReport>;
```

This API is intentionally small. It gives the CLI and external tooling a stable core contract without overcommitting to internal architecture. Implementations MAY attach the informative `tokenEstimation` object described in [C.23 Token Estimation and Document Size Informatics (Informative)](#c23-token-estimation-and-document-size-informatics-informative); that object MUST NOT alter compliance classification or scoring semantics.

---

#### C.21 Implementation Sequence
A practical build sequence SHOULD begin with AST parsing, required-section detection, and deterministic structural rules. The second phase SHOULD add ordering checks, repository-context checks, and reporting. The third phase SHOULD add heuristic warnings, scoring, configuration presets, and CI-grade exit semantics. Only after that should external link checking, editor integration, or third-party rule packs be added.

This sequence minimizes complexity while delivering immediate value. It also aligns with the principle that the validator should begin with high-confidence rules before it attempts more interpretive judgments.

---

#### C.22 TypeScript Package Blueprint

##### C.22.1 Purpose
This section defines a concrete implementation blueprint for the README validator as a TypeScript-based npm package and CLI. It translates the abstract validator design into a practical package structure, module layout, command surface, and implementation sequence suitable for an initial public release.

The blueprint assumes a TypeScript-first implementation, Node.js runtime, and npm distribution. It is designed so that the validator can begin as a single package if necessary, while remaining structurally ready for later extraction into a small monorepo.

##### C.22.2 Package Naming Strategy
The canonical package names proposed are `@rhythmus/readme-validator` for the single-package CLI version, or `@repose/core` (etc.) for a future multi-package architecture. Currently, the canonical name is `@rhythmus/readme-validator`.

The CLI binary name SHOULD be short and memorable. The preferred executable name is `readme-validator`.

##### C.22.3 Release Strategy
The project SHOULD begin with a single published package containing both the core engine and CLI, because this minimizes release overhead and reduces coordination cost during early development. Internal module boundaries SHOULD nevertheless be designed as if later package extraction were expected.

A second release phase MAY split the codebase into separate packages once the public API, rule model, and configuration format have stabilized.

##### C.22.4 Recommended Repository Layout

```text
@rhythmus/readme-validator/
  README.md
  LICENSE
  CONTRIBUTING.md
  package.json
  tsconfig.json
  tsconfig.build.json
  .gitignore
  .npmignore
  src/
    index.ts
    cli.ts
    constants/
      exit-codes.ts
      defaults.ts
    config/
      config-loader.ts
      config-resolver.ts
      config-schema.ts
      presets.ts
    filesystem/
      find-repo-root.ts
      find-readme.ts
      inventory-files.ts
    markdown/
      parse-markdown.ts
      ast-types.ts
      extract-headings.ts
      extract-links.ts
      extract-images.ts
      extract-code-blocks.ts
    analysis/
      build-document-model.ts
      classify-sections.ts
      classify-top-blocks.ts
      compute-ordering.ts
      collect-context.ts
    rules/
      registry.ts
      types.ts
      structural/
      ordering/
      content/
      formatting/
      accessibility/
      repository/
      heuristics/
    diagnostics/
      diagnostic.ts
      normalize-diagnostics.ts
      suppressions.ts
    reporting/
      format-text.ts
      format-json.ts
      format-yaml.ts
      summary.ts
    scoring/
      compute-score.ts
      weights.ts
    commands/
      check.ts
      init.ts
      list-rules.ts
      explain.ts
      print-config.ts
    utils/
      strings.ts
      paths.ts
      arrays.ts
      markdown-text.ts
      logger.ts
  schemas/
    rrs-readme-schema.yml
    readme-config.schema.yml
  presets/
    minimal.yml
    recommended.yml
    strict.yml
    library.yml
    cli.yml
    research.yml
  fixtures/
    compliant/
    noncompliant/
    edge-cases/
  test/
    unit/
    integration/
    snapshots/
  scripts/
    build.ts
    generate-fixture-index.ts
  docs/
    architecture.md
    rules.md
    config.md
```

##### C.22.5 `package.json` Blueprint

```json
{
  "name": "@rhythmus/readme-validator",
  "version": "0.1.0",
  "description": "CLI and TypeScript validator for repository README compliance",
  "license": "MIT",
  "type": "module",
  "bin": {
    "readme-validator": "./dist/cli.js"
  },
  "main": "./dist/index.js",
  "types": "./dist/index.d.ts",
  "exports": {
    ".": {
      "types": "./dist/index.d.ts",
      "import": "./dist/index.js"
    },
    "./schemas/rrs-readme-schema.yml": "./schemas/rrs-readme-schema.yml",
    "./presets/*": "./presets/*"
  },
  "files": [
    "dist",
    "schemas",
    "presets",
    "README.md",
    "LICENSE"
  ],
  "engines": {
    "node": ">=18"
  },
  "scripts": {
    "build": "tsc -p tsconfig.build.json",
    "clean": "rimraf dist",
    "dev": "tsx src/cli.ts",
    "lint": "eslint .",
    "test": "vitest run",
    "test:watch": "vitest",
    "typecheck": "tsc -p tsconfig.json --noEmit",
    "prepublishOnly": "npm run clean && npm run build && npm run test"
  },
  "dependencies": {
    "commander": "^12.0.0",
    "js-yaml": "^4.1.0",
    "unist-util-visit": "^5.0.0",
    "mdast-util-from-markdown": "^2.0.0",
    "mdast-util-gfm": "^3.0.0",
    "micromatch": "^4.0.0",
    "franc": "^6.0.0",
    "text-readability": "^1.1.0"
  },
  "devDependencies": {
    "@types/js-yaml": "^4.0.0",
    "@types/node": "^22.0.0",
    "eslint": "^9.0.0",
    "rimraf": "^6.0.0",
    "tsx": "^4.0.0",
    "typescript": "^5.6.0",
    "vitest": "^2.0.0"
  }
}
```

##### C.22.6 TypeScript Configuration

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    "declaration": true,
    "declarationMap": true,
    "sourceMap": true,
    "rootDir": "src",
    "outDir": "dist",
    "esModuleInterop": true,
    "skipLibCheck": true
  },
  "include": ["src", "test"]
}
```

A separate `tsconfig.build.json` SHOULD narrow compilation to `src/` only, excluding tests and fixtures.

##### C.22.7 Internal Module Boundaries
The internal module graph SHOULD follow the validation pipeline. Filesystem discovery MUST precede parsing, parsing MUST precede section analysis, section analysis MUST precede rule evaluation, and diagnostics formatting MUST remain downstream of rule execution.

The `config` layer resolves user and preset configuration. The `filesystem` layer discovers relevant paths. The `markdown` layer parses Markdown and exposes low-level extractors. The `analysis` layer derives semantic structure from the AST. The `rules` layer evaluates compliance. The `diagnostics` layer normalizes findings. The `reporting` layer renders them. The `commands` layer composes all lower layers for CLI use. This separation SHOULD remain strict.

##### C.22.8 Programmatic API Blueprint

```typescript
export type {
  ValidateOptions,
  ValidationReport,
  Diagnostic,
  Severity,
  ComplianceLevel
} from "./rules/types.js";

export { validateReadme } from "./commands/check.js";
export { loadConfig } from "./config/config-loader.js";
export { builtInRules } from "./rules/registry.js";
```

The public API SHOULD avoid exposing internal AST utilities or parser details until those interfaces are clearly stable.

##### C.22.9 CLI Entry Blueprint

```typescript
#!/usr/bin/env node
import { Command } from "commander";
import { runCheckCommand } from "./commands/check.js";
import { runInitCommand } from "./commands/init.js";
import { runListRulesCommand } from "./commands/list-rules.js";
import { runExplainCommand } from "./commands/explain.js";
import { runPrintConfigCommand } from "./commands/print-config.js";

const program = new Command();

program
  .name("readme-validator")
  .description("Validate repository README files against the RRS specification")
  .version("0.1.0");

program
  .command("check [target]")
  .description("Validate a repository or README file")
  .option("--config <path>", "Path to config file")
  .option("--preset <name>", "Validation preset")
  .option("--format <format>", "Output format: text|json|yaml", "text")
  .option("--fail-on-warnings", "Treat warnings as errors", false)
  .option("--no-external-links", "Disable external link checking")
  .action(runCheckCommand);

program
  .command("init")
  .description("Create a starter configuration file")
  .action(runInitCommand);

program
  .command("list-rules")
  .description("List built-in validation rules")
  .action(runListRulesCommand);

program
  .command("explain <ruleId>")
  .description("Explain a validation rule")
  .action(runExplainCommand);

program
  .command("print-config")
  .description("Print resolved configuration")
  .action(runPrintConfigCommand);

program.parseAsync();
```

##### C.22.10 Core Type Model

```typescript
export type Severity = "error" | "warning" | "info" | "note";
export type ComplianceLevel = "none" | "minimal" | "recommended" | "strict";

export interface ValidateOptions {
  rootDir?: string;
  readmePath?: string;
  configPath?: string;
  preset?: string;
  format?: "text" | "json" | "yaml";
  failOnWarnings?: boolean;
  checkExternalLinks?: boolean;
  quiet?: boolean;
  debug?: boolean;
}

export interface DiagnosticLocation {
  line: number;
  column: number;
  endLine?: number;
  endColumn?: number;
}

export interface Diagnostic {
  id: string;
  severity: Severity;
  category: string;
  title: string;
  message: string;
  path: string;
  location?: DiagnosticLocation;
  evidence?: Record<string, unknown>;
  suggestion?: string;
  heuristic?: boolean;
  suppressed?: boolean;
}

export interface TokenEstimation {
  utf8ByteLength: number;
  utf16CodeUnitCount: number;
  estimatedTokens: number;
  estimationMethod: "utf8_byte_length_div_4_ceiling";
  nominalContextWindowTokens: number;
  estimatedContextSharePercent: number;
}

export interface ValidationReport {
  complianceLevel: ComplianceLevel;
  score?: number;
  diagnostics: Diagnostic[];
  errors: number;
  warnings: number;
  tokenEstimation: TokenEstimation;
  metadata: {
    rootDir: string;
    readmePath: string;
    preset: string;
    checkedExternalLinks: boolean;
  };
}

export interface RuleContext {
  rootDir: string;
  readmePath: string;
  source: string;
  ast: unknown;
  documentModel: unknown;
  repositoryFiles: string[];
  config: ResolvedConfig;
}

export interface Rule {
  id: string;
  title: string;
  description: string;
  category: string;
  severity: Severity;
  heuristic?: boolean;
  applies(context: RuleContext): boolean;
  evaluate(context: RuleContext): Promise<Diagnostic[]>;
}
```

##### C.22.11 Document Model Blueprint

```typescript
export interface SectionBlock {
  id: string;
  headingText?: string;
  headingLevel?: number;
  startLine?: number;
  endLine?: number;
  contentText: string;
  nodeCount: number;
}

export interface TopOfFileModel {
  title?: SectionBlock;
  summary?: SectionBlock;
  proofBlocks: SectionBlock[];
}

export interface DocumentModel {
  title?: string;
  headings: Array<{
    text: string;
    level: number;
    line?: number;
  }>;
  sections: SectionBlock[];
  topOfFile: TopOfFileModel;
  codeBlocks: Array<{
    language?: string;
    value: string;
    line?: number;
  }>;
  links: Array<{
    url: string;
    text?: string;
    internal: boolean;
    line?: number;
  }>;
  images: Array<{
    url: string;
    alt?: string;
    line?: number;
  }>;
  badges: Array<{
    url: string;
    alt?: string;
    line?: number;
  }>;
}
```

##### C.22.12 Rule Registry Blueprint

```typescript
import { ruleMissingTitle } from "./structural/missing-title.js";
import { ruleMissingSummary } from "./structural/missing-summary.js";
import { ruleMissingProof } from "./structural/missing-proof.js";
import { ruleMissingInstallation } from "./structural/missing-installation.js";
import { ruleMissingQuickstart } from "./structural/missing-quickstart.js";
import { ruleMissingUsage } from "./structural/missing-usage.js";
import { ruleMissingDocumentation } from "./structural/missing-documentation.js";
import { ruleMissingSupport } from "./structural/missing-support.js";
import { ruleMissingLicense } from "./structural/missing-license.js";
import { ruleBadgeWallBeforeIdentity } from "./ordering/badge-wall-before-identity.js";
import { ruleArchitectureBeforeUsage } from "./ordering/architecture-before-usage.js";
import { ruleMissingAltText } from "./accessibility/missing-alt-text.js";
import { ruleTooManyBadges } from "./formatting/too-many-badges.js";
import { ruleTooManyBadgesBetweenTitleAndSummary } from "./formatting/too-many-badges-between-title-and-summary.js";
import { ruleMissingProjectStatus } from "./heuristics/missing-project-status.js";
import {
  ruleReadmePrimaryLanguageNotEnglish,
  ruleReadabilityFleschReadingEase,
  ruleReadabilityFleschKincaidGrade,
  ruleReadabilityGunningFog,
  ruleReadabilitySmogIndex,
  ruleReadabilityDaleChall,
} from "./content/readme-language-readability.js";
import type { Rule } from "./types.js";

export const builtInRules: Rule[] = [
  ruleMissingTitle,
  ruleMissingSummary,
  ruleMissingProof,
  ruleMissingInstallation,
  ruleMissingQuickstart,
  ruleMissingUsage,
  ruleMissingDocumentation,
  ruleMissingSupport,
  ruleMissingLicense,
  ruleBadgeWallBeforeIdentity,
  ruleArchitectureBeforeUsage,
  ruleMissingAltText,
  ruleTooManyBadges,
  ruleTooManyBadgesBetweenTitleAndSummary,
  ruleMissingProjectStatus,
  ruleReadmePrimaryLanguageNotEnglish,
  ruleReadabilityFleschReadingEase,
  ruleReadabilityFleschKincaidGrade,
  ruleReadabilityGunningFog,
  ruleReadabilitySmogIndex,
  ruleReadabilityDaleChall,
  ruleHeadingNoSkip,
  ruleAlertSyntax,
  ruleKbdUsage,
  ruleBoldLimit,
  ruleCodeNoPrompts,
  rulePlaceholderCaps,
  ruleAltTextStandard,
  ruleInclusiveLanguage,
  ruleManifestSync,
  ruleSummaryCharLimit,
  ruleSpdxLicense,
  ruleTocMandatoryThreshold,
  ruleI18nNaming
];
```

##### C.22.13 Preset Blueprint

```yaml
name: recommended

rules:
  missing_title: error
  missing_summary: error
  missing_proof: error
  missing_installation: error
  missing_quickstart: error
  missing_usage: error
  missing_documentation: error
  missing_support: error
  missing_license: error
  badge_wall_before_identity: error
  architecture_before_usage: warning
  too_many_badges: warning
  too_many_badges_between_title_and_summary: warning
  too_many_emoji: warning
  features_emoji_inconsistent: warning
  recommend_emoji_in_features: info
  missing_alt_text: warning
  missing_project_status: warning
  heading_no_skip: error
  alert_syntax: warning
  kbd_usage: info
  bold_limit: warning
  code_no_prompts: error
  placeholder_caps: error
  alt_text_standard: warning
  inclusive_language: warning
  manifest_sync: error
  summary_char_limit: warning
  spdx_license: error
  toc_mandatory_threshold: error
  i18n_naming: info

limits:
  max_badges: 14
  max_badges_before_summary: 5
  max_emoji: 16
  max_code_block_lines: 30

readability:
  minProseWords: 100
  minFleschReadingEase: -5
  maxFleschKincaidGrade: 22
  maxGunningFog: 19
  maxSmog: 20
  maxDaleChall: 13.0
  minSentencesForSmog: 10
  minProseWordsForLanguage: 80

reporting:
  score: true
```

Project-type presets such as `library`, `cli`, and `research` SHOULD extend the same base rather than redefining the whole rule space independently.

##### C.22.14 Command Implementation Blueprint

```typescript
import { resolveConfig } from "../config/config-resolver.js";
import { findReadme } from "../filesystem/find-readme.js";
import { parseMarkdown } from "../markdown/parse-markdown.js";
import { buildDocumentModel } from "../analysis/build-document-model.js";
import { inventoryFiles } from "../filesystem/inventory-files.js";
import { builtInRules } from "../rules/registry.js";
import { computeScore } from "../scoring/compute-score.js";
import { formatReport } from "../reporting/summary.js";

export async function runCheckCommand(
  target: string | undefined,
  options: Record<string, unknown>
): Promise<void> {
  const config = await resolveConfig(target, options);
  const readmePath = await findReadme(config);
  const source = await fs.readFile(readmePath, "utf-8");
  const ast = parseMarkdown(source);
  const documentModel = buildDocumentModel(ast, source);
  const repositoryFiles = await inventoryFiles(config.rootDir);

  const context = {
    rootDir: config.rootDir,
    readmePath,
    source,
    ast,
    documentModel,
    repositoryFiles,
    config
  };

  const diagnostics = [];
  for (const rule of builtInRules) {
    if (!rule.applies(context)) continue;
    diagnostics.push(...(await rule.evaluate(context)));
  }

  const report = computeScore({
    diagnostics,
    context,
    config
  });

  console.log(formatReport(report, config.reporting.format));
  process.exitCode = report.errors > 0
    || (config.reporting.failOnWarnings && report.warnings > 0) ? 1 : 0;
}
```

##### C.22.15 Reporter Blueprint

```typescript
export function formatText(report: ValidationReport): string;
export function formatJson(report: ValidationReport): string;
export function formatYaml(report: ValidationReport): string;
```

The text reporter SHOULD group diagnostics by severity and category, show source locations where available, and include a one-line compliance summary at the top.

A typical text output SHOULD resemble:

```text
README validation failed

Compliance level: minimal
Score: 71
Errors: 2
Warnings: 3

ERROR  missing_quickstart  README.md:24:1
Quickstart section is missing.
Add a section titled "Quickstart" or "Getting Started" with a minimal executable flow.

ERROR  missing_license  README.md:1:1
License section is missing.
Add a "License" section near the end and link the LICENSE file.

WARNING  too_many_badges  README.md:3:1
8 badges detected near the top of the document.
Reduce badge count to 6 or fewer.
```

##### C.22.16 Fixtures and Test Corpus Blueprint

The project SHOULD include a curated fixture corpus from the start:

```text
fixtures/
  compliant/
    minimal-readme/
      README.md
      expected.json
    recommended-readme/
      README.md
      expected.json
  noncompliant/
    missing-quickstart/
      README.md
      expected.json
    badge-wall-before-title/
      README.md
      expected.json
    broken-internal-links/
      README.md
      expected.json
  edge-cases/
    alternate-section-headings/
    multiple-readmes/
    readme-without-h2s/
```

Each fixture SHOULD include the README source and the expected normalized report or diagnostic subset. This makes rule behavior auditable and regression-safe.

##### C.22.17 MVP Implementation Order
The MVP SHOULD be implemented in a controlled sequence. First, implement repository root resolution, README discovery, Markdown parsing, heading extraction, and title-summary-proof detection. Second, implement required-section rules and a plain text reporter. Third, add ordering rules, internal link checks, and repository-context checks. Fourth, add YAML config, presets, JSON/YAML report rendering, and score calculation. Fifth, add heuristics, suppression, and richer diagnostics.

##### C.22.18 Suggested Initial Version Plan
Version `0.1.0` SHOULD ship with the CLI, programmatic API, recommended preset, required-section rules, ordering checks, text and JSON output, and internal link validation. Version `0.2.0` MAY add YAML reporting, external link validation, project-type presets, and score breakdowns. Version `0.3.0` MAY add suppression support, autofix suggestions, richer heuristics, and rule explanation metadata.

A `1.0.0` release SHOULD wait until the configuration format, rule identifiers, exit-code semantics, and core programmatic API have stabilized.

##### C.22.19 Dogfooding
The validator project's own README SHOULD conform strictly to the specification it enforces. This serves as a dogfooding artifact, integration test, and public reference implementation. The repository SHOULD therefore include a high-quality `README.md`, a `docs/architecture.md`, and a visible `CONTRIBUTING.md`, and its CI SHOULD validate its own README during every pull request.

---

#### C.23 Token Estimation and Document Size Informatics (Informative)

This subsection is **non-normative** and **informative only**. It belongs in Appendix C (validator annex) alongside machine validation and reporting design. It MUST NOT be read back into Chapters 1–12 or Section 9 as an additional compliance requirement, size cap, or scoring ingredient. The normative README model remains structure, ordering, content expectations, accessibility, and the explicitly defined scoring model in §C.12 and related sections—**without** token-derived length as a quality signal.

##### C.23.1 Placement and scope

**Why this is appendix-only.** “Tokens” and “context window utilization” are artifacts of **external** language-model runtimes (provider tokenizers, chat templates, tool schemas, and billing meters). The RRS defines what a good README is for **human readers** and for **deterministic tooling** (headings, sections, links, readability metrics where specified). Conflating those goals with LLM token economics would (a) bake unstable vendor behavior into a document standard, (b) encourage gaming length instead of clarity, and (c) mislead authors who assume a byte heuristic equals invoice line items. Therefore:

- Token estimation and any **heuristic “information density” or quality judgment derived primarily from length or token proxies** are **out of scope** for the **core** specification and for **compliance level**, **exit codes**, and the **primary quality score** as defined elsewhere in this appendix.
- The same material **MAY** appear only as **optional reporting fields** and **human-oriented explanations** in validator output (text, JSON, YAML, playgrounds), exactly as described below.

##### C.23.2 Author and integrator need (without normative overreach)

Authors and CI integrators increasingly paste README-sized documents into coding agents or summarization pipelines. They reasonably ask: “Roughly how much of a 128k (or 200k, or 1M) context budget does this file represent?” That question is **practical** but **not answerable** from the README file alone in a provider-accurate way:

- **Tokenizer variance.** Subword tokenization (BPE, WordPiece, SentencePiece, and proprietary merges) splits the same UTF-8 stream differently across models and even across model revisions.
- **Template overhead.** Chat formatting, system prompts, tool definitions, and attachments are added by the host application; they are invisible to a README-only validator.
- **Semantic vs. syntactic size.** Two READMEs with identical byte length can differ wildly in usefulness; length is at best a weak correlate of “too much boilerplate” or “missing sections,” which the RRS already addresses with explicit rules—not with a token count.

The specification therefore does **not** mandate token limits or “density scores.” It **MAY** recommend that validators expose **transparent, labeled heuristics** so consumers understand they are approximations.

##### C.23.3 Reference heuristic (tokenizer-agnostic)

A common **portable** proxy, used when no provider tokenizer is available, is:

`estimatedTokens = ceil(utf8ByteLength / 4)`

where `utf8ByteLength` is the number of bytes when the **validated README source** is encoded as UTF-8 (the same string the validator parses for rules).

**Interpretation.** The divisor four is a long-standing **rule-of-thumb** for English-heavy Latin prose (order-of-magnitude bytes per subword token). It is **not** a standard endorsed by any particular model vendor. It systematically **over-** or **under-estimates** for:

- Dense code blocks, tables, and URLs (often many short tokens per byte in real tokenizers).
- CJK, Arabic, emoji, and mixed scripts (byte length and token count diverge from Latin-centric averages).
- Repeated boilerplate vs. unique technical content (same bytes, different information value).

Implementations SHOULD therefore:

- Set `estimationMethod` to an explicit literal (e.g. `utf8_byte_length_div_4_ceiling`) so downstream tools never confuse this with provider-native counts.
- Emit **raw** `utf8ByteLength` and **ECMAScript** `utf16CodeUnitCount` (i.e. `String.length`, which counts UTF-16 code units so astral-plane characters count as two units) so integrators can apply alternate formulas or attach their own tokenizer.

##### C.23.4 Nominal context share (dashboards only)

For **human-oriented** dashboards only, a validator MAY compute:

`estimatedContextSharePercent` from `estimatedTokens` and a fixed **nominal** `nominalContextWindowTokens` (e.g. 128 000), using a clearly documented rounding rule (e.g. two decimal places). That constant is **not** a maximum README size under the RRS, **not** a compliance threshold, and **not** implied alignment with any specific product’s context window. It is solely a **reference denominator** so a percentage is meaningful on a ruler authors already think in.

Percentages **MAY** exceed 100 when the heuristic estimate exceeds the nominal window.

##### C.23.5 Prohibited uses and anti-patterns

The following are **incompatible** with the intent of this appendix:

- **Billing or quota claims.** Output MUST NOT imply that `estimatedTokens` matches invoiced tokens or API metering.
- **Normative caps.** The RRS MUST NOT use token estimates to define MUST/SHOULD maximum document sizes (separate informative “rendered size” guidance may exist elsewhere; it is not token-derived).
- **Scoring and conformance coupling.** Token estimates MUST NOT be inputs to compliance level, weighted quality score, or exit-code determination. **Heuristic quality assessments that are predominantly length- or token-driven** (e.g. “information density” = tokens divided by section count without semantic analysis) MUST NOT substitute for or modify those outcomes—they bias toward short shallow READMEs and penalize legitimately deep technical documentation.
- **Silent relabeling.** UIs MUST distinguish “estimated tokens (heuristic)” from any future provider-supplied counts if both are shown.

##### C.23.6 Report shape

When present, the payload SHOULD match the `TokenEstimation` interface in §C.20 and §C.22.10: at minimum `utf8ByteLength`, `utf16CodeUnitCount`, `estimatedTokens`, `estimationMethod`, and, if a share is shown, `nominalContextWindowTokens` plus `estimatedContextSharePercent`.

---

### D. Glossary

#### D.1 Terms and Definitions

The glossary defines key terms used throughout the specification. Definitions are consistent with Section 0.3.

- **README**: A top-level documentation file within a repository that provides an overview of the project, instructions for use, and contextual information necessary for evaluation and adoption.
- **Repository**: A version-controlled collection of files representing a software project, typically hosted on platforms such as GitHub, GitLab, or Bitbucket.
- **User**: An individual who consumes or integrates the project.
- **Contributor**: An individual who modifies or extends the project's code or documentation.
- **First Success**: The earliest point at which a user achieves a meaningful outcome using the project.
- **Cognitive Funnel**: The ordered progression from awareness to adoption that a README SHOULD guide readers through.
- **Reproducibility**: The ability to recreate the described behavior or output using the instructions provided.
- **Trust Signal**: Any element that communicates reliability, maintenance status, or credibility.
- **Compliance Level**: A classification of how thoroughly a README adheres to this specification (minimal, recommended, or strict).
- **Normative**: A requirement or recommendation that is binding under this specification.
- **Heuristic Rule**: A validation rule that estimates quality or compliance based on probabilistic reasoning rather than strict deterministic checking.
- **GFM**: GitHub Flavored Markdown, the reference rendering context for this specification.

#### D.2 Cross-References

Terms SHOULD include references to related concepts within the specification. The cognitive funnel is defined in §2.2, user personas in §2.3, compliance levels in §9.1, and normative language conventions in §0.3.1.

---

### E. Bibliography

#### E.1 Citation Format

All references are expressed in BibTeX-compatible format. Entries include author, title, year, and URL where applicable.

#### E.2 Primary Sources

```bibtex
@misc{github_readme_docs,
  author       = {{GitHub}},
  title        = {About READMEs},
  year         = {2024},
  url          = {https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes},
  note         = {Official GitHub documentation on README purpose and structure}
}

@misc{github_markdown_syntax,
  author       = {{GitHub}},
  title        = {Basic Writing and Formatting Syntax},
  year         = {2024},
  url          = {https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax},
  note         = {Defines GitHub Flavored Markdown capabilities and constraints}
}

@misc{github_docs_style_guide,
  author       = {{GitHub}},
  title        = {GitHub Docs Style Guide},
  year         = {2024},
  url          = {https://docs.github.com/en/contributing/style-guide-and-content-model/style-guide},
  note         = {Normative guidance on technical documentation style, formatting, and naming conventions}
}

@misc{standard_readme_spec,
  author       = {Richard Littauer},
  title        = {Standard README Specification},
  year         = {2024},
  url          = {https://github.com/RichardLitt/standard-readme/blob/main/spec.md},
  note         = {Standard style for README files; provides sharp thresholds for ToC, descriptions, and section ordering}
}

@misc{spdx_license_list,
  author       = {{Linux Foundation}},
  title        = {SPDX License List},
  year         = {2024},
  url          = {https://spdx.org/licenses/},
  note         = {Authoritative list of common open-source licenses and their identifiers for machine-readable declarations}
}

@misc{npm_readme_docs,
  author       = {{npm Inc.}},
  title        = {About package README files},
  year         = {2024},
  url          = {https://docs.npmjs.com/about-package-readme-files/},
  note         = {README rendering and expectations in npm registry context}
}

@misc{makeareadme,
  author       = {Katherine Peterson},
  title        = {Make a README},
  year         = {2020},
  url          = {https://www.makeareadme.com/},
  note         = {Practical guide and template for writing READMEs}
}

@misc{utrecht_readme,
  author       = {{Utrecht University}},
  title        = {README files — Computational Reproducibility Workshop},
  year         = {2022},
  url          = {https://utrechtuniversity.github.io/workshop-computational-reproducibility/chapters/readme-files.html},
  note         = {Academic perspective emphasizing reproducibility and clarity}
}

@misc{awesome_readme,
  author       = {Matias Singers},
  title        = {Awesome README},
  year         = {2024},
  url          = {https://github.com/matiassingers/awesome-readme},
  note         = {Curated collection of README examples, tools, and articles}
}

@misc{awesome_readme_articles,
  author       = {Matias Singers},
  title        = {Awesome README — Articles Section},
  year         = {2024},
  url          = {https://github.com/matiassingers/awesome-readme#articles},
  note         = {Curated list of articles on README best practices}
}

@misc{awesome_readme_examples,
  author       = {Matias Singers},
  title        = {Awesome README — Examples Section},
  year         = {2024},
  url          = {https://github.com/matiassingers/awesome-readme#examples},
  note         = {Collection of exemplary README implementations}
}

@misc{awesome_readme_tools,
  author       = {Matias Singers},
  title        = {Awesome README — Tools Section},
  year         = {2024},
  url          = {https://github.com/matiassingers/awesome-readme#tools},
  note         = {Tooling ecosystem for README generation and enhancement}
}

@misc{awesome_readme_gifs,
  author       = {Matias Singers},
  title        = {Awesome README — Creating GIFs},
  year         = {2024},
  url          = {https://github.com/matiassingers/awesome-readme#creating-gifs},
  note         = {Tools for creating visual demonstrations in READMEs}
}

@article{preston_werner_readme,
  author       = {Tom Preston-Werner},
  title        = {Readme Driven Development},
  year         = {2010},
  url          = {https://tom.preston-werner.com/2010/08/23/readme-driven-development.html},
  note         = {Seminal article proposing README-first design methodology}
}

@misc{thoughtbot_readme,
  author       = {thoughtbot},
  title        = {How to Write a Great README},
  year         = {2013},
  url          = {https://thoughtbot.com/blog/how-to-write-a-great-readme},
  note         = {Widely cited practical guide emphasizing clarity and examples}
}

@misc{yegor_elegant_readme,
  author       = {Yegor Bugayenko},
  title        = {Elegant READMEs},
  year         = {2019},
  url          = {https://www.yegor256.com/2019/04/23/elegant-readme.html},
  note         = {Minimalist approach emphasizing concision and structure}
}

@misc{art_of_readme,
  author       = {Stephen Whitmore},
  title        = {The Art of README},
  year         = {2014},
  url          = {https://github.com/hackergrrl/art-of-readme},
  note         = {Conceptual model introducing cognitive funneling}
}

@misc{stacoviak_top10,
  author       = {Adam Stacoviak},
  title        = {Top 10 Reasons Why I Won't Use Your Open Source Project},
  year         = {2013},
  url          = {https://changelog.com/posts/top-ten-reasons-why-i-wont-use-your-open-source-project},
  note         = {Adoption-focused critique emphasizing README importance}
}

@misc{freecodecamp_readme_growth,
  author       = {freeCodeCamp},
  title        = {What I Learned from an Old GitHub Project that Won 3000 Stars in a Week},
  year         = {2017},
  url          = {https://www.freecodecamp.org/news/what-i-learned-from-an-old-github-project-that-won-3-000-stars-in-a-week-628349a5ee14/},
  note         = {Empirical evidence linking README quality to engagement}
}

@misc{johnjago_docs,
  author       = {John Jago},
  title        = {Great Docs},
  year         = {2022},
  url          = {https://johnjago.com/great-docs/},
  note         = {Analysis of documentation structure in real-world projects}
}

@misc{matklad_architecture,
  author       = {Aleksey Kladov},
  title        = {ARCHITECTURE.md},
  year         = {2021},
  url          = {https://matklad.github.io/2021/02/06/ARCHITECTURE.md.html},
  note         = {Distinction between README and architecture documentation}
}

@misc{reddit_readme_discussion,
  author       = {{Reddit /r/learnprogramming}},
  title        = {How to Write a README},
  year         = {2022},
  url          = {https://www.reddit.com/r/learnprogramming/comments/vxfku6/how_to_write_a_readme/},
  note         = {Informal practitioner discussion; recurring emphasis on explicit clone, build, run, and test steps}
}

@misc{best_readme_template,
  author       = {Othneil Drew},
  title        = {Best README Template},
  year         = {2020},
  url          = {https://github.com/othneildrew/Best-README-Template},
  note         = {Widely used template demonstrating structured README design}
}

@misc{awesome_profile_readmes,
  author       = {Abhishek Naidu},
  title        = {Awesome GitHub Profile READMEs},
  year         = {2024},
  url          = {https://github.com/abhisheknaiidu/awesome-github-profile-readme},
  note         = {Examples of dynamic and visual README patterns}
}

@misc{devto_profile_readmes,
  author       = {GitHub / dev.to},
  title        = {10 Standout GitHub Profile READMEs},
  year         = {2022},
  url          = {https://dev.to/github/10-standout-github-profile-readmes-h2o},
  note         = {Examples of advanced README design patterns}
}
```

#### E.3 Tooling and Ecosystem References

Tooling references are included within the entries above where applicable. Specific tools referenced include README generators (Best README Template), visualization tools (Awesome README — Creating GIFs), and validation-adjacent tools (community linters and formatters).

#### E.4 Informal and Community Sources

Community sources include Reddit discussions, practitioner blog posts, and forum threads. These are cited within the bibliography entries above with appropriate `note` fields.

#### E.5 Annotated Bibliography (Optional)

Each source listed above includes a `note` field summarizing its relevance to this specification. Key sources include GitHub's official README documentation (defining baseline platform expectations), Tom Preston-Werner's "Readme Driven Development" (establishing README-first methodology), Stephen Whitmore's "The Art of README" (introducing the cognitive funnel concept), and Utrecht University's reproducibility workshop materials (providing academic grounding for README as knowledge preservation artifact).
