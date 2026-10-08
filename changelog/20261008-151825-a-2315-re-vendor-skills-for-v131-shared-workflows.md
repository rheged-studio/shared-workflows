---
title: Re-vendor agent skills for mattpocock/skills 1.3.1
release_note: ""
created_at: "2026-10-08T15:18:25Z"
merged_at:
branch: a-2315-re-vendor-skills-for-v131-shared-workflows
pr:
commit:
author: rob@rheged.studio
co_authors: []
category: chore
breaking: false
issues:
  - A-2315
  - A-2299
affected_packages:
  - infrastructure
stats:
  files_changed:
  loc_added:
  loc_removed:
  commits:
---

## Changed

**Re-vendor shared-workflows onto the estate skill catalogue ([A-2315](https://linear.app/rheged-studio/issue/A-2315), parent [A-2299](https://linear.app/rheged-studio/issue/A-2299))**

- Roll `.claude/skills` and `.agents/skills` via `fleet-update.mjs --apply` (Rheged ship set plus Matt Pocock 1.3.1 packs)
- Add `implement-spec`, `retro`, and Rheged `pr`; drop upstream-removed `resolving-merge-conflicts`
- Restore per-skill `config.json` from trunk ([A-706](https://linear.app/rheged-studio/issue/A-706)); set triage-pr `humanEnvelope` false and `followUpLabel` `follow-up` on both mirrors
- Refresh `skills-lock.json` / `.claude/skills.lock` provenance to GitHub sources
