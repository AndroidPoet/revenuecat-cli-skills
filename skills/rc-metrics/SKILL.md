---
name: rc-metrics
description: View subscription metrics, project status dashboard, and live-updating metrics watch.
---

# Metrics & Monitoring

Use this skill when checking subscription health, viewing dashboards, or monitoring metrics in real-time.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set

## Metrics overview

```bash
rc metrics overview
rc metrics overview --pretty
rc metrics overview -o table
```

Returns: Active Subscribers, Active Trials, MRR, Revenue.

## Status dashboard

One-command project overview with apps, entitlements, offerings, and metrics:

```bash
rc status
```

Output:
```
Project: proj561f52f3
  Apps:              3
  Entitlements:      1
  Offerings:         1
  Active Subscribers: 0
  Active Trials:     0
  MRR:               $0.00
  Revenue:           $0.00
```

## Live watch

Auto-refreshing terminal dashboard:

```bash
rc watch metrics                    # Refresh every 5 seconds
rc watch metrics --interval 10s     # Custom interval
rc watch metrics --interval 30s     # Slower refresh
```

Press Ctrl+C to stop.

## Agent behavior

- Use `rc status` for a quick project health check
- Use `rc watch metrics` when the user wants to monitor in real-time
- Use `rc metrics overview -o table` for human-readable single snapshot
- Default JSON output is useful for programmatic parsing
