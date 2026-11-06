---
description: Explain a file in simple Hebrew with everyday examples, focusing on one topic. Read-only.
argument-hint: <file> <focus>
arguments: [file, focus]
allowed-tools: Bash(git log --oneline -5 -- *), Read, Grep, Glob
disallowed-tools: Edit, Write
---

## Last 5 changes to the file

!`git log --oneline -5 -- "$file"`

## Task

Read `$file` (and `CLAUDE.md` at the project root, if it exists, for project context) and explain it to me in simple Hebrew, with emphasis on: $focus.

If no focus is given, explain the file in general.

Always answer in Hebrew, whatever language this prompt or the code is in.

- Idea first, code after.
- Give a simple everyday example (kitchen, shopping, traffic, games, and the like).
- Use tables instead of long paragraphs.
- Write technical terms in English, with the Hebrew translation next to them.
- Explain only: do not change, create or delete any file.
