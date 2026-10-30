# Source Engineering  -  Roadmap

> A phased, slice-by-slice plan. Each slice is shippable. Each slice closes one or more open questions.
>
> The discipline has completed the polyrepo rollout and seeded v0.1 content across the organisation. The forward plan from v0.1 to a robust, reputable, and complete system is captured in the Advancement Plan epic: [`.github/epics/advancement-plan.md`](.github/epics/advancement-plan.md). Slices 0 through 2 below have shipped as the v0.1 floor; the Advancement Plan phases supersede the slice numbering for work from here on.

## Phasing principle

**Complete the current layer before expanding the next.** A four-layer stack discipline earns its name by shipping each layer end-to-end, not by widening the surface. Slices below are listed in their build order; a slice does not start until every prior slice is either shipped or explicitly deferred via CR.

---

## Slice 0  -  Scaffold (shipped)

**Goal:** Establish the discipline on GitHub and Kanban. Land a working repo with manifesto, reframed architecture, pillar stubs, license, and contributing guide.

**Done when:**
- The discipline's canonical artifacts (README, MANIFESTO, ROADMAP, four-layer-stack.md, pillar sub-folder stubs, LICENSE (Apache-2.0), CONTRIBUTING, .github/README.md) are public under the `Source-Engineering` organisation, one authoritative home per artefact per the organisation map in [README.md](README.md)
- The org profile README links both source essays and is the canonical landing page for the discipline
- The work is linked to a dedicated Source Engineering Kanboard project via a project card
- GitHub Project board exists with WBS epic issues (Pillars / Architecture / Reference Implementation / Validation Domains / Advancement Plan)
- The slice lives on `main`

**Status:** shipped via the polyrepo rollout (ADR-0001).

---

## Slice 1  -  Framework Spec (shipped)

**Goal:** Land the framework as a written specification  -  the interfaces, the COTS schema, the layer responsibilities  -  without code yet.

**Scope:**
- `docs/framework/cots-schema.md`  -  the COTS JSON/YAML/TOML schema, version 0.1
- `docs/framework/layer-01-typed-model.md`  -  typed question interface contract
- `docs/framework/layer-02-runtime-validation.md`  -  runtime calibration API
- `docs/framework/layer-03-business-guardrails.md`  -  guardrail DSL
- `docs/framework/layer-04-audit-trail.md`  -  audit-trail persistence contract
- Interface-first: every layer's inputs, outputs, and failure modes

**Closes open question:** What does the COTS schema need to expose to be a usable contract?

---

## Slice 2  -  Reference Implementation (typed-model slice) (shipped)

**Goal:** First runnable artifact. A minimal typed-model interface in a single language (TBD, likely Python with type hints + pydantic, or TypeScript with zod) that demonstrates COTS emission for a single decision.

**Scope:**
- One canonical decision ("approve / reject / refer" with calibrated probabilities)
- Carry the full COTS from input to audit log
- One test that proves the audit trail reconstructs the decision end-to-end

**Closes open question:** Can a COTS emit alongside the decision in one call, in a single language, without losing fidelity?

---

## Slice 3  -  Validation Domain: Legal Document Summarization

**Goal:** Apply the framework to the legal-document-summarization prototype named in the 2025 essay. Use the typed-model + audit-trail pair to evaluate where the hesitation factor still bites.

**Scope:**
- Pick a narrow corpus (e.g. one jurisdiction, one document type)
- Run the framework against a small practitioner panel
- Capture the hesitation factor at every decision point
- Publish findings as a Slice 3 report

**Closes open question:** Does the framework reduce the hesitation factor in a domain where the cost of a confidently wrong decision is liability, not latency?

---

## Slice 4  -  Runtime Validation Layer

**Goal:** Implement Layer 2 (runtime validation). Calibration, per-segment drift detection, evidence-aware feedback surfaces.

**Scope:**
- Calibration API: declare segments, capture per-segment score, surface drift
- Evidence-aware feedback: tied to specific data points in the COTS, not just the overall response
- Runtime latency budget: where COTS emission is amortized vs. carried per call

**Closes open question:** Can the runtime layer surface per-segment drift without leaking segment identity?

---

## Slice 5  -  Business Guardrails DSL

**Goal:** Implement Layer 3. A domain-specific language for declaring business guardrails that reference the COTS schema.

**Scope:**
- DSL grammar
- Compilation to guardrail predicates
- Test corpus from Slice 3 findings

**Closes open question:** Can guardrails be authored by domain experts, not just engineers?

---

## Slice 6  -  Cross-Domain Validation

**Goal:** Port the framework to a second high-stakes domain (finance or medical triage candidate) and validate that the discipline's claims hold cross-domain.

**Scope:**
- Second domain (TBD with community)
- Cross-domain COTS profile variance doc
- Updated open questions

**Closes open question:** Is "judgment separate from evidence" the same claim in every high-stakes domain, or does it need per-domain framing?

---

## Slices deferred (no CR yet)

These are observed in the essays or surfaced in early kanban cards, but are not on the build path until a CR names them.

- Visualization tools for audit trails (Layer 4 UI)
- Cross-provider COTS adapters (Anthropic Citations API, OpenAI Decisions API, Gemini Grounding)
- A benchmark suite for evidence-anchored reasoning

Each will land via its own CR when ready.

---

## How slices land

Each slice ships as one or more PRs against `main`. Every PR carries:

- A CR-style summary tying the change to a slice item above
- An update to the matching pillar doc (if it touches a pillar)
- A milestone assignment on the repo (v0.x.x progressing semver)
- A linked card on the Source Engineering Kanboard project
