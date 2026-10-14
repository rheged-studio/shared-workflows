---
title: Re-vendor multi-team skills, set R and A issue keys, bump changelog-core
release_note: ""
created_at: "2026-10-13T14:00:00Z"
merged_at: "2026-10-13T13:32:04Z"
branch: a-2762-shared-workflows-re-vendor-the-multi-team-skills-and
pr: 130
commit: 644ad65
author: rob@rheged.studio
co_authors: []
category: chore
breaking: false
issues:
  - R-2762
  - R-2739
  - R-2684
affected_packages:
  - infrastructure
stats:
  files_changed: 81
  loc_added: 2444
  loc_removed: 870
  commits:
---

## Changed

**Re-vendor shared-workflows onto agent-skills v1.13.0 ([R-2762](https://linear.app/rheged-studio/issue/R-2762), part of [R-2684](https://linear.app/rheged-studio/issue/R-2684))**

- Roll `.claude/skills` and `.agents/skills` to the multi-team Linear skills: changelog 0.10.0, cleanup-repo 0.5.0, commit 0.3.0, Linear-sync 0.4.0, preflight 0.5.0, rheged-skills-setup 0.15.2, send-it 0.12.1, triage-pr 0.19.0
- Refresh `skills-lock.json` / `.claude/skills.lock` provenance to GitHub sources
- Bump the `@rheged-studio/changelog-core` devDependency and lockfile to `^1.2.0`

**Set R and A issue keys ([R-2739](https://linear.app/rheged-studio/issue/R-2739))**

- Set `issueKeys` to `["R", "A"]` in the changelog, cleanup-repo, Linear-sync and triage-pr configs on both mirrors; `linearTeamName` already read "Rheged Studio"
