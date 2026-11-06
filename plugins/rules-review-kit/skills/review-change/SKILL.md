---
name: review-change
description: Reviews a change in specific files against the project's own rules (CLAUDE.md, .claude/rules/, architecture docs) and returns CLEAN or a list of violations. Use before merging a change.
argument-hint: <files>
context: fork
agent: rules-review-kit:rules-reviewer
disable-model-invocation: true
allowed-tools: Bash(git diff *)
---

## The change

Files to review: $ARGUMENTS

!`git diff HEAD -- $ARGUMENTS`

## Review procedure

1. Check the changed lines in the diff above against the project's rules: `CLAUDE.md`, everything in `.claude/rules/`, and any architecture docs you find.
2. Read the full files only to understand context.
3. Anything a project document already rejected with a reason is not a violation.
4. If the diff is empty, say so and review the full files instead.
5. If the project has no rules at all, say so clearly and report only objective errors (secrets in code, obvious bugs), labeled as general notes, with no style opinions.

Reply in the language of the user's request; if there is no clear language signal, reply in English.

## Output

At most 10 lines:

- No violations: `CLEAN`
- Violations, one line each: `file:line | rule | suggested fix`
