---
name: clear
description: Clear every active Work This Way control while preserving controls, bindings, annotations, and state owned by other decks. Use only when the user invokes WORK CLEAR or explicitly asks to stop the active Work This Way controls.
disable-model-invocation: true
---

# 🧹 Work Clear

**ID:** `work-this-way/clear`\
**HACP:** `0.4`\
**Kind:** `control`\
**Mode:** `clear`\
**Traits:** `deck-clear`, `mutation-safe`\
**Default Binding:** Current Work This Way control state\
**Accepts:** `hacp/content`, `hacp/result`\
**Produces:** `work-this-way/control-state`\
**Duration:** `once`

## Effect

Remove every active control owned by `work-this-way`, including its duration
qualifiers. Leave all other bindings, annotations, controls, and state
untouched. Succeed when nothing is active; clearing is idempotent and
mutation-safe. The complete ordered stream still requires preflight.

## Limits

- Do not clear a pending approval or state owned by another deck.
- Do not treat this card as a global clear.

## Format

```text
> 🛠 WORK · CLEARED · NONE · WORK CLEAR
```
