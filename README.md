# Work This Way

**Visible controls for how your agent works, right now.**

Work This Way turns session-only preferences into explicit cards. Set a boundary, combine it with an action, see the active state, and clear it when the situation changes.

## The problem

“Be careful” and “ask me first” are easy to lose inside a long prompt. They also become dangerous when the agent cannot tell whether they apply once, for the current subject, or until the user stops them. Work This Way makes that state explicit and composable.

![Work This Way hero](assets/work-this-way-hero.jpg)

## The flagship card

### READ ONLY

`READ ONLY` blocks every HACP operation marked `mutation`. It lasts until `WORK CLEAR` unless combined with `ONCE`.

```text
READ ONLY → IMPLEMENT → THINK EXPLAIN

> 🛠 WORK · BLOCKED · READ ONLY · READ ONLY → IMPLEMENT → THINK EXPLAIN
No changes were made. IMPLEMENT was blocked because READ ONLY is active.
```

The blocked result remains a valid Working Object, so safe cards from another deck can still explain or inspect it.

## Install

Install the HACP session adapter once, then the deck. Without a compatible
adapter the commands may appear, but the session is not fully HACP-conforming.

### Codex

```bash
codex plugin marketplace add control-decks/human-agent-control-protocol
codex plugin add hacp@hacp
codex plugin marketplace add control-decks/work-this-way
codex plugin add work-this-way@work-this-way
```

Use `$work-this-way:help` or play `$work-this-way:read-only`.

### Claude Code

```bash
claude plugin marketplace add control-decks/human-agent-control-protocol --scope user
claude plugin install hacp@hacp --scope user
claude plugin marketplace add control-decks/work-this-way --scope user
claude plugin install work-this-way@work-this-way --scope user
```

Use `/work-this-way:help` or play `/work-this-way:read-only`.

## The deck

| Card | What it controls | Default duration |
|---|---|---|
| `READ ONLY` | Blocks mutation | Until clear |
| `ASK FIRST` | Requires approval before each mutation batch | Until clear |
| `LOCAL ONLY` | Keeps governed work on local resources | Until clear |
| `EVIDENCE REQUIRED` | Requires evidence before dependent work | Until clear |
| `ONCE` | Limits controls in the same combo | One completed turn |
| `WORK CLEAR` | Clears all Work This Way controls | One resolution |
| `IMPLEMENT` | Executes the current actionable direction | One resolution |

## Combos

```text
ASK FIRST → IMPLEMENT
```

The implementation becomes `pending`; after approval, resolution resumes at `IMPLEMENT`.

```text
LOCAL ONLY → REALITY CHECK SOURCES
```

Reality Check runs, but consults only local sources and records that boundary.

```text
READ ONLY → ONCE → IMPLEMENT → THINK EXPLAIN
```

The mutation is blocked and the one-turn control expires after that completed governed turn.

```text
WORK CLEAR → IMPLEMENT
```

All Work controls are removed before the action. State from other decks stays intact.

## Rules

- Cards resolve left to right as one ordered HACP stream.
- The whole combo is prevalidated before any effect.
- A late control cannot govern an earlier operation: `IMPLEMENT → READ ONLY` is invalid and produces no effect.
- A refusal outranks an approval request.
- Controls change behavior in this session only. They never expand authority.
- Every governed response shows one compact Work state line.
- With no card and no active control, the agent responds normally without a trace.

## HACP

Work This Way implements [HACP Draft 0.4](https://github.com/control-decks/human-agent-control-protocol): **Cards are the interface. Control is the protocol.** The HACP adapter supplies ordered resolution; each Work card contains only its own effect and open semantic relations. Cards are explicit human commands and cannot be inferred or replayed by the agent.

This is a semantic protocol, not a technical sandbox or permission system.

## Detailed reference

- Canonical card metadata: [`hacp.deck.json`](hacp.deck.json)
- Provider-independent behavior: [`plugins/work-this-way/skills`](plugins/work-this-way/skills)
- Protocol: [Human-Agent Control Protocol](https://github.com/control-decks/human-agent-control-protocol)

MIT © thevzion · Published by Control Decks
