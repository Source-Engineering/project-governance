# Changelog

All notable changes to Source Engineering are recorded here. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project adheres to [Semantic Versioning](https://semver.org/) once versioning begins.

## [Unreleased]  -  Slice 0 / Scaffold

### Added

- README, MANIFESTO, ROADMAP, CONTRIBUTING, LICENSE, .github/README.md
- `docs/architecture/four-layer-stack.md`  -  the 2026 reframing of the five pillars into a shippable architecture
- `docs/pillars/01-data-provenance.md` through `05-human-validation.md`  -  pillar evolution and stack placement notes
- `framework/README.md`, `tools/README.md`  -  placeholder directories for future slices
- `.gitignore`  -  standard ignores + secrets guard (`.env`, `*.pem`, `*.key`, `*id_rsa*`)

## [Advancement Plan] - 2026 Phase Planning

### Added

- `.github/epics/advancement-plan.md` - the WBS epic turning the discipline from a working Layer 1 demo into a robust, reputable, and complete system: Phase 0 hardening (CI, releases, compatibility matrix), Phase 1 Layer 2 floor (RFC-0001), Phase 2 semantic conformance, Phase 3 Layer 3 guardrails DSL, Phase 4 Layer 4 audit trail, Phase 5 evidence and adoption

### Changed

- `ROADMAP.md` - Slices 0-2 marked shipped via the polyrepo rollout (ADR-0001); the Advancement Plan phases supersede slice numbering for work from v0.1 onward; Slice 0 stale repo references corrected to the polyrepo organisation map

## [Unreleased] - Phase 0 hardening

### Changed

- `ROADMAP.md` - stale-path sweep complete: Slice 1 artefact paths corrected to their polyrepo homes (specifications, architecture layer contracts); Slice 2 language decision recorded (TypeScript); Slice 3 marked shipped as the 2026 legal-summarization case study, with Q3.2 traced to RFC-0002
