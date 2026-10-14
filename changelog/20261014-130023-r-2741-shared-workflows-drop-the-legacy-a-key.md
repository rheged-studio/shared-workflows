---
title: Drop the legacy A key from the skill configs
release_note: ""
created_at: "2026-10-14T13:00:23Z"
merged_at: ""
branch: r-2741-shared-workflows-drop-the-legacy-a-key
pr: ""
commit: ""
author: rob@rheged.studio
co_authors: []
category: chore
breaking: false
issues:
  - R-2741
stats:
  files_changed: 0
  loc_added: 0
  loc_removed: 0
  commits: 0
version: ""
---

## Changed

**Remove the legacy A issue key ([R-2741](https://linear.app/rheged-studio/issue/R-2741))**

- Set `issueKeys` to ["R"] in every skill `config.json` copy, so the legacy `A` key is no
  longer accepted now that no `a-` branches or PRs remain open.
