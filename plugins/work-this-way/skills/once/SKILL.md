---
name: once
description: Qualify Work This Way controls activated in the same combo so they expire after one completed governed turn. Use only when the user invokes ONCE together with at least one activatable Work This Way control.
disable-model-invocation: true
---

# 1️⃣ Once

**ID:** `work-this-way/once`\
**HACP:** `0.4`\
**Kind:** `control`\
**Mode:** `qualify`\
**Traits:** `duration-qualifier`\
**Default Binding:** Controls activated in the same combo\
**Accepts:** `work-this-way/control-state`\
**Produces:** `work-this-way/control-state`\
**Duration:** `once`

## Effect

Set the duration of each Work This Way control activated in the same combo to `one-turn`. Consume the duration after one completed governed turn, including a completed `blocked` result. Do not consume it while the operation is `pending`, `deferred`, or the combo is `invalid`.

## Limits

- `ONCE` cannot qualify a control activated in an earlier message.
- It has no useful standalone effect and must not become hidden default state.
- It never changes controls from another deck.

## Format

Include `ONCE` in the compact Work state line beside the controls it qualifies. Do not add a separate explanation unless asked.
