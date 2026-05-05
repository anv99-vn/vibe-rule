# Issue

Read a GitHub issue from the provided argument.

## Input

- Full URL, such as `https://github.com/owner/repo/issues/123`
- Issue number, such as `42` or `#42`
- If no input is provided, ask the user for an issue number or URL.

## Steps

1. Parse the input.
2. If it is a full URL, extract `owner`, `repo`, and `number`, then run:
   `gh issue view <number> --repo <owner>/<repo> --json title,body,labels,comments`
3. If it is a number, run in the current repo:
   `gh issue view <number> --json title,body,labels,comments`
4. Show the issue in this format:

```markdown
## Issue #<number>: <title>
**Labels:** <labels>

<body>

---
**Comments** (<n> comments):
<summary of important comments, if any>
```

5. Ask whether to use the issue as the implementation spec:

> Do you want to start implementing this issue? (y/n)

If yes, continue from Step 2 of the Vibe Coding Workflow in `AGENTS.md`, using the issue content as the gathered requirement.

