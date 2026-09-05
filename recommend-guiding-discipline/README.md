# Recommend Guiding Discipline (RGD)

> A verification-first workflow for AI when giving advice or troubleshooting.
> 中文版见 [README.zh-CN.md](./README.zh-CN.md) ｜ Skill files: [SKILL.en.md](./SKILL.en.md) / [SKILL.zh-CN.md](./SKILL.zh-CN.md)

**RGD** keeps AI assistants honest whenever they give advice or help troubleshoot. It was drafted by its author, line by line, after a real incident where an AI confidently gave wrong troubleshooting steps for the wrong service provider — costing the user several rounds of confusion. The lesson: **trust is built on every recommendation being verifiable.**

## When to use it

Any reply that involves:

- The current state of external websites / services / docs
- Facts about the user's environment (domains, systems, accounts, paths, configs)
- Software versions and APIs
- Bug-fixing, or any step-by-step operational guidance

## The six laws at a glance

1. **Websites involved: browse first, then advise** — never describe a site from memory.
2. **Environment facts: ask first; if unanswerable, check yourself with a time box** — never infer from a name or TLD.
3. **Align on the entry point before troubleshooting** — one step per user report, no dumping a long chain.
4. **Users are not omniscient: supplement and correct** — point out contradictions directly, with evidence.
5. **Verification & steps: actual-verification methods, numbered, incremental** — no "trust me" checks.
6. **Raw error text first; on conflict, ask "did anything change midway?"** — never invent the error, never flatly reject either side.

## Files

| File | Purpose |
|---|---|
| `SKILL.en.md` / `SKILL.zh-CN.md` | The full discipline (bilingual). |
| `references/case-history.en.md` / `.zh-CN.md` | Anonymized retrospective of the real incident that motivated this discipline — read it to understand *why* each law exists. |

## How to adopt it

- **As a mental rule**: read `SKILL.zh-CN.md` (or `.en.md`) once. The six laws are easy to internalize — they mainly say *verify, ask, be honest*.
- **As an installable skill**: place the directory into your agent's skill folder (e.g. WorkBuddy `~/.workbuddy/skills/recommend-guiding-discipline/` with `SKILL.md` = your preferred language copy). It then activates automatically for advice/troubleshooting requests.
- **Pair it with A2D**: RGD governs *advising & troubleshooting*; [Agent-Development Discipline (A2D)](../agent-development-discipline/) governs *writing code with agents*. Together they cover the two places AI commonly goes wrong.

Part of [Development and Guidance Skills](https://github.com/GiantAxeint/development-and-guidance-skills). MIT licensed.
