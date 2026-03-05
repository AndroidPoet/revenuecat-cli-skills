---
name: rc-project-ops
description: Project operations — diff between projects, export/import configurations, and manage multiple projects.
---

# Project Operations

Use this skill for cross-project operations — comparing, exporting, importing, and managing project configurations.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set (except for `diff` which takes explicit source/target)

## Compare two projects

```bash
rc diff --source proj_staging --target proj_prod
```

Compares entitlements and offerings between two projects by lookup key. Shows:
- Resources only in source
- Resources only in target
- Resources in both

Useful for verifying staging matches production before deploying.

## Export project configuration

```bash
rc export                                    # Export to rc-export.yaml
rc export --file my-config.yaml              # Custom filename
```

Exports all entitlements, offerings, and packages as YAML. Use for:
- Backing up project configuration
- Version controlling your RevenueCat setup
- Migrating between projects

Example output:
```yaml
version: "1"
project_id: proj561f52f3
entitlements:
  - lookup_key: pro
    display_name: Mindly Pro
offerings:
  - lookup_key: default
    display_name: Default Offering
    is_current: true
    packages:
      - lookup_key: $rc_monthly
        display_name: Monthly
      - lookup_key: $rc_annual
        display_name: Annual
```

## Import project configuration

```bash
rc import --file my-config.yaml --confirm          # Import config
rc import --file my-config.yaml --dry-run           # Preview what would be created
```

Creates entitlements, offerings, and packages from a YAML file. Skips resources that already exist (by lookup key).

## Manage projects

```bash
rc projects list                                    # List all projects
rc projects create --name "My New Project"          # Create a project
```

## Common workflows

### Clone config from staging to production

```bash
# 1. Export from staging
rc export --project proj_staging --file staging.yaml

# 2. Preview import to production
rc import --project proj_prod --file staging.yaml --dry-run

# 3. Import to production
rc import --project proj_prod --file staging.yaml --confirm
```

### Verify staging matches production

```bash
rc diff --source proj_staging --target proj_prod
```

### Backup before making changes

```bash
rc export --file backup-$(date +%Y%m%d).yaml
```

## Agent behavior

- Always use `--dry-run` first when importing
- Show diff output before suggesting import
- Suggest export as backup before destructive operations
- Use `rc diff` to verify after import
