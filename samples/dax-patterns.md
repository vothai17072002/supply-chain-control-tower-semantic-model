# Generic DAX patterns

These examples demonstrate calculation patterns against fabricated names. They are not production formulas.

## Weighted forecast error

```dax
Weighted MAPE % :=
DIVIDE(
    SUMX(
        FactForecast,
        ABS(FactForecast[ForecastQty] - FactForecast[ActualQty])
    ),
    SUM(FactForecast[ActualQty])
)
```

## Forecast accuracy with a bounded result

```dax
Forecast Accuracy % :=
VAR ErrorRate = [Weighted MAPE %]
RETURN MAX(0, 1 - ErrorRate)
```

## Selected-period comparison

```dax
Inventory Value Prior Period :=
VAR WeeksBack = SELECTEDVALUE(ComparePeriod[WeeksBack], 1)
RETURN
    CALCULATE(
        [Inventory Value],
        DATEADD(DimDate[Date], -WeeksBack * 7, DAY)
    )
```

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
