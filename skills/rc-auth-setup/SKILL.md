---
name: rc-auth-setup
description: Configure authentication, manage profiles, and verify setup with doctor.
---

# Auth & Setup

Use this skill when setting up `rc` for the first time or managing auth profiles.

## First-time setup

```bash
# 1. Install
brew tap AndroidPoet/tap && brew install revenuecat-cli

# 2. Authenticate
rc auth login --api-key sk_xxxxx --name production

# 3. Set project
rc init --project proj_xxxxx

# 4. Verify
rc doctor
```

## Auth profiles

### Login with a named profile

```bash
rc auth login --api-key sk_xxxxx --name production
rc auth login --api-key sk_xxxxx --name staging --default-project proj_staging
```

### Switch between profiles

```bash
rc auth switch --name staging
```

### List and inspect profiles

```bash
rc auth list
rc auth current
```

### Delete a profile

```bash
rc auth delete --name old --confirm
```

## Project initialization

```bash
rc init --project proj_xxxxx
```

Creates `.rc.yaml` in the current directory with project defaults.

## Shell completion

```bash
rc completion bash > /etc/bash_completion.d/rc
rc completion zsh > "${fpath[1]}/_rc"
rc completion fish > ~/.config/fish/completions/rc.fish
rc completion powershell > rc.ps1
```

## Diagnostics

```bash
rc doctor
```

Checks:
1. Configuration file loads correctly
2. API key is configured
3. Project ID is set
4. RevenueCat API is reachable

## Apps management

```bash
rc apps list
rc apps get --app-id app_xxx
rc apps create --name "My App" --type play_store
rc apps update --app-id app_xxx --name "New Name"
rc apps delete --app-id app_xxx --confirm
rc apps api-keys --app-id app_xxx
```

## Projects

```bash
rc projects list
rc projects create --name "My Project"
```

## Agent behavior

- Run `rc doctor` after any auth or config change
- Use named profiles for multi-environment setups
- Store API keys securely — never log them in full
