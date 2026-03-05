---
name: rc-report
description: Generate full project reports as PDF, HTML, JSON, or YAML — including metrics, apps, products, entitlements, offerings, and packages.
---

# Project Reports

Use this skill when the user wants to export, download, or generate a report of their RevenueCat project data.

## Preconditions

- Auth configured (`rc doctor` passes)
- Project ID set
- For PDF format: Chrome, Chromium, Brave, or Edge installed

## Generate reports

### PDF report (direct export)

```bash
rc report --format pdf
rc report --format pdf --file my-report.pdf
```

Generates a professional, print-ready PDF with metric cards, tables, and branding. Uses Chrome headless under the hood.

### HTML report

```bash
rc report --format html
rc report --format html --file report.html
```

Opens in any browser. Can also be printed to PDF manually via Cmd+P / Ctrl+P.

### JSON report

```bash
rc report --format json
rc report --format json --file report.json
```

Machine-readable structured data. Pipe to `jq` for processing.

### YAML report

```bash
rc report --format yaml
rc report --format yaml --file report.yaml
```

Human-readable, easy to diff and version control.

## What's included

Every report contains:
- **Summary metrics**: Active Subscribers, Active Trials, MRR, Revenue
- **Resource counts**: Apps, Products, Entitlements, Offerings, Packages
- **Apps**: ID, Name, Type (app_store, play_store, etc.)
- **Products**: ID, Store Identifier, Type, App ID
- **Entitlements**: ID, Lookup Key, Display Name
- **Offerings**: ID, Lookup Key, Display Name, Current status
- **Packages**: Nested under each offering with ID, Lookup Key, Display Name

## Default filenames

| Format | Default file |
|--------|-------------|
| html | `rc-report.html` |
| pdf | `rc-report.pdf` |
| json | `rc-report.json` |
| yaml | `rc-report.yaml` |

## Agent behavior

- Use `--format pdf` when the user asks for a PDF or downloadable report
- Use `--format json` when the user wants to process data programmatically
- Use `--format html` when the user wants to view in a browser
- Always mention the output file path after generation
- If PDF fails (no Chrome), suggest `--format html` as fallback
