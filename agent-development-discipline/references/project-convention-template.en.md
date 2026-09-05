# Project Convention Template (copy to the project root as AGENTS.md or CLAUDE.md)

> Purpose: loaded automatically at the start of every session / every agent, to eliminate environment assumptions.
> Fill in real values, then remove these comments and example lines.

## Local environment (re-check before every dev session; never assume)

- OS: Windows 10.0.x (e.g. Win11) / Ubuntu 22.04 / macOS …
- Shell & terminal type: cmd / PowerShell / Git Bash / bash (note the default shell inside agent sandboxes)
- Project root path: `C:\path\to\project` (mind non-ASCII characters / spaces)
- Path conventions: prefer relative paths; never hardcode user directories; mind path-separator compatibility in Windows scripts
- Python: interpreter path (managed venv or system), install method (venv activation command)
- Node/npm: global npm prefix path; `npm install -g` forbidden (if your environment says so)
- Other toolchains: git, gcc, docker versions, etc.

## Common commands (use only what has been verified)

| Action | Command |
|---|---|
| Install dependencies | `…` |
| Start dev server | `…` |
| Run tests | `…` |
| Build | `…` |

## Project layout (one line per directory)

```
src/       main code
docs/      docs (incl. handoff/ directory)
tests/     tests
```

## Development discipline (the five laws)

1. Before installing any dependency, read the official docs to confirm the version. Never fill in versions from memory.
2. Before writing code, check the "Local environment" section above; if unsure, probe with real commands.
3. Solve exactly one technical block at a time; `git commit` immediately when it is done.
4. After each block, re-read the code and add comments (explain the why).
5. Multi-agent: before touching another agent's block, read the matching handoff doc under `docs/handoff/`; after finishing your own block, write a handoff doc and push to git.

## Known pitfalls (record them once hit, to avoid repeating)

- (example) npm 11 needs `--allow-scripts=<pkg>` to run postinstall
- (example) In some sandboxes `reg.exe` is blocked; read the registry with Python `winreg` instead
