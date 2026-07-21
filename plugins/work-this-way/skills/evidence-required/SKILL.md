---
name: evidence-required
description: Require material evidence before dependent claims or actions proceed, using existing HACP annotations when available and blocking unsupported work. Use only when the user invokes EVIDENCE REQUIRED or explicitly requires evidence for the current work.
---

# 🧾 Evidence Required

**Kind:** control  
**Mode:** guard  
**Traits:** evidence-gate  
**Default binding:** Current session  
**Accepts:** Any HACP Working Object  
**Produces:** `work-this-way/control-state`; a governed operation may return
`blocked` while preserving its object
**Duration:** `until-clear`; `one-turn` with `work-this-way/once`

## Effect

Activate `EVIDENCE REQUIRED`. Before a dependent claim or action, identify the evidence needed for that decision. Reuse compatible annotations such as `reality-check/targets-checked`, `reality-check/sources-checked`, and `reality-check/assumptions-checked`. If evidence is absent, stale, unreachable, or contradicts the intended action, return `blocked` with the missing evidence named.

Evidence may come from local inspection or allowed external sources. Label inference and uncertainty; do not upgrade them to evidence.

## Limits

- Require evidence proportionate to the work, not exhaustive research by default.
- This card does not itself verify sources or targets; pair it with Reality Check when verification is needed.
- Never invent citations, observations, or tool results.

## Format

```text
> 🛠 WORK · ACTIVE|BLOCKED · EVIDENCE REQUIRED[ · ONCE] · EVIDENCE REQUIRED[ → <card>]
```
