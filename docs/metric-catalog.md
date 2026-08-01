# Metric catalog

This catalog groups business intent rather than publishing production formulas.

## Forecast Accuracy

| Family | Examples | Decision supported |
|---|---|---|
| Volume | Forecast, actual, naive forecast | Establish scale and baseline |
| Error | Bias, absolute bias, normalized bias | Detect systematic over/under forecasting |
| Accuracy | WAPE, row-level MAPE, MPE, RMSE | Compare performance across periods and horizons without conflating aggregation methods |
| Value add | Process value add versus naive baseline | Determine whether planning improves the baseline |
| Horizon | Lag 0 through Lag 4 | Identify when a forecast becomes dependable |
| Narrative | Status and dynamic insight measures | Translate calculations into decision-ready language |

## Inventory Health

| Family | Examples | Decision supported |
|---|---|---|
| Position | On hand, in transit, on order, ATP | Understand available and committed inventory |
| Service | In-stock rate, shippable rate, demand at risk | Identify customer-service exposure |
| Capital | Total commitment, turns, days on hand | Monitor working-capital efficiency |
| Risk | Shortage, surplus, excess, SLOB, inactive | Prioritize intervention |
| Capacity | Used cube, free space, utilization | Identify warehouse constraints |
| Trend | Current/prior/delta and future horizon | Separate persistent from transient issues |
| Explainability | Status, colors, narratives, hotspot ranks | Make operational triage faster |

## Metric contract

Every published KPI should document:

- business definition and owner;
- base grain and eligible population;
- numerator, denominator, and blank/zero behavior;
- date context and comparison period;
- acceptable thresholds;
- reconciliation source;
- expected visual interactions.

## Representative contract templates

These are intentionally generic review contracts, not production definitions. A named business metric owner must approve eligibility, sign convention, thresholds, and reconciliation before publication.

| KPI | Calculation intent | Grain and aggregation | Blank/zero policy | Minimum regression evidence |
|---|---|---|---|---|
| WAPE / weighted error | Sum absolute forecast error divided by sum absolute actual over the same eligible population | Compute numerator and denominator at the declared forecast comparison grain, then divide; never average row-level percentages | Zero denominator returns blank plus an explicit “no eligible actual” state | Perfect forecast, mixed over/under errors, zero actual, horizon subtotal, filtered grand total |
| Forecast bias % | Sum signed error divided by the approved actual denominator | Ratio of sums; the owner documents whether positive means over- or under-forecast | Zero denominator returns blank; sign is never inferred from color alone | Balanced errors, all-over, all-under, zero actual, customer/horizon filters |
| In-stock rate | Eligible in-stock observations divided by all eligible observations | Owner chooses and documents SKU-location weighting versus demand weighting; aggregation recomputes counts | Empty population is blank, not 0%; excluded/non-stocked items are removed symmetrically | All in stock, none in stock, excluded items, mixed locations, subtotal weighting |
| Inventory value | Snapshot quantity multiplied by the governed valuation basis and currency treatment | Additive across eligible product/location for one snapshot; semi-additive over date | Missing cost is surfaced as a DQ exception, not silently valued at zero | Latest snapshot, period total, missing cost, negative/return quantity, currency reconciliation |

## Governance lifecycle

1. **Draft:** owner, definition, eligible population, and grain are recorded.
2. **Review:** data and semantic leads reconcile the base components and validate totals across representative filters.
3. **Certified:** description, display folder, format string, owner, and golden-query tests ship together.
4. **Observed:** usage and query telemetry identify redundant, slow, or confusing measures.
5. **Deprecated:** replacement and sunset date are communicated; removal waits for consumer and report dependency checks.
