# Generic DAX patterns

These examples demonstrate calculation patterns against fabricated names. They are not production formulas.

## Weighted forecast error (WAPE-style)

Some organizations label this pattern “weighted MAPE”; others call it WAPE. The metric contract must fix the name, eligible population, and denominator convention. This example uses absolute actual quantity and returns blank when that denominator is zero.

```dax
WAPE % :=
VAR AbsoluteError =
    SUMX(
        FactForecast,
        ABS(FactForecast[ForecastQty] - FactForecast[ActualQty])
    )
VAR ActualMagnitude =
    SUMX(FactForecast, ABS(FactForecast[ActualQty]))
RETURN
    DIVIDE(AbsoluteError, ActualMagnitude)
```

## Forecast accuracy with a bounded result

```dax
Forecast Accuracy % :=
VAR ErrorRate = [WAPE %]
RETURN
    IF(
        ISBLANK(ErrorRate),
        BLANK(),
        MAX(0, 1 - ErrorRate)
    )
```

## Selected-period comparison

This pattern assumes `DimDate` is a marked, contiguous date table and that week comparison means a seven-day shift. Fiscal-week semantics may require a governed week index instead.

```dax
Inventory Value Prior Period :=
VAR WeeksBack = SELECTEDVALUE(ComparePeriod[WeeksBack], 1)
RETURN
    CALCULATE(
        [Inventory Value],
        DATEADD(DimDate[Date], -WeeksBack * 7, DAY)
    )
```

## Semi-additive inventory snapshot

Inventory balances are additive across product and location for one snapshot, but not across dates. The following pattern selects the latest visible date; a production contract must also define what happens when that date has no trusted snapshot.

```dax
Inventory Value at Latest Visible Snapshot :=
VAR LatestVisibleDate = MAX(DimDate[Date])
RETURN
    CALCULATE(
        [Inventory Value],
        KEEPFILTERS(DimDate[Date] = LatestVisibleDate)
    )
```

## Golden-query expectations

Every sample measure should be tested under no filter, a single product/location, multiple selections, a period subtotal, the grand total, an empty eligible population, and the applicable security personas. Expected results belong in version control alongside the semantic change.

## Status as a presentation contract

```dax
KPI Status :=
SWITCH(
    TRUE(),
    ISBLANK([KPI Value]), "No data",
    [KPI Value] >= [Green Threshold], "On track",
    [KPI Value] >= [Amber Threshold], "Watch",
    "Action required"
)
```
