---
name: work-local-only
description: Restrict governed work to local resources and block network, connector, remote repository, hosted service, or external-message access until cleared. Use only when the user invokes LOCAL ONLY or explicitly requests local-only work.
---

# 🏠 Local Only

**Kind:** control  
**Mode:** guard  
**Traits:** refusal, external-access-guard  
**Default binding:** Current session  
**Accepts:** Any HACP Working Object  
**Produces:** `work-this-way/control-state`; a governed operation may return
`blocked` while preserving its object
**Duration:** `until-clear`; `one-turn` with `work-this-way/once`

## Effect

Activate `LOCAL ONLY`. Permit work against the local workspace, local files, and already available conversation context. Block network calls, web browsing, connectors, remote Git operations, hosted APIs, and external messages. A card such as `reality-check/check-sources` may still run, but it must inspect only local evidence and annotate that limitation.

## Limits

- Do not silently substitute remote evidence with an unsupported claim.
- Do not claim provider isolation; this is a behavioral control.
- Reading a locally cached remote artifact is local access and must be identified as cached evidence.

## Format

```text
> 🛠 WORK · ACTIVE|BLOCKED · LOCAL ONLY[ · ONCE] · LOCAL ONLY[ → <card>]
```
