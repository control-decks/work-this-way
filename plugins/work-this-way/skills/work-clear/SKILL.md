---
name: work-clear
description: Clear every active Work This Way control while preserving controls, bindings, annotations, and state owned by other decks. Use only when the user invokes WORK CLEAR or explicitly asks to stop the active Work This Way controls.
---

# 🧹 Work Clear

**Kind:** control  
**Mode:** clear  
**Traits:** deck-clear, mutation-safe  
**Default binding:** Current Work This Way control state  
**Accepts:** Any HACP Working Object  
**Produces:** `work-this-way/control-state`  
**Duration:** `one-shot`

## Effect

Remove all active Work This Way controls: `READ ONLY`, `ASK FIRST`, `LOCAL ONLY`, and `EVIDENCE REQUIRED`, including their `ONCE` qualifiers. Leave every other deck's state untouched. Succeed when nothing is active; clearing is idempotent.

The full ordered stream is still prevalidated. `READ ONLY → WORK CLEAR → IMPLEMENT` is valid because clearing control state is mutation-safe and `IMPLEMENT` runs after the clear. `IMPLEMENT → READ ONLY` remains invalid because the late control cannot govern the earlier operation.

## Limits

- Do not clear a pending user approval record from another deck.
- Do not treat `CLEAR` as a global alias; the canonical identity is `work-this-way/work-clear`.

## Format

```text
> 🛠 WORK · CLEARED · NONE · WORK CLEAR
```
