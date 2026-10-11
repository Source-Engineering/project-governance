# WBS Epic: Reference Implementation

This epic owns the first runnable artifact of the framework. The minimal viable slice is a typed-model interface in one language that emits a COTS alongside a single decision. Later slices expand from this base.

## Acceptance

- One canonical decision ("approve / reject / refer" with calibrated probabilities) runs end-to-end
- The COTS is emitted alongside the decision
- A test reconstructs the decision from the COTS in isolation
- A second language can be ported from the same spec without restating contracts

## Children

- [ ] Story: Pick language + typing discipline (candidates: Python+pydantic, TypeScript+zod) - Spike
- [ ] Story: Define the canonical decision surface for Slice 2 - Slice 2
- [ ] Story: Emit a v0.1 COTS from one decision call - Slice 2
- [ ] Story: Test that the COTS reconstructs the decision - Slice 2
- [ ] Story: Add a second provider adapter (LLM-independent core) - Slice 2+ stretch
