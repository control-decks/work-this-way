---
name: work-ask-first
description: Require explicit approval before each described batch of mutations, preserving the intended operation as pending and resuming it after approval. Use only when the user invokes ASK FIRST or explicitly requests approval before mutation.
---

# ✋ Ask First

**Kind:** control  
**Mode:** guard  
**Traits:** approval-gate, mutation-guard  
**Default binding:** Current session  
**Accepts:** Any HACP Working Object  
**Produces:** `work-this-way/control-state` or a pending Working Object  
**Duration:** `until-clear`; `one-turn` with `work-this-way/once`

## Effect

Activate `ASK FIRST`. Before a mutation, describe the smallest concrete batch: targets, intended changes, and meaningful external effects. Do not mutate yet. Return `pending` and request explicit approval. Mark dependent cards `deferred` without running them.

After approval, resume at the suspended operation. Ask again if its scope, targets, or external effects changed. If approval is denied, return `blocked` and preserve the refusal in the Working Object.

## Limits

- Approval never overrides `READ ONLY`, `LOCAL ONLY`, higher-priority instructions, or unavailable authority.
- Group mutations only when they were described as one coherent batch.
- Do not request approval for read-only work.

## Format

```text
> 🛠 WORK · PENDING · ASK FIRST[ · ONCE] · ASK FIRST → <mutation>
```

Follow with the approval question and no unrelated explanation.
