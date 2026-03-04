---
name: rc-paywalls
description: Create and manage paywall configurations for offerings.
---

# Paywalls

Use this skill when managing paywall configurations.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set
- Offering must exist before creating a paywall

## Commands

### List paywalls

```bash
rc paywalls list
```

### Get paywall details

```bash
rc paywalls get --paywall-id pw_xxx
```

### Create a paywall

```bash
rc paywalls create --offering-id ofrngs_xxx
```

### Delete a paywall

```bash
rc paywalls delete --paywall-id pw_xxx --confirm
```

## Agent behavior

- Verify the offering exists before creating a paywall
- Show paywall details before deleting
