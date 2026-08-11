---
title: Bump shared @acme-skunkworks packages and fix markdownlint 3.x fallout
release_note: Raise changelog-core, commitlint-config, and markdownlint-config to their published latest floors, and adapt local markdownlint ignores and first-party docs so the stricter 3.x ruleset stays green.
created_at: "2026-08-07T15:11:57Z"
merged_at: "2026-08-11T13:06:54Z"
branch: a-1346-shared-workflows-bump-acme-skunkworks-and-fix-lint-fallout
pr: 106
commit: ad1bcd6
author: rob@acmeskunkworks.io
co_authors: []
category: fix
breaking: false
issues:
  - A-1346
stats:
  files_changed: 8
  loc_added: 69
  loc_removed: 27
  commits:
version:
---

## Fixed

**Bump shared @acme-skunkworks packages and clear markdownlint 3.x fallout ([A-1346](https://linear.app/rheged-studio/issue/A-1346))**

- Bump `@acme-skunkworks/changelog-core` to `^1.1.1`, `commitlint-config` to `^1.0.1`, and `markdownlint-config` to `^3.0.0`.
- Ignore vendored `.claude/skills/**` / `.agents/skills/**` and fan-out `AGENTS.md` in markdownlint config and `lint:md` globs so skill bundles stay byte-identical to upstream.
- Tag ASCII diagram fences as `text` (MD040) and reword identifier-heavy changelog lines that tripped MD044.
