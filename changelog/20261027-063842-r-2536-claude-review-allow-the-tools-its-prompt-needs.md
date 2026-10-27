---
title: Report the tools a Claude review run was refused
release_note: Claude Code Review now names the tools it was refused, with a count each, as a warning on the run, so a green review that quietly lost tool calls is visible and the allow-list can be widened from real data.
created_at: "2026-10-27T06:38:42Z"
merged_at: ""
branch: r-2536-claude-review-allow-the-tools-its-prompt-needs
pr:
commit: ""
author: rob@rheged.studio
co_authors: []
category: feature
breaking: false
issues:
  - R-2536
stats:
  files_changed:
  loc_added:
  loc_removed:
  commits:
version: ""
---

## Added

**Report refused tool calls ([R-2536](https://linear.app/rheged-studio/issue/R-2536))**

- A step in `reusable-claude-code-review.yml` and this repo's inline
  `claude-code-review.yml` that reads `permission_denials` from the execution
  log and prints each refused tool with a count, plus a `::warning::`
  annotation. A refused call leaves the run green, and the action prints only
  `permission_denials_count`, so until now there was no way to tell which
  tools to allow.
- For Bash it prints only the command's first words (three for `gh`, two
  otherwise), drops leading `VAR=value` assignments and masks any other value,
  so no full command line, prompt or diff reaches the log. It runs on success
  and failure, and never fails the job.
