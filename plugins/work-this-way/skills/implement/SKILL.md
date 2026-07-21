---
name: implement
description: Execute an explicit actionable request or the accepted or explicitly provisional current plan under all active controls. Use only when the user invokes IMPLEMENT or explicitly asks to implement the current actionable direction.
disable-model-invocation: true
---

# ⚙️ Implement

**ID:** `work-this-way/implement`\
**HACP:** `0.4`\
**Kind:** `operation`\
**Mode:** `action`\
**Traits:** `mutation`\
**Default Binding:** Explicit action request, otherwise accepted or provisional
current plan\
**Accepts:** `hacp/content`, `hacp/result`\
**Requires:** `hacp/actionable-direction`, `hacp/user-authorized-scope`\
**Produces:** `work-this-way/implementation-result`\
**Duration:** `once`

**Effect:** Execute only the authorized actionable direction under every active
control, then return the observed result.

## Resolve the operation

1. Resolve the Binding. If no concrete action or accepted or provisional plan exists, ask for scope and return `pending` without guessing.
2. Preflight the entire combo and all active controls before the first mutation.
3. If an active control blocks `mutation`, return `blocked` without mutating.
4. If an active control gates `mutation`, describe the mutation batch, return `pending`, and resume here after approval.
5. If an active control blocks `external-access`, use an allowed local path or return `blocked` when none can satisfy the request.
6. If an active control requires evidence, use only compatible scoped evidence annotations before dependent changes.
7. Execute only the authorized, feasible scope. Verify the result in proportion to risk.

Return the observed implementation result as the Working Object. When a later
presentation follows, pass the object without printing a duplicate intermediate
report.

## Limits

- Never expand authority, scope, targets, or side effects.
- Never override a control, higher-priority instruction, provider boundary, or missing credential.
- Never report success for a blocked, pending, partial, or unverified mutation.

## Format

```text
> 🛠 WORK · SUCCESS|BLOCKED|PENDING · <active controls or NONE> · IMPLEMENT
```

Then return only the smallest useful implementation result or blocking reason.
