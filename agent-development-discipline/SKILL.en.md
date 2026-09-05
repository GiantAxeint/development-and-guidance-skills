---
name: agent-development-discipline
description: Project discipline and multi-agent collaboration rules for AI/agent-driven development (a.k.a. A2D). Use when "building with AI/agents such as Claude Code, OpenCode, Codex", starting a project from scratch, setting up a dev environment, or splitting a large project across multiple agents — and when hitting version hallucination, environment inconsistency, unmaintained AI-written code, or messy multi-agent handoffs. Five laws: ①verify versions first ②know your environment ③one block = one atomic commit ④read through & comment ⑤split blocks & hand off via docs. 中文版: SKILL.zh-CN.md. Chinese triggers: AI 写代码、多 agent 协作开发、agent 驱动开发、用 Claude Code 写码.
---

# Agent-Development Discipline (A2D)

## Overview

When you write code with AI agents, the biggest cost is not "writing slowly" — it is **rework caused by broken environments, hallucinated versions, unreviewed code, and agents stepping on each other**. This discipline constrains AI-assisted coding into five laws, so that every development step stays rollback-able, reviewable, and handoff-able.

Use it for: personal website development, bootstrapping projects from scratch, adding features to existing codebases, and running medium-sized+ projects across multiple agents in parallel.

## The Five Laws

1. **Verify versions first.** Before installing or importing any dependency, read the official docs to confirm the version and API signature — then download. Never fill in versions from memory or let an agent guess.
2. **Know your environment.** Before writing any code, find out the actual OS, shell, path conventions, package manager, and start commands on this machine, and record them in the project-root `AGENTS.md` (template: `references/project-convention-template.en.md`).
3. **One block, one atomic commit.** Give agents a hard limit — solve exactly one technical block at a time; **commit to git immediately** when it is done, then move to the next block.
4. **Read through & comment.** After each block, the agent must re-read its own code and add rough comments (explaining the "why" over the "what") so a human can read and maintain it.
5. **Split blocks & hand off via docs.** For project-level tasks, a human first splits the requirement into technical blocks and assigns different blocks to different agents; when each agent finishes, it writes a handoff document for the next agent, then pushes to git to preserve the version.

## Workflow

```
Project-level requirement
   │
   ▼
[Stage A] Environment inventory & version pinning ──────┐
   │                                                    │
   ▼                                                    │
[Stage B] Split into blocks + assign agents             │ Small single-file
   │                                                    │ changes may enter
   ▼                                                    │ the block loop here
[Stage C] Block execution loop (inside each agent)       │
   │  ① solve only this block                          │
   │  ② read through + comment                         │
   │  ③ git commit (atomic)                            │
   │  ④ write handoff doc → pass to next agent         │
   ▼                                                    │
[Stage D] Integration verification & wrap-up           ◄┘
```

## Stage A: Environment inventory & version pinning

Before any install or coding, take an environment inventory:

1. **Probe the host environment** (measure with commands, never assume):
   - OS and version (Windows/Linux/macOS), CPU architecture
   - Current shell type (cmd / PowerShell / Git Bash)
   - Project path conventions (non-ASCII characters? spaces? drive letters?)
   - Package manager and its global install location (e.g. the real path of system npm)
   - Start/build commands (`npm run dev`, `python app.py`, …)
2. **Write all of the above into the project-root `AGENTS.md` / `CLAUDE.md`**, so every new session or agent loads it on startup and never repeats environment mistakes. Use `references/project-convention-template.en.md`.
3. **Pin versions.** Before installing any package, read that package's official docs (npm registry / PyPI / GitHub README) and confirm: the latest stable version, compatibility with your existing dependencies, and whether extra compilation steps are needed. **Never let an agent fill in a version from training memory** — version hallucination is the #1 rework source in AI coding. After installing, read back the actual installed version with `pip show` / `npm ls` to confirm what landed on disk.

## Stage B: Split into blocks & assign agents

Split a big project first, then assign people:

1. **Draw a dependency graph.** Break the requirement into mutually independent "technical blocks" (e.g. UI block / API block / database block / deploy block) and annotate the interfaces between blocks (function signatures, data structures, ports).
2. **Interfaces first.** Define the public interfaces and data flow of each block before agents start in parallel — without interfaces agreed first, parallel work always collides.
3. **One person per block.** Assign one agent per block; **only one agent may touch shared files at a time** (root configs, interface definition files); others work in their own directories.
4. **Task card.** Each agent's instructions must state: which block it owns, what it depends on, acceptance criteria, and that it must write a handoff document when done.

## Stage C: Block execution loop (mandatory inside every agent)

```
Solve this block's coding problem
   ↓
Re-read the code you produced; add rough comments (why it is done this way)
   ↓
git add + commit (each commit contains only this block; message states the block name)
   ↓
Write a handoff document (template: references/block-handoff-template.en.md)
   ↓
(multi-agent) pass the handoff doc to the next agent, then continue with your next block
```

Key points:

- **Solve one block at a time.** Even when an agent offers to "also fix X while we're here" — refuse. Keep commit granularity and code blame traceable.
- **Comment standard.** Comments explain the "why" (business reasons, pitfalls hit, trade-offs), not repeat the code itself; key functions must have a docstring.
- **Commit standard.** One block = one commit. Suggested message format: `<block name>: <what was done>`; push to the remote right after committing (when applicable) as a second safety net.

## Stage D: Integration verification & wrap-up

After all blocks are done:

1. Let an "integration agent" (or the lead agent) read through the whole codebase and verify that interfaces between blocks line up.
2. Run the full start/test flow and confirm the whole thing works.
3. Update `AGENTS.md` (new commands, new directory structure, newly recorded pitfalls).
4. Tag or merge to the main branch, then commit the whole project as wrap-up.

## Resources

- `references/project-convention-template.en.md` — project-root AGENTS.md/CLAUDE.md template (environment info table + discipline summary). Copy and fill it in when initializing any project.
- `references/block-handoff-template.en.md` — block handoff document template. Each agent fills it in after completing a block and passes it to the next agent.
