---
name: rc-cli-usage
description: Guidance for running RevenueCat CLI commands — flags, output formats, auth profiles, pagination, and safety conventions.
---

# CLI Usage

Use this skill when you need the correct `rc` command syntax, flag combinations, or output configuration.

## Preconditions

- Install: `brew tap AndroidPoet/tap && brew install revenuecat-cli`
- Binary name: `revenuecat-cli` (alias: `rc`)
- Auth configured: `rc doctor` passes

## Global flags

| Flag | Short | Description |
|------|-------|-------------|
| `--project` | `-p` | Project ID (overrides config) |
| `--output` | `-o` | Format: json, table, csv, tsv, yaml, minimal |
| `--pretty` | | Pretty-print JSON |
| `--quiet` | `-q` | Suppress info messages |
| `--debug` | | Show HTTP request/response details |
| `--timeout` | | Request timeout (default: 60s) |
| `--dry-run` | | Preview without executing |
| `--config` | | Config file path |
| `--profile` | | Auth profile name |

## Output formats

```bash
rc apps list                # JSON (default)
rc apps list --pretty       # Pretty JSON
rc apps list -o table       # Table
rc apps list -o csv         # CSV
rc apps list -o tsv         # TSV
rc apps list -o yaml        # YAML
rc apps list -o minimal     # IDs only
```

## Pagination

All list commands support cursor-based pagination:

```bash
rc products list --limit 50                    # First 50 results
rc products list --starting-after prod_xxx     # Next page
rc products list --all                         # All pages automatically
```

## Environment variables

| Variable | Description |
|----------|-------------|
| `RC_API_KEY` | API key (overrides profile) |
| `RC_PROJECT` | Default project ID |
| `RC_PROFILE` | Auth profile name |
| `RC_OUTPUT` | Default output format |

## Safety conventions

- Destructive commands (`delete`, `cancel`, `refund`) require `--confirm`
- Use `--dry-run` to preview changes before executing
- Always verify with `rc doctor` after setup changes

## Agent behavior

- Always pass `--project` explicitly when operating on a specific project
- Use `--pretty` or `-o table` when showing output to the user
- Use `-o json` (default) when parsing output programmatically
- Use `--dry-run` for destructive operations unless the user explicitly confirms
