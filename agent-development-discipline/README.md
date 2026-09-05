<div align="right">

**[English](README.md)** | [中文](README.zh-CN.md)

</div>

# Agent-Development Discipline (A2D)

> Rules that keep AI/agent-driven coding rollback-able, reviewable, and handoff-able.
> 中文版见 [README.zh-CN.md](./README.zh-CN.md) ｜ Skill files: [SKILL.en.md](./SKILL.en.md) / [SKILL.zh-CN.md](./SKILL.zh-CN.md)

**A2D** is a coding discipline for anyone who writes software *with* AI agents (Claude Code, OpenCode, Codex, WorkBuddy, …). It exists because the real cost of AI-assisted development is rework from broken environments, hallucinated versions, unreviewed code, and agents stepping on each other.

## When to use it

- Bootstrapping a project from scratch with an agent
- Adding features to an existing codebase via AI
- Splitting a medium/large project across multiple agents in parallel
- Symptoms you recognize: "the version it installed doesn't exist", "it works on their machine but not mine", "nobody understands the AI-written code", "two agents overwrote each other"

## The five laws at a glance

1. **Verify versions first** — read official docs before installing anything; never guess versions from memory.
2. **Know your environment** — probe the real OS/shell/paths/commands and record them in a project-root `AGENTS.md`.
3. **One block, one atomic commit** — one technical block per agent step, committed to git immediately.
4. **Read through & comment** — agents re-read their own code and comment the "why", so humans can maintain it.
5. **Split blocks & hand off via docs** — a human splits the project, agents write handoff docs between blocks.

## Files

| File | Purpose |
|---|---|
| `SKILL.en.md` / `SKILL.zh-CN.md` | The full discipline (bilingual). Read the one you are comfortable with. |
| `references/project-convention-template.en.md` / `.zh-CN.md` | Template for the project-root `AGENTS.md`/`CLAUDE.md`. Copy & fill in per project. |
| `references/block-handoff-template.en.md` / `.zh-CN.md` | Handoff-doc template used between agents/blocks. |

## How to adopt it

- **Quickest**: read `SKILL.zh-CN.md` (or `.en.md`) once, and enforce the five laws in your next agent session.
- **Per project**: copy `references/project-convention-template.*` into the project root as `AGENTS.md` (Claude Code / OpenCode / Codex read this automatically) or `CLAUDE.md`, and fill in the real environment values.
- **As an installable skill**: place the directory into your agent's skill folder (e.g. WorkBuddy `~/.workbuddy/skills/agent-development-discipline/` with `SKILL.md` = your preferred language copy), then it activates automatically on matching requests.

Part of [Development and Guidance Skills](https://github.com/GiantAxeint/development-and-guidance-skills). MIT licensed.
