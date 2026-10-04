# Slack Alert Policy Template for Web Performance Teams

A complete **alert policy** for performance monitoring: channels, P1–P4 severity, message format, response steps, cooldowns, and digests — so the team knows when to page vs backlog.

**Who it's for:** DevOps, agency tech leads, engineering managers.

**What you need:** Slack (or similar) plus any monitoring tool that can route alerts by severity.

**Canonical article:** [Slack Alert Policy Template for Web Performance Teams](https://apogeewatcher.com/blog/slack-alert-policy-template-for-web-performance-teams)

**Index:** [core-web-vitals-checklists](https://github.com/Apogee-Information-Systems/core-web-vitals-checklists) · [Apogee on GitHub](https://apogee-information-systems.github.io/)

## How to use this repo
- Copy [`templates/alert-policy.md`](templates/alert-policy.md) into your team wiki.
- Use [`templates/alert-message.md`](templates/alert-message.md) as the Slack message body.
- Run the implementation checklist via **New issue → Alert policy rollout** (Issue Form).

## Severity quick reference

| Level | Condition | Channel | Response |
|:------|:----------|:--------|:---------|
| P1 Critical | CWV in Poor range or Score &lt; 50 | `#perf-alerts-critical` + email | Ack in 30 min |
| P2 Warning | Over budget by &gt; 20% | `#perf-alerts-critical` | Investigate in 4h |
| P3 Notice | Over budget by &lt; 20% | `#perf-alerts` | Next standup |
| P4 Info | Recovered / big improvement | `#perf-alerts` | Awareness only |

## Minimal policy (small teams)

- One channel: `#perf-alerts`
- Two levels: Critical vs Notice
- Cooldown: 8 hours for the same page/metric
- Critical ack within 4 hours; Notice in next standup

## Automate your monitoring

Configurable thresholds and cooldowns pair with this policy. [Apogee Watcher](https://apogeewatcher.com) supports email alerts today (Slack/webhooks on the roadmap). [Learn more →](https://apogeewatcher.com)
