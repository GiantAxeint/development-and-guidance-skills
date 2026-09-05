---
name: agent-development-discipline
description: AI/agent 驱动开发的项目纪律与多 agent 协作规范（简称 A2D）。当要"用 AI/agent/Claude Code/OpenCode/Codex 等写代码、从零开发项目、搭建开发环境、多 agent 分工完成大项目"，或遇到版本幻觉、环境不一致、代码无人维护、多 agent 交接混乱等痛点时使用。核心五律：①版本先行 ②环境感知 ③单区块原子提交 ④通读+注释 ⑤分块+文档交接。English version: SKILL.en.md. English triggers: AI coding workflow, multi-agent development, AI-driven development, coding with Claude Code.
---

# Agent 开发纪律（Agent-Development Discipline, A2D）

## Overview

用 AI agent 写代码时，最大的成本不是"写得慢"，而是**环境错乱、版本幻觉、代码无人复核、多 agent 互相踩脚**导致的返工。本纪律把 AI 编码约束为五条铁律，保证每个开发步骤可回滚、可复核、可交接。

适用场景：个人网站开发、从零搭建项目、给已有项目加功能、多个 agent 并行完成一个中型以上项目。

## 五条铁律（总纲）

1. **版本先行**：安装/引入任何依赖前，先读官方文档查清版本与 API 签名，再下载。禁止凭记忆或让 agent 凭空猜测版本。
2. **环境感知**：写任何代码前，先查明本机 OS、shell、路径规范、包管理方式与启动命令，写入项目根 `AGENTS.md`（模板见 `references/project-convention-template.zh-CN.md`）。
3. **单区块原子提交**：给 agent 一个硬限制——一次只解决一个技术区块；解决完**立即 git 提交**保留版本，再进入下一个区块。
4. **通读 + 注释**：每个区块完成后，agent 必须先通读自己写的代码并补上大致注释（解释"为什么"重于"是什么"），确保人能读懂、能维护。
5. **分块 + 文档交接**：项目级任务，先由人把需求拆成技术区块，将不同区块分派给不同 agent；每个 agent 完成后把相关信息写成交接文档，传给下一个 agent 让它理解当前进度，随后上传 git 保留版本。

## 工作流程

```
项目级需求
   │
   ▼
[阶段A] 环境盘点与版本锁定 ─────────────┐
   │                                    │
   ▼                                    │
[阶段B] 技术分块 + 多 agent 分派          │ 单文件小改动
   │                                    │ 可从此处直接进入
   ▼                                    │ 区块执行循环
[阶段C] 区块执行循环（每个 agent 内部）    │
   │  ① 只解本区块                       │
   │  ② 通读 + 注释                     │
   │  ③ git 提交（原子）                │
   │  ④ 写交接文档 → 传给下一个 agent     │
   ▼                                    │
[阶段D] 集成验证 + 收口                 ◄┘
```

## 阶段 A：环境盘点与版本锁定

执行任何安装/编码前，先做环境盘点：

1. **查明主机环境**（用命令实测，不要假设）：
   - OS 与版本（Windows/Linux/macOS）、CPU 架构
   - 当前 shell 类型（cmd / PowerShell / Git Bash）
   - 项目所在路径规范（是否含中文/空格、盘符）
   - 包管理器及全局安装位置（如系统 npm 的实际路径）
   - 启动/构建命令（`npm run dev`、`python app.py` 等）
2. **把以上信息写入项目根 `AGENTS.md` / `CLAUDE.md`**：这样每个新会话/新 agent 启动即加载，不会重复犯环境错误。使用 `references/project-convention-template.zh-CN.md` 为模板。
3. **版本锁定**：装任何包前，先读该包的官方文档（npm registry / PyPI / GitHub README），确认：最新稳定版本号、与你现有依赖的兼容性、是否需要额外编译步骤。**禁止让 agent 凭训练记忆填写版本号**——版本幻觉是 AI 编码第一返工源。装完用 `pip show` / `npm ls` 等实测回读确认落盘版本。

## 阶段 B：技术分块与多 agent 分派

大项目先拆块，再派人：

1. **画依赖图**：把需求拆成互相独立的"技术区块"（如：UI 区块 / API 区块 / 数据库区块 / 部署区块），标注块间接口（函数签名、数据结构、端口）。
2. **接口先行**：先定各区块的公共接口与数据流，再让各 agent 并行开工——接口不先定，并行必冲突。
3. **一人一块**：每个区块指派一个 agent；**同一时间只允许一个 agent 写共享文件**（如根配置、接口定义文件），其余 agent 写自己的目录。
4. **任务卡**：给每个 agent 的指令里写明——负责哪个区块、依赖谁、验收标准、完成后写交接文档。

## 阶段 C：区块执行循环（每个 agent 内部强制执行）

```
解决本区块代码问题
   ↓
通读自己产出的代码，补充大致注释（为什么这么做）
   ↓
git add + commit（一次提交只含本区块，message 写清区块名）
   ↓
写交接文档（模板见 references/block-handoff-template.zh-CN.md）
   ↓
（多 agent 场景）把交接文档发给下一个 agent，再继续自己的下一区块
```

要点：

- **一次只解一个区块**：即使 agent 提出"顺手把 X 也改了"，也拒绝——保持提交粒度与代码 blame 可追溯。
- **注释标准**：注释解释"为什么"（业务原因、踩过的坑、权衡），不重复代码本身；关键函数必须有 docstring。
- **提交规范**：每个区块一个 commit，message 格式建议 `<区块名>: <做了什么>`；commit 后立即推送到远端（如适用）双保险。

## 阶段 D：集成验证与收口

所有区块完成后：

1. 让一个"集成 agent"（或主 agent）通读全局代码，验证区块间接口对接无误。
2. 跑一遍完整启动/测试流程，确认整体可运行。
3. 更新 `AGENTS.md`（新增命令、新目录结构、新坑记录）。
4. 打 tag 或合并主干，全项目 git 提交收口。

## Resources

- `references/project-convention-template.zh-CN.md` — 项目根 AGENTS.md/CLAUDE.md 模板（环境信息表 + 纪律摘要），每个项目初始化时复制填写。
- `references/block-handoff-template.zh-CN.md` — 区块交接文档模板，每个 agent 完成区块后填写并传给下一个 agent。
