# Metric catalog

This catalog groups business intent rather than publishing production formulas.

## Forecast Accuracy

| Family | Examples | Decision supported |
|---|---|---|
| Volume | Forecast, actual, naive forecast | Establish scale and baseline |
| Error | Bias, absolute bias, normalized bias | Detect systematic over/under forecasting |
| Accuracy | wMAPE, MAPE, MPE, RMSE | Compare performance across periods and horizons |
| Value add | Process value add versus naive baseline | Determine whether planning improves the baseline |
| Horizon | Lag 0 through Lag 4 | Identify when a forecast becomes dependable |
| Narrative | Status and dynamic insight measures | Translate calculations into decision-ready language |

## Inventory Health

| Family | Examples | Decision supported |
|---|---|---|
| Position | On hand, in transit, on order, ATP | Understand available and committed inventory |
| Service | In-stock rate, shipable rate, demand at risk | Identify customer-service exposure |
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
