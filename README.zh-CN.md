<div align="right">

[English](README.md) | **[中文](README.zh-CN.md)**

</div>

# Development and Guidance Skills

> 两套在真实项目中磨出来的 AI 协作纪律——一套管**用 agent 写代码**，一套管**给建议与排障时的查证**。
> English: [README.md](./README.md)

这个仓库收录两套纪律，它们诞生于真实项目而非理论——每一套都因为某种真实翻车付出了时间与返工成本，并由作者在与 Claude Code、OpenCode 等 agent 的日常协作中逐句打磨定稿。

| | [Agent 开发纪律（A2D）](./agent-development-discipline/) | [Agent 引导纪律（AGD）](./agent-guiding-discipline/) |
|---|---|---|
| **管什么** | 用 AI agent 写代码 | AI 给建议 / 排障 |
| **要解决的问题** | 环境错乱、版本幻觉、代码无人复核、多 agent 互相踩脚 | 自信地答错——凭记忆描述网站、看域名猜环境事实、一次性倾倒一长串步骤 |
| **解法** | 五律：①版本先行 ②环境感知 ③单区块原子提交 ④通读+注释 ⑤分块+文档交接 | 六律：①先浏览再建议 ②环境事实先问（限时自查）③排查先对齐入口 ④敢纠正不附和 ⑤编号循序渐进 ⑥报错原文优先 |
| **何时用** | 用 agent 建站/做项目、多 agent 协作 | 回答涉及网站、用户环境、软件版本、故障排查 |

两套纪律均**中英双语**发布：每个技能含 `SKILL.zh-CN.md` + `SKILL.en.md`，每个 README 含 `.zh-CN.md` + `.md`，所有模板参考文件也都双语文档化。

## 仓库结构

```
development-and-guidance-skills/
├── README.md  README.zh-CN.md   项目总览（中文 / EN）
├── LICENSE                        MIT
├── agent-development-discipline/  A2D — 编码纪律（五律）
│   ├── SKILL.zh-CN.md  SKILL.en.md
│   ├── README.zh-CN.md  README.md
│   └── references/
│       ├── project-convention-template.zh-CN.md / .en.md   AGENTS.md 模板
│       └── block-handoff-template.zh-CN.md / .en.md        交接文档模板
└── agent-guiding-discipline/  AGD — 建议与排障纪律（六律）
    ├── SKILL.zh-CN.md  SKILL.en.md
    ├── README.zh-CN.md  README.md
    └── references/
        └── case-history.zh-CN.md / .en.md   促成 AGD 的真实事故复盘（已脱敏）
```

## 快速开始

1. **A2D——用 agent 写代码**：读 [`agent-development-discipline/SKILL.zh-CN.md`](./agent-development-discipline/SKILL.zh-CN.md)（或 `.en.md`）；每个新项目把 [`project-convention-template`](./agent-development-discipline/references/) 复制为项目根 `AGENTS.md` / `CLAUDE.md` 并填真实环境值。
2. **AGD——建议与排障**：读一遍 [`agent-guiding-discipline/SKILL.zh-CN.md`](./agent-guiding-discipline/SKILL.zh-CN.md)（或 `.en.md`）——核心就三个词：查证、询问、诚实。再读 [`case-history`](./agent-guiding-discipline/references/) 理解每条铁律的由来。

### 安装为 agent 技能（可选）

把任一目录复制进你 agent 的技能目录，命中相关请求时自动生效。以 WorkBuddy 为例：

```bash
# A2D（SKILL.md 选用你习惯语言的那份）
cp -r agent-development-discipline ~/.workbuddy/skills/agent-development-discipline
cp agent-development-discipline/SKILL.zh-CN.md ~/.workbuddy/skills/agent-development-discipline/SKILL.md
```

其他 harness（Claude Code / OpenCode / Codex）会自动读取项目根 `AGENTS.md` / `CLAUDE.md`，无需技能系统即可用上模板。

## License

[MIT](./LICENSE) © 2026 Erius（GiantAxeint）。可自由使用、改编、再分发——纪律本来就是用来传播的。

*在 Windows 上产出，经真实 agent 会话每日验证。欢迎 Issue 与 PR。*
