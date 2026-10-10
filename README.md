# Source Engineering

> A discipline for grounding AI-based decisions with integrity.

Source Engineering is the practice of building **chains of orchestrable and traceable sources** (COTS) so a model's reasoning can be examined end-to-end  -  not merely trusted on the model's say-so. This repository is the working home for the discipline: its framework, its reference architecture, and the tools that grow around it.

The concept was introduced in the December 2025 essay [Source Engineering: Grounding AI-based Decisions with Integrity](https://nuel.otchere.com/posts/2025/12/source-engineering-grounding-ai-based-decisions-with-integrity.html) and reframed one year later in [Reframing the Five Pillars, One Year Later](https://nuel.otchere.com/posts/2026/10/reframing-the-five-pillars-one-year-later.html).

## The thesis

AI models in 2026 can produce structurally valid answers that are the wrong answers for the business. The hesitation factor  -  the gap between "the model answered" and "I can act on the answer"  -  has shrunk at the model layer but remains open at the **judgment layer**. Source Engineering exists to close that gap by turning decisions into auditable artifacts.

The discipline stands on three load-bearing claims:

1. **Provenance is a property of the response, not an afterthought.** Every input that shaped an output is logged, surfaced, and reproducible.
2. **Context is a runtime signal, not a hidden prompt.** Context engineering parameters are first-class data points back to the user, not just knobs for the model operator.
3. **Judgment is separate from evidence.** A decision that fits every declared option can still be the wrong decision for the situation. The evidence chain proves *what*; the judgment layer decides *whether*.

## The four-layer stack (2026 reframing)

The five pillars of the 2025 essay compose into a shippable stack. Each pillar becomes a layer; each layer has an interface; the layers stack.

```
+--------------------------------------------------+
|  Layer 4  -  Audit Trail                           |
|  (who saw what, when, and with what evidence)    |
+--------------------------------------------------+
|  Layer 3  -  Business Guardrails                   |
|  (policy, compliance, jurisdictional rules)      |
+--------------------------------------------------+
|  Layer 2  -  Runtime Validation                    |
|  (calibration, drift, segment-aware signals)     |
+--------------------------------------------------+
|  Layer 1  -  Typed Model                           |
|  (typed questions, declared answer shapes,       |
|   calibrated probabilities)                      |
+--------------------------------------------------+
```

The detailed layer-by-layer specification lives in [`docs/architecture/four-layer-stack.md`](docs/architecture/four-layer-stack.md). See [`docs/pillars/`](docs/pillars) for the per-pillar evolution from the 2025 framing.

The canonical manifesto lives at [`docs/00-manifesto.md`](docs/00-manifesto.md); the explicit positioning against adjacent disciplines lives at [`docs/05-positioning.md`](docs/05-positioning.md).

## The five pillars  -  what they became

| Pillar (2025)                               | 2026 form                                    | Now lives in         |
|---------------------------------------------|----------------------------------------------|----------------------|
| Data Provenance Tracking                    | Provenance-as-response, model-card mandate   | Layer 1 + Layer 4    |
| Contextual Signature Mapping                | Context engineering w/ user-visible knobs    | Layer 2              |
| Chain of Evidence Generation                | Typed decisions + structured audit trail     | Layers 1, 3, 4       |
| Explainability Anchoring                    | Trace/observe primitives surfaced to user    | Layers 2, 4          |
| Human Validation Points                     | Evidence-aware feedback w/ runtime loop      | Layers 3, 4          |

## Repository layout

```
source-engineering/
├── README.md                        -  this file
├── ROADMAP.md                       -  phased plan, slice-by-slice
├── MANIFESTO.md                     -  deprecated; superseded by docs/00-manifesto.md
├── CONTRIBUTING.md                  -  how to engage with the work
├── LICENSE                          -  Apache-2.0
├── docs/
│   ├── pillars/                     -  the five pillars, evolved
│   │   ├── 01-data-provenance.md
│   │   ├── 02-contextual-signature.md
│   │   ├── 03-chain-of-evidence.md
│   │   ├── 04-explainability-anchoring.md
│   │   └── 05-human-validation.md
│   └── architecture/
│       └── four-layer-stack.md      -  the 2026 reference architecture
├── framework/                       -  reference framework code (future slice)
│   └── README.md                    -  currently a stub describing intent
├── tools/                           -  reference tooling (future slice)
│   └── README.md                    -  currently a stub describing intent
└── .github/
    └── README.md                    -  project-level governance notes
```

Pillar folders and `framework/`, `tools/` directories are populated incrementally. See [`ROADMAP.md`](ROADMAP.md) for the next slices.

## Status

This is a **scaffold slice**. The repository contains the discipline statement, the reframed architecture, pillar stubs, and the governance surface. No production code yet; that lands in subsequent slices per the roadmap.

## Kanban and channel discipline

Work for this discipline is tracked on a dedicated Kanboard project: **http://192.168.50.160:7000/board/13** (project id 13, columns 52 Backlog / 53 Ready / 54 Work in progress / 55 Done). Every action on the discipline's Discord channel produces a kanban card, with column state matching the lifecycle, autonomously. The per-channel rule lives in `.github/discipline-rule.md`.

The current 10 open cards are seeded against this repo.

## License

Apache-2.0. See [LICENSE](LICENSE).

## Acknowledgements

The thesis and the surrounding work are authored by Emmanuel A. Otchere. The conceptual lineage draws on OODA (`Observe → Orient → Decide → Act`), Chain-of-Thought and its successors, knowledge-graph construction, and the broader explainable-AI community.
