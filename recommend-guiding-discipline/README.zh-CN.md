# 建议引导纪律（Recommend Guiding Discipline, RGD）

> 规范 AI 给建议与排障时的查证协作流程。
> English: [README.md](./README.md) ｜ 技能正文：[SKILL.zh-CN.md](./SKILL.zh-CN.md) / [SKILL.en.md](./SKILL.en.md)

**RGD** 约束 AI 在"给建议 / 帮排障"时保持诚实。它的每一条都由作者在真实事故后逐条定稿——那起事故里，AI 自信满满地给出**错误服务商**的排障步骤，让用户在迷茫中空转数轮。教训是：**信任建立在每次建议都经得起验证上。**

## 适用时机

任何回答涉及：

- 外部网站 / 服务 / 文档的现状
- 用户环境事实（域名、系统、账号、路径、配置）
- 软件版本与 API
- 故障排查、或任何逐步操作指引

## 六条铁律速览

1. **涉及网站：先浏览，再建议**——禁止凭记忆描述网站长什么样。
2. **环境事实：先问；问不到就限时自查**——禁止从名字/后缀联想推断。
3. **排查前先对齐入口**——走一步报一步，禁止一次倾倒一长串步骤。
4. **用户不是无所不知：适当补充与纠正**——发现矛盾直接指出，附上依据。
5. **验证方法与步骤：实际查证 + 编号循序渐进**——不给"凭感觉"的验证法。
6. **报错原文优先；冲突先问「是否中途改过」**——不脑补报错，不轻易否定任何一方。

## 文件清单

| 文件 | 用途 |
|---|---|
| `SKILL.zh-CN.md` / `SKILL.en.md` | 完整纪律正文（双语） |
| `references/case-history.zh-CN.md` / `.en.md` | 促成这套纪律的真实事故复盘（已脱敏）——读它才懂每条铁律为什么存在 |

## 怎么用起来

- **当作心智规则**：通读一遍 `SKILL.zh-CN.md`。六条铁律本质就一句话——查证、询问、诚实。
- **作为可安装技能**：把本目录放进你 agent 的技能目录（如 WorkBuddy `~/.workbuddy/skills/recommend-guiding-discipline/`，`SKILL.md` 用你习惯语言的那份），命中建议/排障类请求自动生效。
- **与 A2D 搭配**：RGD 管"建议与排障"，[A2D（Agent 开发纪律）](../agent-development-discipline/)管"用 agent 写代码"。二者合起来覆盖 AI 最容易翻车的两个场景。

隶属 [Development and Guidance Skills](https://github.com/GiantAxeint/development-and-guidance-skills)，MIT 许可。
