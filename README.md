# Development and Guidance Skills

> Two battle-tested disciplines for working with AI — one for **writing code** with agents, one for **giving advice & troubleshooting** honestly.
> 中文版见 [README.zh-CN.md](./README.zh-CN.md)

This repository collects two disciplines that were forged in real projects — not theory. Each one exists because a specific failure mode cost real time and rework, and each was refined line-by-line by its author through daily use with Claude Code, OpenCode, and other agent harnesses.

| | [Agent-Development Discipline (A2D)](./agent-development-discipline/) | [Recommend Guiding Discipline (RGD)](./recommend-guiding-discipline/) |
|---|---|---|
| **Governs** | Writing code *with* AI agents | AI giving advice / troubleshooting |
| **The problem** | Broken environments, hallucinated versions, unreviewed code, agents stepping on each other | Confident wrong answers — describing a website from memory, inferring environment facts from a domain name, dumping a long chain of steps |
| **The fix** | Five laws: ①verify versions first ②know your environment ③one block = one atomic commit ④read through & comment ⑤split blocks & hand off via docs | Six laws: ①browse before advising ②ask environment facts first (time-boxed self-check) ③align on the entry point ④dare to correct ⑤numbered incremental steps ⑥raw error text first |
| **You use it when** | Building a site / project with agents, multi-agent collaboration | Any reply touching websites, user environment, versions, or bug-fixing |

Both disciplines ship **bilingual** (English / 简体中文): every skill has `SKILL.en.md` + `SKILL.zh-CN.md`, every README has `.md` + `.zh-CN.md`, and every reference template comes in both languages.

## Repository layout

```
development-and-guidance-skills/
├── README.md  README.zh-CN.md   project overview (EN / 中文)
├── LICENSE                       MIT
├── agent-development-discipline/  A2D — coding discipline (five laws)
│   ├── SKILL.en.md  SKILL.zh-CN.md
│   ├── README.md  README.zh-CN.md
│   └── references/
│       ├── project-convention-template.en.md / .zh-CN.md   AGENTS.md template
│       └── block-handoff-template.en.md / .zh-CN.md        handoff-doc template
└── recommend-guiding-discipline/  RGD — advice & troubleshooting (six laws)
    ├── SKILL.en.md  SKILL.zh-CN.md
    ├── README.md  README.zh-CN.md
    └── references/
        └── case-history.en.md / .zh-CN.md   anonymized real incident that motivated RGD
```

## Quick start

1. **A2D — writing code with agents**: read [`agent-development-discipline/SKILL.zh-CN.md`](./agent-development-discipline/SKILL.zh-CN.md) (or `.en.md`), and for each new project copy [`project-convention-template`](./agent-development-discipline/references/) into the project root as `AGENTS.md` / `CLAUDE.md`.
2. **RGD — advice & troubleshooting**: read [`recommend-guiding-discipline/SKILL.zh-CN.md`](./recommend-guiding-discipline/SKILL.zh-CN.md) (or `.en.md`) once — then verify, ask, and be honest. Read the [`case-history`](./recommend-guiding-discipline/references/) to see why each law exists.

### Install as agent skills (optional)

Copy either directory into your agent's skill folder so it activates automatically on matching requests. Example for WorkBuddy:

```bash
# A2D (pick your language file as SKILL.md)
cp -r agent-development-discipline ~/.workbuddy/skills/agent-development-discipline
cp agent-development-discipline/SKILL.zh-CN.md ~/.workbuddy/skills/agent-development-discipline/SKILL.md
```

Other harnesses (Claude Code / OpenCode / Codex) pick up the templates as project-root `AGENTS.md` / `CLAUDE.md` automatically — no skill system needed.

## License

[MIT](./LICENSE) © 2026 Erius (GiantAxeint). Free to use, adapt, and redistribute — the disciplines are meant to spread.

*Built on Windows, verified daily in real agent sessions. Issues & PRs welcome.*
