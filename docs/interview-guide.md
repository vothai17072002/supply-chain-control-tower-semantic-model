# Senior/Team Lead interview guide

## 30-second answer

The core problem was semantic drift across two supply-chain decision products. The architecture uses conformed dimensions and separate forecast/inventory facts in one Direct Lake model, so business definitions are reused without corrupting grain. The senior trade-off is a larger release and regression surface, managed through domain ownership, contract tests, binding validation, telemetry, and explicit ADRs.

## Five-minute walkthrough

1. Clarify the two business domains and their grains.
2. Show the Gold → Direct Lake → shared semantic → two-report boundary.
3. Explain why dimensions are shared but facts remain separate.
4. Defend single-direction relationships and disconnected UX helpers.
5. Treat 545 measures as a governed API, not a success metric.
6. Close with failure handling, security, deployment order, and 10× scale triggers.

## Questions to invite

- Why not use two models?
- What causes Direct Lake fallback and how would you observe it?
- How do you prevent wrong totals across snapshot facts?
- How would you test hundreds of measures without testing each visual manually?
- What is the rollback unit when Gold, semantic, and reports change together?
- Which decisions belong to a team lead versus domain engineers?

## Evidence language

Use **observed** for metadata counts and bindings, **inferred** for architectural implications, and **proposed** for controls or target-state improvements. Do not claim team size, personal ownership, adoption, savings, or performance improvement unless you have approved evidence.
