---
name: rc-customer-management
description: Full customer lifecycle — lookup, attributes, entitlements, subscriptions, transfers, and grants.
---

# Customer Management

Use this skill when managing customers — lookup, attributes, entitlements, subscriptions, and lifecycle operations.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set

## Lookup

```bash
rc customers list
rc customers get --customer-id user_xxx
rc customers create --customer-id user_xxx
```

## Customer data

### Entitlements and subscriptions

```bash
rc customers list-active-entitlements --customer-id user_xxx
rc customers list-subscriptions --customer-id user_xxx
rc customers list-purchases --customer-id user_xxx
rc customers list-invoices --customer-id user_xxx
```

### Aliases and attributes

```bash
rc customers list-aliases --customer-id user_xxx
rc customers list-attributes --customer-id user_xxx
rc customers set-attributes --customer-id user_xxx --attributes '{"key":"value"}'
```

## Entitlement management

### Grant a promotional entitlement

```bash
rc customers grant-entitlement --customer-id user_xxx --entitlement-id entl_xxx
```

### Revoke an entitlement

```bash
rc customers revoke-entitlement --customer-id user_xxx --entitlement-id entl_xxx
```

## Offering override

```bash
rc customers assign-offering --customer-id user_xxx --offering-id ofrngs_xxx
```

## Transfer

```bash
rc customers transfer --customer-id user_xxx --target-id user_yyy
```

## Delete

```bash
rc customers delete --customer-id user_xxx --confirm
```

## Common workflows

### Debug a customer's subscription state

```bash
# 1. Get customer details
rc customers get --customer-id user_xxx --pretty

# 2. Check active entitlements
rc customers list-active-entitlements --customer-id user_xxx -o table

# 3. Check subscriptions
rc customers list-subscriptions --customer-id user_xxx -o table

# 4. Check purchases
rc customers list-purchases --customer-id user_xxx -o table
```

### Grant promotional access

```bash
# 1. Verify the entitlement exists
rc entitlements get --entitlement-id entl_xxx

# 2. Grant it to the customer
rc customers grant-entitlement --customer-id user_xxx --entitlement-id entl_xxx

# 3. Verify it's active
rc customers list-active-entitlements --customer-id user_xxx
```

## Agent behavior

- Always show customer details before making changes
- Confirm customer ID before destructive operations
- Use `--dry-run` when available
- Show entitlement state before and after grant/revoke
