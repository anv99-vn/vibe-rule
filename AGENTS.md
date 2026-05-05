# Codex Project Kit

These instructions adapt the existing Claude workflow in this repo for Codex.

## Vibe Coding Workflow

For feature implementation, bug fixes, or new code, follow this sequence unless the user explicitly asks for a faster path.

### 1. Gather Requirements

Ask whether there is a GitHub issue to use as the spec:

> Do you have a GitHub issue link or issue number? You can also describe the request directly.

If an issue is provided:

- For a full URL, extract owner, repo, and number, then run:
  `gh issue view <number> --repo <owner>/<repo> --json title,body,labels,comments`
- For an issue number, run:
  `gh issue view <number> --json title,body,labels,comments`
- Show the issue title and contents to the user.
- Ask only for missing details, such as unclear behavior, technical constraints, or edge cases.

If no issue is provided, clarify:

- Specific goal.
- Expected inputs and outputs.
- Technical constraints such as language, framework, or libraries.
- Edge cases or special conditions.

Proceed when there is enough information to act.

### 2. Determine Context To Read

Ask how the user wants to provide codebase context:

> To understand the codebase, I can read the whole project, read specific files or folders you name, or avoid reading extra files. Which do you prefer?

- If reading the whole project, inspect the tree first, then read relevant files in groups.
- If reading specific paths, read only those paths unless more context is clearly needed.
- If reading no extra files, continue with the information already available.

After reading, briefly summarize what was learned.

### 3. Summarize And Confirm

Summarize the understood request in clear bullets and ask:

> Do you confirm I can continue?

Continue after the user confirms.

### 4. Plan The File Changes

List every file expected to be created or changed:

```text
path/to/file.ext [CREATE / MODIFY]
  Purpose: ...
```

Ask:

> Do you agree with this structure?

Begin editing after confirmation.

### 5. Implement

Implement according to the confirmed file plan. Do not add files or widen scope without telling the user.

### 6. Self-Check And Report

Before final response, verify:

- Every file in the confirmed plan was handled.
- No files outside the confirmed scope were changed without explanation.
- Requested edge cases were addressed.
- Tests or checks were run where practical.

Report briefly:

```text
Done: ...
Note: ... (only if there are deviations, unhandled edge cases, or skipped checks)
```

## File Reading Limit

If the project contains `.vibe-allowed`, only read files and folders listed there. If a needed file is outside that list, ask the user first.

## Token Discipline

Prefer concise solutions and avoid reading unnecessary files. Read files only when they are relevant to the current task.

