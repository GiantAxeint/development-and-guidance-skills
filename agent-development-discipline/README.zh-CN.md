# Agent 开发纪律（Agent-Development Discipline, A2D）

> 让"用 AI/agent 写代码"可回滚、可复核、可交接的纪律。
> English: [README.md](./README.md) ｜ 技能正文：[SKILL.zh-CN.md](./SKILL.zh-CN.md) / [SKILL.en.md](./SKILL.en.md)

**A2D** 是给所有"用 AI agent 写代码"的人（Claude Code、OpenCode、Codex、WorkBuddy…）的一份编码纪律。它存在的理由：AI 辅助开发的真实成本不是"写得慢"，而是**环境错乱、版本幻觉、代码无人复核、多 agent 互相踩脚**带来的返工。

## 适用时机

- 用 agent 从零搭建项目
- 给已有代码库加功能
- 把中型以上项目拆给多个 agent 并行
- 你遇到过这些症状："它装的版本根本不存在"、"他机器上能跑我这儿不行"、"AI 写的代码没人看得懂"、"两个 agent 互相覆盖"

## 五条铁律速览

1. **版本先行**——装任何依赖前先读官方文档；禁止凭记忆填版本号。
2. **环境感知**——实测本机 OS/shell/路径/命令，写进项目根 `AGENTS.md`。
3. **单区块原子提交**——一次只解一个技术区块，解决完立即 git 提交。
4. **通读 + 注释**——agent 重读自己代码并注释"为什么"，保证人能维护。
5. **分块 + 文档交接**——人来拆块，agent 之间靠交接文档同步进度。

## 文件清单

| 文件 | 用途 |
|---|---|
| `SKILL.zh-CN.md` / `SKILL.en.md` | 完整纪律正文（双语），读你习惯的语言即可 |
| `references/project-convention-template.zh-CN.md` / `.en.md` | 项目根 `AGENTS.md`/`CLAUDE.md` 模板，每个项目复制填写 |
| `references/block-handoff-template.zh-CN.md` / `.en.md` | agent/区块之间的交接文档模板 |

## 怎么用起来

- **最快**：通读一遍 `SKILL.zh-CN.md`，下一次 agent 会话就按五律执行。
- **按项目落地**：把 `references/project-convention-template.*` 复制为项目根 `AGENTS.md`（Claude Code / OpenCode / Codex 会自动读取）或 `CLAUDE.md`，填真实环境值。
- **作为可安装技能**：把本目录放进你 agent 的技能目录（如 WorkBuddy `~/.workbuddy/skills/agent-development-discipline/`，`SKILL.md` 用你习惯语言的那份），命中相关请求时自动生效。

隶属 [Development and Guidance Skills](https://github.com/GiantAxeint/development-and-guidance-skills)，MIT 许可。
