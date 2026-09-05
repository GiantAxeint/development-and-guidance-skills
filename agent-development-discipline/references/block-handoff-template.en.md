# Block Handoff Document: `<blockID>-<blockName>`

> Purpose: in multi-agent collaboration, the agent owning this block fills this in when done, then passes it to the next agent / stores it under `docs/handoff/`.
> The next agent **MUST read this document first** before touching anything. Do not rely on conversation memory.

## 1. Basic info

- Block ID / name:
- Executing agent:
- Finished at:
- Status: ☐ Done  ☐ Partially done (see "Open issues")  ☐ Blocked

## 2. Tech stack & versions (measured values, not recalled ones)

- Language/framework and version:
- Key dependencies and versions (verify by reading back with `npm ls` / `pip show`):
- Runtime environment requirements:

## 3. What changed in this block

- Files added/modified (path + one-line responsibility):
- Public interface definitions (function signatures / data structures / API endpoints / ports) that other blocks depend on:
- Data flow (who calls whom, how data moves):

## 4. How to run & verify

- Start command:
- Verification steps / self-test results:
- Integration points that need cooperation from other blocks:

## 5. Pitfalls hit & open issues

- Pitfall 1 (symptom → cause → fix):
- Open issues / TODOs (write explicitly for the next agent):
- Special warnings for the next agent (the easiest trap to fall into):

## 6. git record

- Commit hash of this block: `…` (so it can be rolled back to this version)
- Branch notes:
