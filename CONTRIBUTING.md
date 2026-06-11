# Contributing to spec-skill

Thank you for your interest! This project welcomes issues and pull requests.

## Before you start

- Open an **issue** first for significant changes (workflow changes, new gates, template changes). The discipline of this skill lives in its details, so a short discussion saves rework.
- For typos, doc fixes, and small clarifications, open a PR directly.

## What this project is

`spec-skill` is a **documentation-only** skill: the entire behavior lives in `skills/spec/SKILL.md`, a single prompt that Claude Code loads. There is no build step and no runtime code. Changes are edits to that prompt (or to the docs around it).

## Design intent — keep these invariant

When proposing changes to `SKILL.md`, preserve the core contract:

- **Investigate before asking.** The skill must never ask what it can find in the project or the conversation.
- **The self-check (Check A).** A spec is only done when a fresh session could build it from the spec alone. Don't weaken this.
- **Two-layer decision log (§12).** Owner decisions (D) are never re-asked; AI placeholders (T) stay visible and vetoable.
- **Anti-Potemkin completion.** Acceptance criteria must be executable; "file exists / imports OK" criteria are rejected by design.

A change that makes the skill ask *more* questions during implementation, or that lets a spec pass without executable acceptance criteria, is moving in the wrong direction.

## Testing a change

There is no automated test suite — the skill is a prompt. Validate changes empirically:

1. Install your edited `skills/spec/` into `~/.claude/skills/`.
2. Run `/spec <a realistic feature idea>` end-to-end in Claude Code.
3. Confirm Check A actually triggers (a fresh-context sub-agent, or the fallback audit table) and that the resulting spec has executable acceptance criteria.
4. Describe what you ran and what you observed in the PR.

## Pull request checklist

- [ ] No hard-coded personal paths (`/Users/...`) or machine identifiers in the diff.
- [ ] The core invariants above are preserved (or the PR explains why a change is intended).
- [ ] `CHANGELOG.md` updated under `[Unreleased]` for user-visible changes.
- [ ] You described the end-to-end run you used to validate the change.

## Licensing

By submitting a Contribution, you agree that it is licensed under the **Apache License 2.0**, the same license as the project. See `LICENSE`.
