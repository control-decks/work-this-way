---
name: deck
description: Supply the shared Work This Way deck rules whenever the user invokes Work This Way, plays or combines one of its cards, or when an active Work This Way control governs the current turn. Resolve ordered HACP controls and operations, preserve session state visibly, and never treat semantic controls as a technical sandbox.
---

# 🛠 Work This Way

Work This Way is a HACP deck for changing how the agent works during the current session. Cards are explicit controls, not hidden preferences and not permission grants.

## Resolve the message

- Read prose and card invocations as one ordered stream.
- Prevalidate the whole stream before the first effect. Reject it as `invalid` if a control arrives too late to govern an earlier operation.
- A card before content acts prospectively. A card after content consumes the Working Object accumulated to its left. An intermediate card updates the object before later cards receive it.
- Pass the current HACP Working Object to every adjacent card, including cards from another deck.
- Never reorder cards, invent an invocation, or expose this deck's internal state as another deck's mental model.

## Working Object

Maintain only the interoperable envelope:

```text
Binding
Status: success | blocked | pending
Kind: namespaced result kind
Content: visible result
Annotations: checks that preserve the object
Source: slug of the last card
```

`blocked` remains transferable to safe cards such as `think-it-through/explain`. `pending` suspends a mutation; dependent cards are `deferred` until approval. Resume at the suspended operation after approval.

## Active controls

- `READ ONLY` blocks every operation with the `mutation` trait and every
  concrete mutating effect or tool call.
- `ASK FIRST` suspends each described mutation batch for approval. A changed scope, target set, or external effect requires a new approval.
- `LOCAL ONLY` blocks access to or mutation of non-local resources while
  allowing cards to continue through a valid local-only path.
- `EVIDENCE REQUIRED` blocks dependent work until the needed evidence is present.
- A strong refusal always outranks approval.
- Controls last until `WORK CLEAR` by default. `ONCE` changes only controls activated in the same combo to one completed governed turn.
- `WORK CLEAR` removes every Work This Way control and no state from another deck. It is idempotent.

Controls are session state only. Never persist them as a user preference. They constrain the agent's available authority; they never create new authority or bypass higher-priority instructions.

## Visibility and economy

Every governed response starts with one compact line:

```text
> 🛠 WORK · <status> · <active controls or NONE> · <card or combo>
```

Then return the smallest useful result. Do not print intermediate objects or explain HACP unless asked. With no active card or control, respond normally without a trace.

## Boundary

These are behavioral contracts. They do not create an operating-system sandbox, revoke tool access, or guarantee provider-level enforcement. State that distinction when it matters.
