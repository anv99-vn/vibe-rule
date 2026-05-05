# Codex Kit

This folder ports the repo's `.claude` workflow into Codex-friendly prompts.

- `../AGENTS.md` contains persistent project instructions Codex will read.
- `commands/` contains reusable task prompts based on the original Claude command files.
- Claude's `PreToolUse` file guard hook cannot be installed as a repo-local Codex hook, so the `.vibe-allowed` rule is documented in `AGENTS.md` instead.

The original `.claude` directory is left unchanged.

