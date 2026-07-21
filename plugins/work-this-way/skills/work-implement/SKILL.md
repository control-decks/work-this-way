---
name: work-implement
description: Execute an explicit actionable request or the accepted or explicitly provisional current plan under all active controls. Use only when the user invokes IMPLEMENT or explicitly asks to implement the current actionable direction.
---

# ⚙️ Implement

**Kind:** operation  
**Mode:** action  
**Traits:** mutation  
**Default binding:** Explicit action request, otherwise the accepted or provisional current plan  
**Accepts:** `hacp/content` or `hacp/result`
**Produces:** `work-this-way/implementation-result`  
**Duration:** `once`

## Resolve the operation

1. Resolve the binding. If no concrete action or accepted or provisional plan exists, ask for scope and return `pending` without guessing.
2. Preflight the entire combo and all active controls before the first mutation.
3. Under `READ ONLY`, return `blocked` without mutating.
4. Under `ASK FIRST`, describe the mutation batch, return `pending`, and resume here after approval.
5. Under `LOCAL ONLY`, exclude external access and block the operation if the requested result requires it.
6. Under `EVIDENCE REQUIRED`, require compatible evidence before dependent changes.
7. Execute only the authorized, feasible scope. Verify the result in proportion to risk.

Return the real implementation result as the Working Object. If a later presentation card such as `think-it-through/explain` follows, pass that object without printing a duplicate intermediate report.

## Limits

- Never expand authority, scope, targets, or side effects.
- Never override a control, higher-priority instruction, provider boundary, or missing credential.
- Never report success for a blocked, pending, partial, or unverified mutation.

## Format

```text
> 🛠 WORK · SUCCESS|BLOCKED|PENDING · <active controls or NONE> · IMPLEMENT
```

Then return only the smallest useful implementation result or blocking reason.
