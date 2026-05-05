# Issues

List GitHub issues for a repo.

## Input

- Optional repo argument: `owner/repo`
- If no input is provided, use the current repo.

## Steps

1. If a repo is provided, run:
   `gh issue list --repo <owner>/<repo> --limit 100 --json number,title,labels,state,createdAt,assignees`
2. Otherwise run:
   `gh issue list --limit 100 --json number,title,labels,state,createdAt,assignees`
3. Display a table:

```markdown
## Issues (<n> issues)

| # | Title | Labels | Assignees |
|---|-------|--------|-----------|
| #1 | ... | bug, ui | @alice |
```

4. Ask what to do next:

> Enter an issue number to read it, enter `implement <number>` to use it as a spec, or enter `cancel`.

For `implement <number>`, fetch the issue and continue from Step 2 of the Vibe Coding Workflow in `AGENTS.md`.

