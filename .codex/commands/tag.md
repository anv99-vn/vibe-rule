# Tag

Create an annotated git tag and push it to `origin`.

## Input

- Optional version, such as `v1.0.1` or `1.0.1`
- If no version is provided, compute the next patch version.

## Steps

1. Normalize the version. Add a leading `v` if needed.
2. If no version is provided, find the latest tag:
   `git tag --sort=-version:refname`
3. Use `v1.0.0` if no tags exist.
4. Otherwise parse `vMAJOR.MINOR.PATCH` and increment `PATCH`.
5. Create the annotated tag:
   `git tag -a <version> -m "Release <version>"`
6. Push it:
   `git push origin <version>`
7. Report:

```text
Created and pushed tag <version> to origin.
```

If the tag exists, `origin` is missing, or push fails, report the exact failure and stop.

