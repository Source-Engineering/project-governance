# WBS Epic: Advancement Plan (Robust, Reputable, Complete)

This epic turns the discipline from a well-documented idea with a working Layer 1 demo into a robust, reputable, and complete system: every layer of the four-layer stack shipped, every claim machine-verifiable, every repository CI-green and released, and an adoption path under 15 minutes.

The plan follows the discipline's own doctrine: complete the current layer before expanding the next, each phase ships a vertical slice (spec, reference implementation, conformance, tools, practice together), and each phase closes one or more open questions.

## Phasing at a glance

```
Phase 0  ████████                          hardening (weeks 1-2)
Phase 1       ███████████████               Layer 2 floor, RFC-0001 (weeks 3-6)
Phase 2             ████████████            semantic conformance (weeks 5-8, overlaps)
Phase 3                  ██████████████████ Layer 3 DSL (weeks 8-13)
Phase 4                            ████████████  Layer 4 audit (weeks 12-16)
Phase 5                 ──────────────────────────── evidence & adoption (ongoing)
```

## Phase 0  -  Harden the Foundation

Nothing else is reputable until the existing surface is green, versioned, and automated.

- [ ] Fix hardcoded `se-ref` path in `source-engineering-tools/tests/tools.test.ts` with a checked-in example COTS fixture
- [ ] Add GitHub Actions CI (`npm install && npm test`) to conformance, reference-implementation, and tools
- [ ] Add typecheck (`tsc --noEmit`) to the same CI
- [ ] Tag `v0.1.0` releases in specifications, reference-implementation, conformance, and tools, with GitHub Releases notes
- [ ] Publish a compatibility matrix (spec x conformance x ref-impl x tools versions), generated in CI
- [ ] Sweep ROADMAP for stale repo paths left over from the monorepo era

**Closes:** nothing ships silently broken again; every claim is anchored to a tag.

## Phase 1  -  Ship the Layer 2 Floor (RFC-0001 vertical slice)

The single highest-leverage move: RFC-0001 is already written and In Review. Ship it as one cross-repo slice.

- [ ] Add `decisions[*].validation` (ValidationFlags, `decision_on_validation`, runtime metadata) to the COTS schema; bump to v0.2 (specifications)
- [ ] Author normative JSON Schema files under `cots/schemas/v1/` (draft 2020-12) (specifications)
- [ ] Implement the `Layer2` module: Layer-1 DecisionRecord + Context in, Validation record attached (reference-implementation)
- [ ] Add TC-L2-01..N test cases and validators; runner loads the JSON Schemas natively (conformance)
- [ ] Add `se-trace validate-runtime` subcommand surfacing ValidationFlags (tools)
- [ ] Handbook chapter: reading a Layer-2 Validation record (practice)
- [ ] Merge RFC-0001 with implementation evidence attached; CHANGELOG entries across repos (governance)

**Closes:** "Layer 2 exists in prose only."

## Phase 2  -  Make Conformance Semantic

The conformance suite currently checks presence, not integrity. A structurally present COTS can still cite itself, which the first case study proved is where trust actually breaks.

- [ ] URN grammar validation: every `urn:source-engineering:*` well-formed and version-pinned
- [ ] Evidence-chain DAG resolution: every decision's evidence URNs resolve to inputs or prior decisions
- [ ] RFC-0002 mechanics: `source_type` + chain-termination policy; validator flags self-citing COTS
- [ ] Temporal integrity: `produced_at` ordering, no evidence from the future, source expiry handling
- [ ] Negative test corpus: malformed, expired, and recursive fixtures the suite must fail correctly
- [ ] Conformance badge: machine-readable level (structural / semantic / full)

**Closes:** "the suite proves the COTS is trustworthy, not just present."

## Phase 3  -  Layer 3: Business Guardrails DSL (Slice 5)

- [ ] RFC-0003: Guardrail DSL grammar referencing COTS schema fields, compiling to predicates
- [ ] Reference implementation `Layer3` module: evaluates guardrails against the COTS, emits pass/fail/override records to the audit trail
- [ ] Test corpus from the legal case-study findings
- [ ] `se-trace check-guardrails` command + practice chapter for domain-expert authoring
- [ ] TC-L3 conformance cases

**Closes:** "Can domain experts author guardrails without engineers?" (Slice 5 open question)

## Phase 4  -  Layer 4: Audit Trail

- [ ] RFC-0004: audit-trail persistence contract; append-only event log of who saw what COTS, when, with what evidence, and what they did (appeal / rerun / correction / override)
- [ ] Reference implementation `Layer4` store: JSONL append-only first; storage interface so Postgres or immutable ledgers plug in
- [ ] The discipline's signature end-to-end test: reconstruct any decision from its COTS + audit trail alone
- [ ] RFC-0005: privacy and redaction; how an immutable audit trail coexists with GDPR deletion and PII redaction
- [ ] `se-trace audit`: replay a decision's full lifecycle from the trail

**Closes:** all four layers floored. The discipline matches its own name.

## Phase 5  -  Evidence and Adoption (ongoing, starts once Phase 1 lands)

- [ ] Second-domain case study: finance transaction-routing (decision-type already registered; lowest-effort cross-domain win, closes Slice 6's open question)
- [ ] Research protocol per domain: standardized hesitation-factor measurement so results are comparable across domains
- [ ] Adopter quickstart: `npx`-runnable path from zero to a validated COTS in under 15 minutes
- [ ] COTS Explorer: static web UI on top of `se-trace visualize` (the demo-able surface)
- [ ] Publisher-side dogfooding: one recorded, reproducible example of a COTS produced from a real LLM call via the Anthropic adapter, validated by the suite
- [ ] Cross-provider adapters: OpenAI and Gemini grounding APIs
- [ ] Evidence-anchored reasoning benchmark suite

## Cross-cutting rules

1. Vertical slices only: each phase touches spec, reference implementation, conformance, tools, and practice together; never prose without code.
2. RFC before floor: Layers 3 and 4 each open an RFC first, mirroring the RFC-0001 pattern.
3. CI-green is a merge precondition everywhere from Phase 0 onward.
4. Tag and release at each floor: v0.2 (Layer 2), v0.3 (Layer 3 + semantic conformance), v0.4 (Layer 4 complete stack).
5. Update ROADMAP.md and the epics as each slice lands.

## Acceptance

- Every layer of the four-layer stack is floored with spec, code, conformance tests, tooling, and practitioner guidance
- All code repositories are CI-green with tests and typecheck enforced on PRs
- Releases are tagged per floor with a published compatibility matrix
- A second domain's case study is published with standardized hesitation-factor measurement
- A new adopter can go from zero to a validated COTS in under 15 minutes
