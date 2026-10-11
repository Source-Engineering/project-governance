# Source Engineering -- Project Governance

> The governance home for the Source Engineering discipline.

This repository governs how the Source Engineering discipline evolves. It hosts the change process, the per-channel kanban discipline rule, the ROADMAP, the WBS epics, and the canonical pointer to the discipline's intellectual home.

The discipline is published across an organisation of repositories, one authoritative home per artefact. This repo is the governance home; the other repos own specific artefacts.

## The discipline

Source Engineering is the practice of building **chains of orchestrable and traceable sources** (COTS) so a model's reasoning can be examined end-to-end; not merely trusted on the model's say-so. The discipline is grounded in two essays:

- [Source Engineering: Grounding AI-based Decisions with Integrity (December 2025)](https://nuel.otchere.com/posts/2025/12/source-engineering-grounding-ai-based-decisions-with-integrity.html)
- [Reframing the Five Pillars, One Year Later (October 2026)](https://nuel.otchere.com/posts/2026/10/reframing-the-five-pillars-one-year-later.html)

The discipline overview, organisation map, and public introduction live at the org profile: https://github.com/Source-Engineering.

## The four-layer stack

```
+--------------------------------------------------+
|  Layer 4  --  Audit Trail                          |
|  (who saw what, when, and with what evidence)     |
+--------------------------------------------------+
|  Layer 3  --  Business Guardrails                  |
|  (policy, compliance, jurisdictional rules)       |
+--------------------------------------------------+
|  Layer 2  --  Runtime Validation                   |
|  (calibration, drift, segment-aware signals)      |
+--------------------------------------------------+
|  Layer 1  --  Typed Model                          |
|  (typed questions, declared answer shapes,        |
|   calibrated probabilities)                       |
+--------------------------------------------------+
```

## Organisation of the discipline

The discipline is published as a set of repositories under the `Source-Engineering` GitHub organisation. Each repository owns a specific artefact. The full map:

| Repo | Owns |
|---|---|
| [Source-Engineering/.github](https://github.com/Source-Engineering/.github) | Org profile README that renders on the org homepage |
| [Source-Engineering/project-governance](https://github.com/Source-Engineering/project-governance) (this repo) | Change process, ADRs, RFCs, maintainer responsibilities, release policy |
| [Source-Engineering/source-engineering-foundations](https://github.com/Source-Engineering/source-engineering-foundations) | Discipline definition, principles, terminology, scope and non-goals |
| [Source-Engineering/source-engineering-research](https://github.com/Source-Engineering/source-engineering-research) | Research agenda, hypotheses, experimental protocols, evaluation reports |
| [Source-Engineering/source-engineering-model](https://github.com/Source-Engineering/source-engineering-model) | Canonical conceptual and data model |
| [Source-Engineering/source-engineering-specifications](https://github.com/Source-Engineering/source-engineering-specifications) | Normative technical requirements. COTS spec lives under `specifications/cots/` |
| [Source-Engineering/source-engineering-architecture](https://github.com/Source-Engineering/source-engineering-architecture) | Reference architecture, blueprint stack, per-layer interface contracts |
| [Source-Engineering/source-engineering-reference-implementation](https://github.com/Source-Engineering/source-engineering-reference-implementation) | Working reference code that demonstrates the spec in action |
| [Source-Engineering/source-engineering-conformance](https://github.com/Source-Engineering/source-engineering-conformance) | Conformance test suite, validation harness, badge system |
| [Source-Engineering/source-engineering-tools](https://github.com/Source-Engineering/source-engineering-tools) | Reusable software utilities: CLI, visualizer, model-card-gen, SDKs |
| [Source-Engineering/source-engineering-case-studies](https://github.com/Source-Engineering/source-engineering-case-studies) | Evaluated demonstrations, case studies |
| [Source-Engineering/source-engineering-practice](https://github.com/Source-Engineering/source-engineering-practice) | Practitioner guidance, implementation guides |
| [Source-Engineering/source-engineering-education](https://github.com/Source-Engineering/source-engineering-education) | Curriculum and learning resources |

One authoritative home per artefact. Cross-repository references are links, never copies.

## What lives in this repo

- `ROADMAP.md` -- the phased, slice-by-slice plan
- `CHANGELOG.md` -- notable changes to the discipline
- `CONTRIBUTING.md` -- how to engage with the work
- `docs/` -- the discipline's working documents (manifesto, pillars, architecture). These are interim monorepo content; the planned destination is the corresponding aspect repo per the organisation map above
- `framework/`, `tools/` -- reference framework code and tooling. Interim monorepo content
- `.github/discipline-rule.md` -- the per-channel kanban discipline rule

## Kanban and channel discipline

Work for this discipline is tracked on a dedicated Kanboard project: **http://192.168.50.160:7000/board/13** (project id 13, columns 52 Backlog / 53 Ready / 54 Work in progress / 55 Done). Every action on the discipline's Discord channel produces a kanban card, with column state matching the lifecycle, autonomously. The per-channel rule lives in `.github/discipline-rule.md`.

A public GitHub Project v2 mirrors the discipline's work for external contributors. See the project's project board on the discipline's project page once it is created in Phase 0.

## Status

This is the governance slice of the discipline. The discipline is published across the organisation of repositories listed above; the content in this repo's `docs/`, `framework/`, and `tools/` sub-directories is interim monorepo content that migrates to its authoritative home in subsequent phases.

## License

Apache-2.0. See [LICENSE](LICENSE).

## Acknowledgements

The thesis and the surrounding work are authored by Emmanuel A. Otchere. The conceptual lineage draws on OODA (`Observe -> Orient -> Decide -> Act`), Chain-of-Thought and its successors, knowledge-graph construction, and the broader explainable-AI community.
