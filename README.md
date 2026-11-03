# team-marketplace

A Claude Code plugin marketplace for the Invoice Maker team. Ships three reference plugins (`deploy-checklist`, `pr-review-rules`, `security-scan`) that standardize how the team deploys services, reviews pull requests, and scans branches for security issues before push. Use this repo as the single source of truth for shared Claude Code automation.

## Subscribe

Add this marketplace to your Claude Code instance:

```
/plugin marketplace add github:eresemai/invoice-maker-team-marketplace
```

To pin the marketplace at the project level (so every contributor in this repo gets it automatically), commit `.claude/settings.json` with:

```json
{
  "extraKnownMarketplaces": {
    "invoice-maker-team-marketplace": {
      "source": {
        "source": "github",
        "repo": "eresemai/invoice-maker-team-marketplace"
      }
    }
  }
}
```

## Install a plugin

```
/plugin install deploy-checklist@invoice-maker-team-marketplace
/plugin install pr-review-rules@invoice-maker-team-marketplace
/plugin install security-scan@invoice-maker-team-marketplace
```

## Update flow

- Maintainers update both manifest versions together and review the validation run before tagging a release.
- Consumers pull the latest with:

```
/plugin marketplace update invoice-maker-team-marketplace
```

## Contribute

1. Read [SECURITY.md](./SECURITY.md) before opening a PR — every plugin runs with full user privileges, review accordingly.
2. Add an entry to [CHANGELOG.md](./CHANGELOG.md) under the next version.
3. CI validates every plugin on every PR via `.github/workflows/validate-plugins.yml`.
4. Get the named maintainer-approver of the affected plugin to review.

## Provenance

Adapted from genkovich/agentic-engineering-course-public, modules/5-claude-code-extended/5.6-marketplace (MIT). CI validates manifests without model calls or API keys.
