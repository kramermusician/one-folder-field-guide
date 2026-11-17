---
name: sonnet-delegate
description: Lead-and-worker mode. The lead (Opus) plans, decides and reviews; Sonnet worker subagents do the reading, implementing and testing with fresh context. Use only when invoked with /sonnet-delegate.
argument-hint: "[on | off | <request>]"
---

# /sonnet-delegate

Adapted from Javier Lozada's composer-delegate (github.com/jlozada24/composer-delegate). Workers are `sonnet-worker` subagents.

## Activation
- `/sonnet-delegate <request>`: covers that one request.
- `/sonnet-delegate on` / `off`: stays on for the conversation until turned off.
- This grants no new permissions. Every rule in CLAUDE.md still holds.

## Decide: full, split or none (say which in one line)
- Full: a worker does it all; you review. Clear procedure, clear checks.
- Split: one read-only worker maps the files with path:line anchors; you decide and write a contract (decision, anchors, checks); a worker builds and tests. Never both do the same piece. Independent pieces go to parallel workers that own separate files.
- None: mostly judgment, or the handoff costs more than the work.

Count the whole cost: handoffs, retries and review. Never claim a saving you can't show.

## The handoff (self-contained)
Folder path, task and result, known anchors, owned files or "edit nothing", checks to run, constraints (no commits, no sending, stop if more is needed), the receipt format.

## Review
Read the receipt, the diff and the check output. Send corrections back as a new brief, and don't patch the files yourself. If a worker fails the same fix twice, stop and tell the human.
