---
title: Remove the Dependabot configuration
release_note: ""
created_at: "2026-11-18T11:23:59Z"
merged_at: "2026-11-18T11:52:57Z"
branch: disable-dependabot
pr: 141
commit: 46307b5
author: rob@rheged.studio
co_authors: []
category: chore
breaking: false
issues: []
stats:
  files_changed: 11
  loc_added: 61
  loc_removed: 85
  commits:
version: ""
---

## Changed

- Removed `.github/dependabot.yml`: Dependabot is switched off across the estate, so this repo
  no longer receives automated GitHub Actions or npm bump PRs.
- Dropped the stale Dependabot references from `CLAUDE.md`, `README.md`, `SECURITY.md`, the
  composite-actions README and the reusable workflow header comments. The README no longer tells
  consumers to add a `.github/dependabot.yml`.
- Marked the Dependabot section of the shared-CI security review as superseded.
