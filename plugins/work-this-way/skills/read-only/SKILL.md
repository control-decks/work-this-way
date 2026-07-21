---
name: read-only
description: Block all HACP operations carrying the mutation trait until cleared or for one completed governed turn when combined with ONCE. Use only when the user invokes READ ONLY or explicitly asks to make the current session read-only.
disable-model-invocation: true
---

# 🔒 Read Only

**ID:** `work-this-way/read-only`\
**HACP:** `0.4`\
**Kind:** `control`\
**Mode:** `guard`\
**Traits:** `session-control`, `refusal`, `mutation-guard`\
**Default Binding:** Current session\
**Accepts:** `hacp/content`, `hacp/result`\
**Produces:** `work-this-way/control-state`; a governed operation may return
`blocked` while preserving its object\
**Duration:** `until-clear`; a same-combo duration qualifier may assign
`one-turn`

## Effect

Activate a guard that blocks the `mutation` trait. Before any later operation,
inspect its manifest traits and concrete effects. If it mutates, do not call
mutating tools and return
`blocked`. Preserve the requested operation and its binding in the Working
Object so a safe later card can consume the block.

Reading, searching, inspecting, reasoning, checking, presenting, and clearing
this deck's controls remain allowed unless another active control blocks them.

## Limits

- Never reinterpret `READ ONLY` as “ask first.” It is a refusal.
- Never claim a technical sandbox.
- A later `READ ONLY` cannot retroactively protect an earlier mutation; preflight rejects the full combo before any effect.

## Format

```text
> 🛠 WORK · ACTIVE|BLOCKED · READ ONLY[ · ONCE] · READ ONLY[ → <card>]
```

State what was blocked in one sentence when status is `BLOCKED`.
