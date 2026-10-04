# Performance Alert Policy

## Alert channels

```
#perf-alerts-critical
  Purpose:     P1 and P2 alerts only
  Who watches:  On-call engineer, tech lead
  Expectation:  Respond within 30 minutes during business hours
  Muted:        Never

#perf-alerts
  Purpose:     All performance alerts (P1-P4)
  Who watches:  Full engineering team
  Expectation:  Review during next standup
  Muted:        Allowed outside business hours

#client-[name]-alerts (optional)
  Purpose:     Client-specific performance alerts
  Who watches:  Account manager, assigned developer
  Expectation:  Review same business day

Email (fallback)
  Purpose:     Backup delivery for all P1 alerts
  Recipients:  tech-lead@agency.com, ops@agency.com
```

## Severity levels

```
P1 — CRITICAL
  Condition:   Any CWV in "Poor" range OR Performance Score < 50
  Thresholds:  LCP > 4.0s | INP > 500ms | CLS > 0.25 | Score < 50
  Channel:     #perf-alerts-critical + email
  Response:    Acknowledge within 30 minutes. Investigate immediately.
  Escalation:  Unacked after 1 hour → notify tech lead
  Cooldown:    4 hours

P2 — WARNING
  Condition:   CWV exceeds budget by > 20% but not Poor
  Thresholds:  LCP > 3.0s | INP > 240ms | CLS > 0.12 | Score < 75
  Channel:     #perf-alerts-critical
  Response:    Investigate within 4 hours (business hours)
  Escalation:  Unresolved after 24 hours → P1
  Cooldown:    8 hours

P3 — NOTICE
  Condition:   CWV exceeds budget by < 20%
  Thresholds:  LCP 2.5–3.0s | INP 200–240ms | CLS 0.10–0.12 | Score 75–89
  Channel:     #perf-alerts
  Response:    Review in next standup; ticket if persistent
  Escalation:  Still over after 3 consecutive tests → P2
  Cooldown:    24 hours

P4 — INFO
  Condition:   Significant improvement OR metric back within budget
  Channel:     #perf-alerts
  Response:    Awareness only
  Cooldown:    None (fire once per event)
```

## Response procedure

1. **Acknowledge** — React / reply in thread (P1: confirm investigating).
2. **Triage** — Multi-page vs one; mobile vs desktop; sudden vs gradual.
3. **Identify cause** — Deploy, third-party, server/TTFB, LCP element, CDN.
4. **Fix or escalate** — Revert/fix + retest, or ticket with severity.
5. **Verify** — Confirm metric within budget; mark resolved in thread.
6. **Post-mortem (P1 > 2h)** — What / why / fix / prevention.

## Cooldown rules

- Per page + metric + strategy within severity cooldown.
- Escalation override if severity worsens during cooldown.
- Resolution resets cooldown.
- Maintenance: suppress P3/P4 for 2h; never suppress P1/P2.

## Scheduled reporting

- **Daily digest** (09:00): tests, violations, top 3 worst pages, overnight alerts.
- **Weekly summary** (Monday): WoW trends, open alerts, API usage.
- **Monthly**: link to full report, wins/regressions, budget compliance.
