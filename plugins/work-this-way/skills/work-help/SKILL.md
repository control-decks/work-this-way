---
name: work-help
description: Explain Work This Way, clarify one of its cards or active controls, or recommend normal conversation, one card, or a short combo. Use only when the user invokes work-help or explicitly asks how to use the deck. Never activate a recommended control.
---

# 🛠 Work Help

Treat this as contextual help, not a card.

## Deck guide

```text
READ ONLY          block mutation
ASK FIRST          require approval before mutation
LOCAL ONLY         keep governed work local
EVIDENCE REQUIRED  require evidence before dependent work
ONCE               limit new controls to one completed turn
WORK CLEAR         clear every Work This Way control
IMPLEMENT          execute the current actionable direction
```

With no argument, recommend zero to three useful interactions from the current context. Recommend `Continue normally` when no card improves the next turn. With a card name, explain its binding, effect, result, duration, limits, and one example. Use provider syntax when known and portable `/work-*` notation otherwise.

Never play a card, change state, grant authority, or recommend domain actions.

## Format

```text
> 🛠 WORK HELP · <resolved request>

Recommended interaction
<normal conversation, card, or combo>

Why
<short explanation>

Try
<exact command when applicable>
```

Give at most three recommendations. Omit `Try` for normal conversation.
