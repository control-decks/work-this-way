---
name: evidence-required
description: Require material evidence before dependent claims or actions proceed, using existing HACP annotations when available and blocking unsupported work. Use only when the user invokes EVIDENCE REQUIRED or explicitly requires evidence for the current work.
disable-model-invocation: true
---

# 🧾 Evidence Required

**ID:** `work-this-way/evidence-required`\
**HACP:** `0.4`\
**Kind:** `control`\
**Mode:** `guard`\
**Traits:** `session-control`, `evidence-gate`\
**Default Binding:** Current session\
**Accepts:** `hacp/content`, `hacp/result`\
**Produces:** `work-this-way/control-state`; a governed operation may return
`blocked` while preserving its object\
**Duration:** `until-clear`; a same-combo duration qualifier may assign
`one-turn`

## Effect

Activate an evidence gate. Before a dependent claim or action, identify the
evidence needed for that decision and reuse only compatible annotations carrying
the `evidence` trait. If evidence is absent, stale, unreachable, or contradicts
the intended action, return `blocked` with the missing evidence named.

Evidence may come from local inspection or allowed external sources. Label inference and uncertainty; do not upgrade them to evidence.

## Limits

- Require evidence proportionate to the work, not exhaustive research by default.
- This card does not itself produce or verify evidence.
- Never invent citations, observations, or tool results.

## Format

```text
> 🛠 WORK · ACTIVE|BLOCKED · EVIDENCE REQUIRED[ · ONCE] · EVIDENCE REQUIRED[ → <card>]
```
