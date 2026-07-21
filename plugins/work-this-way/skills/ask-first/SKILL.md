---
name: ask-first
description: Require explicit approval before each described batch of mutations, preserving the intended operation as pending and resuming it after approval. Use only when the user invokes ASK FIRST or explicitly requests approval before mutation.
disable-model-invocation: true
---

# ✋ Ask First

**ID:** `work-this-way/ask-first`\
**HACP:** `0.4`\
**Kind:** `control`\
**Mode:** `guard`\
**Traits:** `session-control`, `approval-gate`, `mutation-guard`\
**Default Binding:** Current session\
**Accepts:** `hacp/content`, `hacp/result`\
**Produces:** `work-this-way/control-state`; a governed mutation may become
`pending` while preserving its object\
**Duration:** `until-clear`; a same-combo duration qualifier may assign
`one-turn`

## Effect

Activate an approval gate for the `mutation` trait. Before a governed mutation,
describe the smallest concrete batch: targets, intended changes, and meaningful
external effects. Do not mutate yet. Return `pending`, request explicit
approval, and defer dependent cards.

After approval, resume at the suspended operation. Ask again if its scope, targets, or external effects changed. If approval is denied, return `blocked` and preserve the refusal in the Working Object.

## Limits

- Approval never overrides a blocking control, higher-priority instruction, or unavailable authority.
- Group mutations only when they were described as one coherent batch.
- Do not request approval for read-only work.

## Format

```text
> 🛠 WORK · PENDING · ASK FIRST[ · ONCE] · ASK FIRST → <mutation>
```

Follow with the approval question and no unrelated explanation.
