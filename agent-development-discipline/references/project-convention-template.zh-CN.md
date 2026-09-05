# 项目公约模板（复制为项目根 AGENTS.md 或 CLAUDE.md）

> 用途：每个会话/每个 agent 启动时自动加载，杜绝环境假设错误。
> 填写真实值后，删除本注释与示例行。

## 本机环境（每次开发前必须核对，禁止假设）

- OS：Windows 10.0.x（如 Win11）/ Ubuntu 22.04 / macOS …
- Shell 与终端类型：cmd / PowerShell / Git Bash / bash（注明 agent 沙箱内默认 shell）
- 项目根路径：`C:\path\to\project`（注意是否含中文/空格）
- 路径规范：一律使用相对路径；禁止硬编码用户目录；Windows 下脚本路径分隔符兼容性
- Python：解释器路径（managed venv 或系统），包安装方式（venv 激活命令）
- Node/npm：npm 全局 prefix 路径；禁止 `npm install -g`（若环境有该约定）
- 其他工具链：git、gcc、docker 等版本

## 常用命令（实测可用的为准）

| 操作 | 命令 |
|---|---|
| 安装依赖 | `…` |
| 启动开发服务 | `…` |
| 跑测试 | `…` |
| 构建 | `…` |

## 项目结构（一句话说明每个目录干嘛）

```
src/       主代码
docs/      文档（含 handoff/ 交接文档目录）
tests/     测试
```

## 开发纪律（五条铁律）

1. 装任何依赖前，先读官方文档确认版本，禁止凭记忆/凭空填版本号。
2. 写码前先核对本文件"本机环境"，不确定就跑命令实测。
3. 一次只解决一个技术区块；解决完立即 `git commit` 保留版本。
4. 每完成一个区块，通读代码并补注释（解释为什么）。
5. 多 agent 协作：接手别人区块前，先读 `docs/handoff/` 下对应交接文档；完成自己的区块后写交接文档再上传 git。

## 已知坑（踩过就记，防止再犯）

- （示例）npm 11 需要 `--allow-scripts=<pkg>` 才能跑 postinstall
- （示例）某沙箱内 reg.exe 被拦，读注册表用 Python winreg
