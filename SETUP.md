# Setup & Verification

This fork is installed and verified on a local Claude Code environment.

## Install (Option 1 — plugin)

```
/plugin marketplace add 1mp3ctz/skill-codex
/plugin install skill-codex@skill-codex
/reload-plugins
```

## Environment

- Codex CLI: `codex-cli 0.141.0`
- Auth: ChatGPT login (no API key) — runs against the ChatGPT subscription
- Skill loaded as: `skill-codex:codex`

## Smoke test

Read-only call to confirm the Claude Code -> skill -> `codex exec` chain:

```
codex exec --skip-git-repo-check --sandbox read-only -m gpt-5.4-mini \
  --config model_reasoning_effort="low" \
  "Reply with one short sentence confirming you received this." </dev/null 2>/dev/null
```

Result: Codex responded successfully ("Received; I'm Codex, based on GPT-5"). Chain working end-to-end.

## Usage

Ask Claude to "have Codex review this" — it activates the `codex` skill, asks for
model + reasoning effort, runs read-only by default, and critically evaluates the output.
