# The Four-Layer Stack

> The 2026 reframing of the five pillars into a shippable architecture.

## Why reframe

The five pillars of the 2025 essay were a checklist of what had to be true before an automated decision could be trusted. By 2026 most of them ship as product capabilities from major model providers. What remains is composition  -  how the pillars stand together into a single, auditable decision surface.

The four-layer stack is the composition. Each layer has a clear responsibility, a clear interface, and a clear boundary with its neighbors. A decision flows top-down through validation and bottom-up through evidence.

## The stack

```
+--------------------------------------------------+
|  Layer 4  -  Audit Trail                           |
|  Persists who saw what, when, with what          |
|  evidence. Surfaces to operators and end users.  |
+--------------------------------------------------+
                      ^ read          v enforce
+--------------------------------------------------+
|  Layer 3  -  Business Guardrails                   |
|  Encodes policy, compliance, jurisdictional      |
|  rules. References Layer 1 + Layer 4.            |
+--------------------------------------------------+
                      ^ read          v enforce
+--------------------------------------------------+
|  Layer 2  -  Runtime Validation                    |
|  Captures calibration, drift, segment-aware      |
|  signals. Surfaces knobs to the user.            |
+--------------------------------------------------+
                      ^ read          v enforce
+--------------------------------------------------+
|  Layer 1  -  Typed Model                           |
|  The decision surface. Typed questions, declared |
|  answer shapes, calibrated probabilities.        |
+--------------------------------------------------+
```

## Layer 1  -  Typed Model

**Responsibility.** Accept a structured state and typed questions; emit a typed decision with calibrated probabilities.

**Interface in.** A state object (domain-defined), a set of typed questions (each declaring its answer shape), and the runtime knobs from Layer 2.

**Interface out.** A typed decision: option chosen, calibrated probability, supporting evidence per option, and the question ID.

**Why a layer, not just a prompt.** A typed surface makes the audit trail structurally true. The question ID, the criteria map, and the answer form the trail by construction; there is nothing to remember to log.

**2025 lineage:** pillars 1 and 3 (provenance tracking and chain of evidence). The 2026 stack absorbs both.

## Layer 2  -  Runtime Validation

**Responsibility.** Tune Layer 1's runtime; observe per-segment behavior; surface knobs to the user.

**Interface in.** A calibration target (per segment, defined by the domain owner), a feedback signal from Layer 4.

**Interface out.** Runtime parameters set per call (temperature, top-p, cache state, tool budget, retrieval depth), drift reports per segment, and an evidence-aware feedback surface to the user.

**Why a layer, not just hyperparameters.** Context engineering, when surfaced to the user, becomes a runtime signal rather than a hidden knob. The user sees what the model sees. The user can adjust it. The user can ask why it was set this way.

**2025 lineage:** pillars 2 and 5 (contextual signature mapping and human validation points). The 2026 stack absorbs both.

## Layer 3  -  Business Guardrails

**Responsibility.** Enforce domain-specific policy. Reference Layers 1 and 4. Reject or escalate decisions that violate.

**Interface in.** A guardrail DSL authored by domain experts, the typed decision from Layer 1.

**Interface out.** Allowed / blocked / escalated verdict, the violated rule, the evidence the rule referenced.

**Why a layer, not just a prompt with rules.** Guardrails written in a prompt are invisible. Guardrails written in a DSL with reference to the COTS are auditable: the operator can answer "why was this rejected?" with the same evidence chain.

**2025 lineage:** pillars 3 and 4 (chain of evidence and explainability anchoring) plus domain-policy work that fell outside the 2025 framing.

## Layer 4  -  Audit Trail

**Responsibility.** Persist the COTS for every decision. Surface to operators and, where appropriate, to end users.

**Interface in.** The COTS bundle from Layer 1 (optionally extended by Layers 2 and 3).

**Interface out.** Reconstructed decisions, segment-level drift reports, regulator-grade exports, and (where the user invokes it) a user-visible reasoning breadcrumb trail.

**Why a layer, not just logging.** Logs are for engineers. The audit trail is a user-facing surface in domains where the user must be able to verify the reasoning.

**2025 lineage:** pillar 4 (explainability anchoring) plus the operator-side work the 2026 essays describe.

## The COTS  -  the artifact that crosses layers

Every decision produces a **Chain of Orchestrable and Traceable Sources** (COTS). It is the contract between layers and the artifact that survives the audit trail.

A COTS contains:

- **Inputs**  -  every data point that shaped the decision, with provenance metadata
- **Context**  -  runtime parameters set for this call, with rationale
- **Decisions**  -  every decision point in the workflow, with the option set and rationale
- **Evidence**  -  the chain linking each output to its supporting data and reasoning step
- **Validation**  -  feedback surfaces exposed back to the user for this decision

The COTS is what "Source Engineering" actually means in practice: a single artifact that is auditable, reproducible, and round-trippable.

## Open questions

These are the questions each layer must answer before we can call the stack "shipped":

- **Layer 1.** How typed can the answer shapes get before the workflow expresses them only once and stops paying the cost?
- **Layer 2.** Can drift be surfaced per-segment without leaking segment identity? Who authorizes a segment definition?
- **Layer 3.** Can domain experts author guardrails, or must engineers always translate? Where is the DSL line?
- **Layer 4.** Where does the audit trail surface to the end user? What does it cost in latency, and what does it save in re-litigation?

These become the slices. See [`ROADMAP.md`](../../ROADMAP.md).
