---
name: local-only
description: Restrict governed work to local resources and block network, connector, remote repository, hosted service, or external-message access until cleared. Use only when the user invokes LOCAL ONLY or explicitly requests local-only work.
disable-model-invocation: true
---

# 🏠 Local Only

**ID:** `work-this-way/local-only`\
**HACP:** `0.4`\
**Kind:** `control`\
**Mode:** `guard`\
**Traits:** `session-control`, `refusal`, `external-access-guard`\
**Default Binding:** Current session\
**Accepts:** `hacp/content`, `hacp/result`\
**Produces:** `work-this-way/control-state`; a governed operation may return
`blocked` while preserving its object\
**Duration:** `until-clear`; a same-combo duration qualifier may assign
`one-turn`

## Effect

Activate a guard against `external-access`. Permit work against the local
workspace, local files, cached artifacts, command output, and available
conversation context. Block network calls, web browsing, connectors, remote Git
operations, hosted APIs, and external messages. An operation that has a valid
local path may continue and must preserve that limitation in its result.

## Limits

- Do not silently substitute remote evidence with an unsupported claim.
- Do not claim provider isolation; this is a behavioral control.
- Reading a locally cached remote artifact is local access and must be identified as cached evidence.

## Format

```text
> 🛠 WORK · ACTIVE|BLOCKED · LOCAL ONLY[ · ONCE] · LOCAL ONLY[ → <card>]
```
