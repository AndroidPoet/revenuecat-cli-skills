# revenuecat-cli skills

A collection of Agent Skills for the [RevenueCat CLI](https://github.com/AndroidPoet/revenuecat-cli) (`rc`). These skills teach AI coding agents how to automate RevenueCat subscription management — products, entitlements, offerings, customers, metrics, and more.

Skills follow the [Agent Skills](https://github.com/anthropics/agent-skills) format.

## Available Skills

### rc-cli-usage

Guidance for running `rc` commands — flags, output formats, auth profiles, and safety conventions.

**Use when:**
- You need the correct `rc` command or flag combination
- You want to configure auth profiles or output formats

### rc-product-catalog

Manage products, entitlements, offerings, and packages — the building blocks of your subscription model.

**Use when:**
- You're creating or organizing subscription products
- You need to attach products to entitlements or packages
- You want to set up or update offerings

### rc-customer-management

Full customer lifecycle — lookup, attributes, entitlements, subscriptions, transfers, and grants.

**Use when:**
- You need to look up a customer or their subscriptions
- You're granting or revoking entitlements
- You want to transfer a customer or set attributes

### rc-subscription-lifecycle

Manage active subscriptions and purchases — get details, cancel, refund, and check entitlements.

**Use when:**
- You need to cancel or refund a subscription
- You're checking what entitlements a subscription grants
- You want to process a purchase refund

### rc-paywalls

Create and manage paywall configurations for offerings.

**Use when:**
- You're setting up paywalls for your offerings
- You need to list or delete paywall configurations

### rc-metrics

View subscription metrics, project status dashboard, and live-updating metrics watch.

**Use when:**
- You need a quick overview of subscription health (`rc status`)
- You're checking MRR or active subscriber counts
- You want to monitor metrics in real-time (`rc watch metrics`)

### rc-report

Generate full project reports as PDF, HTML, JSON, or YAML — including metrics, apps, products, entitlements, offerings, and packages.

**Use when:**
- You need a downloadable PDF or HTML report of project data
- You want machine-readable export (JSON/YAML) for processing
- You're creating a project summary for stakeholders

### rc-project-ops

Project operations — diff between projects, export/import configurations, and manage multiple projects.

**Use when:**
- You need to compare staging vs production (`rc diff`)
- You're migrating config between projects (`rc export` / `rc import`)
- You want to back up your RevenueCat configuration as YAML

### rc-integrations

Set up webhooks and review audit logs for your project.

**Use when:**
- You need to create webhook integrations
- You want to review audit logs for changes

### rc-auth-setup

Configure authentication, manage profiles, and verify setup with doctor.

**Use when:**
- You're setting up `rc` for the first time
- You need to switch between API key profiles
- You want to verify your configuration works

## Installation

```bash
npx skills add AndroidPoet/revenuecat-cli-skills
```

## Usage

Skills are automatically available once installed. The agent will use them when relevant tasks are detected.

**Examples:**

```
Create a premium entitlement and attach my monthly subscription product
```

```
Show me the current MRR and active subscriber count
```

```
Look up customer user_123 and list their active entitlements
```

```
Set up a webhook for https://api.myapp.com/rc-webhook
```

```
Cancel subscription sub_xxx and process a refund
```

## Skill Structure

Each skill contains:
- `SKILL.md` — Instructions for the agent

## License

MIT
