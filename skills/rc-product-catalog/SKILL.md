---
name: rc-product-catalog
description: Manage products, entitlements, offerings, and packages — the building blocks of your RevenueCat subscription model.
---

# Product Catalog

Use this skill when managing the product catalog — products, entitlements, offerings, and packages.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set via `rc init` or `--project` flag

## Products

### List and inspect products

```bash
rc products list
rc products get --product-id prod_xxx
```

### Create a product

```bash
rc products create --store-identifier com.app.monthly --type subscription --app-id app_xxx
```

### Delete a product

```bash
rc products delete --product-id prod_xxx --confirm
```

## Entitlements

### List and inspect entitlements

```bash
rc entitlements list
rc entitlements get --entitlement-id entl_xxx
```

### Create an entitlement

```bash
rc entitlements create --lookup-key premium --display-name "Premium"
```

### Update an entitlement

```bash
rc entitlements update --entitlement-id entl_xxx --display-name "Premium+"
```

### Attach/detach products

```bash
rc entitlements list-products --entitlement-id entl_xxx
rc entitlements attach-products --entitlement-id entl_xxx --product-ids prod1,prod2
rc entitlements detach-products --entitlement-id entl_xxx --product-ids prod1
```

### Delete an entitlement

```bash
rc entitlements delete --entitlement-id entl_xxx --confirm
```

## Offerings

### List and inspect offerings

```bash
rc offerings list
rc offerings get --offering-id ofrngs_xxx
```

### Create an offering

```bash
rc offerings create --lookup-key default --display-name "Default Offering"
```

### Update an offering

```bash
rc offerings update --offering-id ofrngs_xxx --is-current
rc offerings update --offering-id ofrngs_xxx --metadata '{"theme":"dark"}'
```

### Delete an offering

```bash
rc offerings delete --offering-id ofrngs_xxx --confirm
```

## Packages

### List and inspect packages

```bash
rc packages list --offering-id ofrngs_xxx
rc packages get --package-id pkg_xxx
```

### Create a package

```bash
rc packages create --offering-id ofrngs_xxx --lookup-key monthly --display-name "Monthly"
```

### Update a package

```bash
rc packages update --package-id pkg_xxx --display-name "Monthly Plan"
```

### Attach/detach products

```bash
rc packages list-products --package-id pkg_xxx
rc packages attach-products --package-id pkg_xxx --product-ids prod1,prod2
rc packages detach-products --package-id pkg_xxx --product-ids prod1
```

### Delete a package

```bash
rc packages delete --package-id pkg_xxx --confirm
```

## Common workflows

### Set up a new subscription offering

```bash
# 1. Create the entitlement
rc entitlements create --lookup-key premium --display-name "Premium Access"

# 2. Create the offering
rc offerings create --lookup-key default --display-name "Default"

# 3. Create packages within the offering
rc packages create --offering-id ofrngs_xxx --lookup-key monthly --display-name "Monthly"
rc packages create --offering-id ofrngs_xxx --lookup-key annual --display-name "Annual"

# 4. Attach products to packages
rc packages attach-products --package-id pkg_monthly --product-ids prod_monthly
rc packages attach-products --package-id pkg_annual --product-ids prod_annual

# 5. Attach products to the entitlement
rc entitlements attach-products --entitlement-id entl_xxx --product-ids prod_monthly,prod_annual

# 6. Set as current offering
rc offerings update --offering-id ofrngs_xxx --is-current
```

## Agent behavior

- Show current state before making changes
- Use `--dry-run` for destructive operations
- Confirm product IDs before attaching/detaching
