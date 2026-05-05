# Pull Requests

List GitHub pull requests for a repo.

## Input

- Optional repo argument: `owner/repo`
- Optional state: `open`, `closed`, `merged`, or `all`
- If no input is provided, use open PRs in the current repo.

## Steps

1. If a repo is provided, run:
   `gh pr list --repo <owner>/<repo> --limit 100 --json number,title,state,labels,assignees,reviewDecision,createdAt`
2. If a state is provided, add `--state <state>`.
3. Otherwise run:
   `gh pr list --limit 100 --json number,title,state,labels,assignees,reviewDecision,createdAt`
4. Display a table:

```markdown
## Pull Requests (<n> PRs)

| # | Title | State | Review | Assignees |
|---|-------|-------|--------|-----------|
| #1 | ... | open | approved | @alice |
```

5. Ask what to do next:

> Enter a PR number to read it, or enter `cancel`.

For a PR number, fetch and display it using the `pr.md` workflow.

