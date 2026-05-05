# Pull Request

Read a GitHub pull request from the provided argument.

## Input

- Full URL, such as `https://github.com/owner/repo/pull/123`
- PR number, such as `42` or `#42`
- If no input is provided, ask the user for a PR number or URL.

## Steps

1. Parse the input.
2. If it is a full URL, extract `owner`, `repo`, and `number`, then run:
   `gh pr view <number> --repo <owner>/<repo> --json number,title,body,state,labels,assignees,reviewers,commits,files,comments`
3. If it is a number, run in the current repo:
   `gh pr view <number> --json number,title,body,state,labels,assignees,reviewers,commits,files,comments`
4. Show the PR:

```markdown
## PR #<number>: <title>
**State:** <open/merged/closed>
**Labels:** <labels>
**Assignees:** <assignees>
**Reviewers:** <reviewers>

### Description
<body>

### Files Changed (<n> files)
- path/to/file.ext

### Commits (<n> commits)
- <sha> <message>

### Comments
<summary of important comments, if any>
```

5. Ask what to do next:

> Enter a file path to view its diff, enter `context` to use this PR as implementation context, or enter `cancel`.

For a file diff, run:
`gh pr diff <number> -- <file>`

