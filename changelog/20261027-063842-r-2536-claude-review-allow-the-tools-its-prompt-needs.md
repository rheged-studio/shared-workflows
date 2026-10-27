---
title: Allow the Claude review the tools it uses, and report any it is refused
release_note: Claude Code Review may now run the read-only git and gh commands its prompt asks for, and names any tool it is still refused as a warning on the run, so a green review that quietly lost tool calls is visible.
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

## Fixed

**Allow the read-only tools the review uses ([R-2536](https://linear.app/rheged-studio/issue/R-2536))**

- Add `gh pr list`, `gh issue view`, `gh issue list`, `gh search`,
  `git status`, `git diff`, `git log`, `git show` and `git blame` to the
  review's `--allowedTools`, in the reusable workflow and the inline copy.
  `claude-code-action`'s prompt tells Claude to run `git status` and
  `git diff origin/<base>...HEAD`, and the code-review plugin's command
  declares the `gh` ones, but none were allowed: recent cadogan runs refused 0
  to 11 calls each, and a tempest run refused 19 and posted no review.
