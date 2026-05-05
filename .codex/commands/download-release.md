# Download Release

Download assets from a GitHub release in the current repo.

## Input

- Optional version, such as `v1.0.1` or `1.0.1`
- If no version is provided, use the latest release.

## Steps

1. Normalize the version. Add a leading `v` if a version is provided without one.
2. Fetch release data:
   - With a version: `gh release view <version> --json tagName,assets`
   - Without a version: `gh release view --json tagName,assets`
3. If no release exists, report the error and stop.
4. Show assets:

```markdown
## Release <tagName>
Assets:
  1. <file name> (<size>)
  2. <file name> (<size>)
```

5. Ask:

> Which file do you want to download? Enter a number, `all`, or `cancel`.

6. Download:
   - Specific asset: `gh release download <tagName> --pattern <file name>`
   - All assets: `gh release download <tagName>`
7. Report:

```text
Downloaded: <file names> from release <tagName>
Saved to: <current directory>
```

