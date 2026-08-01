# Evidence register

This register prevents a sanitized case study from presenting architectural interpretation as measured production fact. It records claim strength without retaining tenant IDs, endpoints, proprietary formulas, or raw metadata exports.

## Claim taxonomy

| Label | Meaning | Permitted language |
|---|---|---|
| **Observed** | Verified from read-only metadata at the stated point in time | “The assessed snapshot contained…” |
| **Derived** | Calculated or inferred from observed structure using a documented rule | “The structure implies…” |
| **Proposed** | Target-state control or senior-level recommendation | “The operating model should…” |
| **Not evidenced** | Requires telemetry, business approval, or personal-scope confirmation | Do not state as an achieved result |

## Registered claims

| Claim | Class | Evidence basis | Limitation |
|---|---|---|---|
| 27 model tables and 22 relationships | Observed | Read-only semantic metadata assessment dated 2026-08-01 | Point-in-time structure; not proof of quality or usage |
| 89 Forecast Accuracy and 456 Inventory Health measures | Observed | Measure inventory grouped by assessed domain | Count is not an outcome and does not prove every measure is active |
| Direct Lake for governed fact/dimension serving | Observed | Storage-mode metadata and model structure | No production latency, concurrency, capacity, or fallback result is claimed |
| Shared Calendar, Product, and Warehouse patterns | Observed | Relationship/model inventory | Diagram and names are generalized; not all physical relationships are published |
| Separate forecast and inventory analytical grains | Derived | Fact boundaries and relationship shape | Exact physical composite keys are withheld and must be validated at deployment |
| ADRs, release gates, SLOs, security controls, and 10× responses | Proposed | Architecture review of the observed shape | Production adoption and effectiveness were not assessed |
| Team size, personal authorship, user adoption, savings, and performance improvement | Not evidenced | No approved evidence retained in this repository | Must be supplied and approved before interview use |

## Verification method

1. Query accessible metadata read-only.
2. Count and classify model objects and report bindings.
3. Generalize names that expose organization-specific implementation.
4. Cross-check public claims against the sanitized machine-readable summary.
5. Store no raw data, tenant identifiers, endpoints, credentials, or proprietary DAX.

## Interpretation limits

- A binding proves technical lineage, not adoption or business value.
- A measure count describes surface area, not correctness, maintainability, or ownership.
- Metadata cannot prove SLO attainment, incident response maturity, or capacity headroom.
- Proposed controls are included to demonstrate design judgment; they are not represented as already implemented in a production tenant.

Any future impact statement should identify its approver, measurement window, baseline, method, and whether attribution is individual or team-level.
