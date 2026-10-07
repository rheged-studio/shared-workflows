---
title: Pin load-repo-config action at v1.8.0 so bot outputs resolve
release_note: reusable-load-repo-config now actually emits the optional `app_client_id`, `bot_name`, and `bot_email` outputs added in v1.8.0 — they were always empty because the workflow still pinned the pre-A-1927 action.
created_at: "2026-10-07T09:03:17Z"
merged_at:
branch: a-2344-bump-load-repo-config-action-pin
pr:
commit:
author: rob@rheged.studio
co_authors: []
category: fix
breaking: false
issues:
  - A-2344
stats:
  files_changed:
  loc_added:
  loc_removed:
  commits:
---

## Fixed

- `reusable-load-repo-config.yml` declared the [A-1927](https://linear.app/rheged-studio/issue/A-1927) `app_client_id` /
  `bot_name` / `bot_email` outputs, but still pinned the `load-repo-config`
  action at `v1.5.1`, which predates the `githubAppClientId` / `botName` /
  `botEmail` keys. Every caller therefore received empty values. Wiring them
  into `reusable-changelog-enrich` (the [A-1945](https://linear.app/rheged-studio/issue/A-1945) rollout) would have passed an
  explicit empty `bot-name` and broken the changelog write-back.
- The action is now pinned at `v1.8.0`, so the optional keys are read from the
  caller's `infrastructure/repo-config.yaml`. Repos that don't set the keys are
  unaffected — the outputs stay empty, exactly as before.
