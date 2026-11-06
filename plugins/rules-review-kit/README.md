# rules-review-kit

Review a change against a project's own rules, plus a Hebrew code explainer.

## Components

| Type | Name | What it does |
|------|------|--------------|
| Agent | `rules-reviewer` | Read-only review of a change against `CLAUDE.md`, `.claude/rules/` and architecture docs. With no rules found it says so and reports only objective errors (secrets, obvious bugs) as general notes. |
| Skill | `review-change` | `/rules-review-kit:review-change <files>` feeds the `git diff` of the files to the agent. |
| Command | `explain-he` | `/rules-review-kit:explain-he <file> <focus>` explains a file in simple Hebrew with everyday examples. Never edits files. |

## Install

```
/plugin marketplace add ita315/rules-review-kit
/plugin install rules-review-kit@ita-plugins
```

## Usage

```
/rules-review-kit:review-change src/app.ts src/utils.ts
/rules-review-kit:explain-he src/app.ts "how the state works"
```

## Requirements

- `review-change` needs a git repository.
- `review-change` needs at least one commit, and new untracked files are not in the diff (`git add` them first).
- File paths without spaces.

## Notes

- The agent replies in the language of the user; `explain-he` always replies in Hebrew.
- Tip: the review is most useful when the project has rules in `.claude/rules/` or `CLAUDE.md`.
