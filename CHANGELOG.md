# Changelog

All notable changes to this project are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-06-11

### Added

- Initial public release of the `spec` skill for Claude Code.
- Front-loaded requirements loop: investigate → ask up front → write the spec → build straight through.
- Interview questions are asked through the **AskUserQuestion** tool (structured dialog); free-text answers remain available via the auto-provided input field, and questions ride notification / remote-response setups so they reach you while away from the terminal.
- Step 1 self-research explicitly covers **external facts** — whether a library has a feature, API limits/pricing, SDK/platform specifics, version differences — via WebSearch / WebFetch (and an official-docs MCP if available). Principle: research the facts, ask only the decisions; sourced facts are recorded in §9/§10 of the spec.
- **Check A** (a fresh-agent self-check — could it build the spec as-is?) with a fresh-context sub-agent, and a 12-point self-audit fallback for environments without sub-agents.
- **Gate B** (full-text presentation and approval), flowing straight into autonomous implementation on "approve & start".
- Fixed 13-section spec template, including a two-layer decision log (owner decisions `D` vs. AI placeholders `T`) and an implementation-log section for execution evidence.
- Anti-Potemkin completion rule: acceptance criteria must be executable; "stub-passable" criteria are rejected.
- Configurable output language for generated specs and questions (`auto` / `ja` / `en`) via `skills/spec/config.yml`, resolved in step 0 of the skill.
- Lightweight path for requirements already settled in conversation.
- Revision / resume handling across `draft → approved → implementing → done` states.

[Unreleased]: https://github.com/dualform-labs/spec-skill/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/dualform-labs/spec-skill/releases/tag/v1.0.0
