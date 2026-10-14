---
title: Sweep Linear issue references to R and C keys
release_note: ""
created_at: "2026-10-13T20:37:32Z"
merged_at: "2026-10-14T08:07:08Z"
branch: r-2740-shared-workflows-sweep-issue-references
pr: 133
commit: "1975846"
author: rob@rheged.studio
co_authors: []
category: chore
breaking: false
issues:
  - R-2740
affected_packages: []
stats:
  files_changed: 98
  loc_added: 603
  loc_removed: 574
  commits:
---

## Changed

**Sweep issue references ([R-2740](https://linear.app/rheged-studio/issue/R-2740))**

- Rewrite old `A-n` Linear issue references through the committed Linear-migrate mapping
- 97 files and 634 references changed, with no flags and no unmapped IDs
- Changelog file names and `branch:` lines are kept verbatim
