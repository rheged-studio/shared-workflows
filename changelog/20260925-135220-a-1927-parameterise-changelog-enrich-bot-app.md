---
title: Parameterise changelog-enrich bot/App identity
release_note: reusable-changelog-enrich accepts configurable GitHub App credentials and git author identity (road-runner defaults unchanged); load-repo-config exposes optional bot/App keys for caller wiring.
created_at: "2026-09-25T13:52:20Z"
merged_at: "2026-09-25T14:08:01Z"
branch: a-1927-parameterise-reusable-changelog-enrich-botapp-via-repo
pr: 121
commit: f5e33cb
author: rob.studio
co_authors: []
category: feature
breaking: false
issues:
  - A-1927
stats:
  files_changed: 8
  loc_added: 223
  loc_removed: 80
  commits:
---

## Changed

**Parameterise `reusable-changelog-enrich` bot/App identity ([A-1927](https://linear.app/rheged-studio/issue/A-1927))**

- Add optional `app-client-id`, `app-id`, `bot-name`, and `bot-email` inputs plus `APP_PRIVATE_KEY` secret (road-runner defaults preserve Rheged callers on `secrets: inherit`)
- Extend `load-repo-config` with optional `githubAppClientId`, `botName`, and `botEmail` outputs
- Document multi-tenant enrich prerequisites in README and CLAUDE.md
