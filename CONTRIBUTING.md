# Contributing to Source Engineering

> This discipline is shaped by what gets built, not what gets claimed. Contributions that ship evidence beat contributions that ship prose.

## Where to start

- Read [`README.md`](README.md), [`MANIFESTO.md`](MANIFESTO.md), and [`ROADMAP.md`](ROADMAP.md) end-to-end before proposing a change.
- Skim [`docs/pillars/`](docs/pillars) and [`docs/architecture/`](docs/architecture) to see the current state of the discipline.
- Open a card on the [Source Engineering Kanboard project](https://192.168.50.160:7000/board/<project-id>)  -  name the slice it belongs to and the question it closes.

## What kinds of contribution we want

| Kind | What's welcome |
|------|---------------|
| **Pillar critique** | A disagreement with one of the five pillars or with the four-layer refactoring. Cite a working artifact, a published paper, or a real-domain experience. |
| **COTS schema proposals** | Edits to the COTS schema (Slice 1 and later). Backwards-incompatible changes need a CR. |
| **Validation-domain write-ups** | Findings from running the framework in a high-stakes domain. Even preliminary. |
| **Runtime-layer explorations** | Calibration / drift / feedback work (Slice 4). |
| **Reference implementation PRs** | One PR, one decision, one test. |
| **Editorial fixes** | Typos, broken links, unclear sentences. Smallest acceptable PR. |

## How we govern

- **Every change lands as a GitHub Issue or PR**, not as a silent push.
- **Every PR carries a CR-style summary** in the body: which slice it advances, which open question it closes.
- **Reversible until shipped.** A CR (`docs/cr/CR-NNNN.md`) is the place for breaking changes  -  interface contracts, COTS schema bumps, deprecations.
- **No silent pillars.** Every claim in the discipline must trace to a working artifact or an explicitly labeled open question.

## Style and language

- Plain prose first. Diagrams earn their place when prose alone can't carry the idea.
- No en-dashes (-, U+2013) or em-dashes ( - , U+2014) in GitHub artefacts. Use `-`, `:`, or sentence boundaries instead. (Cardinal rule.)
- No triple-semicolons (`;;`) in prose. The `;;` divider is reserved.
- Titles are sentence case in source strings; capitalization is enforced at render time, not in source.
- First-person active voice in philosophy/vision statements; third-person neutral voice in technical specs.

## The hesitation factor is the point

If you are working on high-stakes decision layers where confidently wrong answers are still possible, source engineering wants to hear from you. Open an issue or a kanban card, and we'll route it to the right slice.
