# Architecture decision record

Status labels: **Observed** describes the assessed implementation, while **Proposed** describes a senior-level target control. Neither label asserts personal ownership.

## ADR-001 — Shared model with bounded domain facts

- **Status:** Observed
- **Context:** Forecast Accuracy and Inventory Health share Calendar, Product, and Warehouse, but use different temporal and analytical grains.
- **Decision:** Use one semantic model with conformed dimensions and separate domain facts/measure groups.
- **Alternatives:** Separate models per report; one flattened cross-domain fact; composite models over domain models.
- **Why:** A shared model reduces definition drift and enables reusable dimensions without forcing facts into an invalid common grain.
- **Consequences:** Release coordination and regression scope increase; domain ownership and compatibility contracts become mandatory.
- **Revisit when:** Teams require independent release cadences, capacity isolation, or materially different security boundaries.

## ADR-002 — Direct Lake over governed Gold tables

- **Status:** Observed architecture; operational controls proposed
- **Decision:** Use Direct Lake for physical facts/dimensions and calculated/import objects only for small semantic helpers.
- **Alternatives:** Import mode, DirectQuery, or mixed/composite storage.
- **Why:** Direct Lake minimizes duplicated ingestion while retaining a semantic layer over report-ready Gold data.
- **Consequences:** Performance depends on Gold layout, capacity, cardinality, framing, and fallback behavior. A successful data load does not guarantee a performant semantic query.
- **Revisit when:** Concurrency, high-cardinality columns, fallback frequency, or capacity cost breaches agreed budgets.

## ADR-003 — Single-direction star relationships

- **Status:** Observed
- **Decision:** Dimensions filter facts in one direction; disconnected tables handle UX selections.
- **Alternatives:** Bidirectional filtering, direct fact-to-fact relationships, or pre-joined report tables.
- **Why:** The selected pattern keeps filter propagation and totals explainable.
- **Consequences:** Some calculations require explicit DAX such as `TREATAS`, inactive relationship activation, or controlled virtual relationships.
- **Revisit when:** A proven business path cannot be expressed safely without a bridge or role-playing dimension.

## ADR-004 — Govern a large measure surface as a product API

- **Status:** Proposed control for an observed 545-measure surface
- **Decision:** Require display folders, owners, descriptions, naming rules, golden-query tests, usage telemetry, and deprecation windows.
- **Alternatives:** Report-local measures, duplicated domain models, or unrestricted measure creation.
- **Why:** A broad measure layer creates value only when consumers can discover and trust it.
- **Consequences:** Governance adds review overhead but lowers semantic drift and regression risk.
- **Revisit when:** Usage telemetry shows domains can be split without harming reuse.

