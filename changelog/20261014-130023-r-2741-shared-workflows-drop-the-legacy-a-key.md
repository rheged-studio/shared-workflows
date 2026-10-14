---
title: Drop the legacy A key from the skill configs
release_note: ""
created_at: "2026-10-14T13:00:23Z"
merged_at: "2026-10-14T13:05:49Z"
branch: r-2741-shared-workflows-drop-the-legacy-a-key
pr: 135
commit: 5487dc7
author: rob@rheged.studio
co_authors: []
category: chore
breaking: false
issues:
  - R-2741
stats:
  files_changed: 9
  loc_added: 36
  loc_removed: 8
  commits: 0
version: ""
---

## Changed

**Remove the legacy A issue key ([R-2741](https://linear.app/rheged-studio/issue/R-2741))**

- Set `issueKeys` to ["R"] in every skill `config.json` copy, so the legacy `A` key is no
  longer accepted now that no `a-` branches or PRs remain open.
