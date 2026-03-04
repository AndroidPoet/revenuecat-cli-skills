---
name: rc-integrations
description: Set up webhooks and review audit logs for your RevenueCat project.
---

# Integrations

Use this skill when managing webhooks and reviewing audit logs.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set

## Webhooks

### List webhooks

```bash
rc webhooks list
```

### Create a webhook

```bash
rc webhooks create --url https://api.myapp.com/rc-webhook
```

## Audit Logs

### List audit logs

```bash
rc audit-logs list
rc audit-logs list --limit 50
rc audit-logs list --all
```

## Agent behavior

- Verify webhook URL is HTTPS before creating
- Use `--limit` and `--all` for paginating audit logs
- Show existing webhooks before creating duplicates
