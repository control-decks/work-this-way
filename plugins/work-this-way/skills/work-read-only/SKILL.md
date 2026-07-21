---
name: work-read-only
description: Block all HACP operations carrying the mutation trait until cleared or for one completed governed turn when combined with ONCE. Use only when the user invokes READ ONLY or explicitly asks to make the current session read-only.
---

# 🔒 Read Only

**Kind:** control  
**Mode:** guard  
**Traits:** refusal, mutation-guard  
**Default binding:** Current session  
**Accepts:** Any HACP Working Object  
**Produces:** `work-this-way/control-state`; a governed operation may return
`blocked` while preserving its object
**Duration:** `until-clear`; `one-turn` with `work-this-way/once`

## Effect

Activate `READ ONLY`. Before any later operation, inspect its manifest traits
and concrete effects. If it mutates, do not call mutating tools and return
`blocked`. Preserve the requested operation and its binding in the Working
Object so a safe later card can consume the block.

Reading, searching, inspecting, reasoning, checking, explaining, and clearing Work controls remain allowed unless another active control blocks them.

## Limits

- Never reinterpret `READ ONLY` as “ask first.” It is a refusal.
- Never claim a technical sandbox.
- A later `READ ONLY` cannot retroactively protect an earlier mutation; preflight rejects the full combo before any effect.

## Format

```text
> 🛠 WORK · ACTIVE|BLOCKED · READ ONLY[ · ONCE] · READ ONLY[ → <card>]
```

State what was blocked in one sentence when status is `BLOCKED`.
