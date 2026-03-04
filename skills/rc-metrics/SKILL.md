---
name: rc-metrics
description: View subscription metrics — MRR, active subscribers, trials, and revenue.
---

# Metrics

Use this skill when checking subscription health and business metrics.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set

## Overview

```bash
rc metrics overview
rc metrics overview --pretty
rc metrics overview -o table
```

Returns:
- **Active Subscribers** — currently active paid subscribers
- **Active Trials** — currently active trial subscriptions
- **MRR** — Monthly Recurring Revenue
- **Revenue** — total revenue

## Agent behavior

- Use `-o table` or `--pretty` for human-readable output
- Default JSON output is useful for programmatic parsing
- Present metrics in a clear, summarized format
