---
name: rc-subscription-lifecycle
description: Manage active subscriptions and purchases — get details, cancel, refund, and check entitlements.
---

# Subscription Lifecycle

Use this skill when managing subscriptions and purchases — details, cancellation, refunds, and entitlements.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set

## Subscriptions

### Get subscription details

```bash
rc subscriptions get --subscription-id sub_xxx
```

### List entitlements for a subscription

```bash
rc subscriptions list-entitlements --subscription-id sub_xxx
```

### Cancel a subscription

```bash
rc subscriptions cancel --subscription-id sub_xxx --confirm
```

### Refund a subscription

```bash
rc subscriptions refund --subscription-id sub_xxx --confirm
```

## Purchases

### Get purchase details

```bash
rc purchases get --purchase-id pur_xxx
```

### List entitlements for a purchase

```bash
rc purchases list-entitlements --purchase-id pur_xxx
```

### Refund a purchase

```bash
rc purchases refund --purchase-id pur_xxx --confirm
```

## Agent behavior

- Always show subscription/purchase details before cancelling or refunding
- Require explicit user confirmation for cancel and refund operations
- Show the entitlements that will be affected by cancellation
- Use `--pretty` or `-o table` when displaying details to the user
