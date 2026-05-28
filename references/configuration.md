---
title: Configuration
---

# Configuration

extractor reads defaults from `skills/extractor/.env`. Falls back to `.env.example` if `.env` is missing.

## Environment variables

| Variable | Default | Values | Purpose |
|----------|---------|--------|---------|
| `GG_EXTRACTOR_GITHUB_OWNER` | `gg-skills` | any GitHub user or org | Owner under which new repos are created |
| `GG_EXTRACTOR_DEFAULT_VISIBILITY` | `private` | `private`, `public` | Default repo visibility |
| `GG_EXTRACTOR_DEFAULT_INTEGRATION` | `gitignore` | `gitignore`, `submodule` | Default re-integration mode |

## Behavior rules

- These are **defaults only**. Always prompt the user to confirm or override at each decision point.
- Never silently apply `.env` values.
- The skill does not fail if `.env` is missing; it simply has no defaults to offer.
