# Alert message template

```
[SEVERITY] Performance Alert — [SITE] — [PAGE]

Metric:        [METRIC_NAME]
Current Value: [ACTUAL_VALUE]
Budget:        [BUDGET_VALUE]
Strategy:      [MOBILE / DESKTOP]
Deviation:     [PERCENTAGE OVER BUDGET]

Page URL:      [FULL_URL]
Test Time:     [TIMESTAMP]
Dashboard:     [LINK_TO_MONITORING_DASHBOARD]

Previous Test: [PREVIOUS_VALUE] at [PREVIOUS_TIMESTAMP]
Trend:         [IMPROVING / DEGRADING / STABLE]
```

## Example (P2)

```
[P2] Performance Alert — acme.com — Homepage

Metric:        LCP (Largest Contentful Paint)
Current Value: 3,200 ms
Budget:        2,500 ms
Strategy:      Mobile
Deviation:     28% over budget

Page URL:      https://acme.com/
Test Time:     2026-02-12 07:00 UTC
Dashboard:     https://app.apogeewatcher.com/sites/acme/results

Previous Test: 2,400 ms at 2026-02-11 07:00 UTC
Trend:         DEGRADING (↑ 800ms in 24 hours)
```
