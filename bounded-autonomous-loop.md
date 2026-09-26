# Bounded autonomous loop

**English** · [Español](bounded-autonomous-loop.es.md)

**A contract that lets an agent iterate without a human between turns, without the
"the goal isn't met yet" argument becoming authority to do anything.**

## The contract

Seven elements, all required before a loop is allowed to run unattended:

| Element | Meaning |
| --- | --- |
| Verifiable objective | Stated so that something other than the agent can decide it is met |
| Action per turn | One unit of work per turn, not "whatever is needed" |
| Independent evaluator | The thing that judges is not the thing that acted |
| Limits | Max turns, max wall-clock, max spend |
| Authority | Enumerated **per effect**, never per goal |
| Durable checkpoint | State survives the process dying mid-loop |
| Escalation | A defined way to stop and ask |

## The invariants

1. One turn is one unit of work.
2. Each turn observes fresh state; never reason from a snapshot taken turns ago.
3. Evaluation is independent of execution.
4. **Permission is granted per effect, not per objective.** This is the load-bearing one.
5. Actions are idempotent and mutually excluded, so a retry is not a double charge.
6. *Not verifiable* is not a pass.
7. The checkpoint is durable, or the loop cannot be resumed — only restarted.

## Why invariant 4 is the important one

A loop authorised "to achieve X" will, on a long enough run, justify sending the message,
running the deploy or making the payment, because each of those genuinely serves X. A loop
authorised "to read this collection and write to this document" cannot, regardless of how
far from X it is. **Scope authority to effects, and an unmet goal stops being an argument.**

## What it costs

Friction. Every turn pays for a checkpoint and an evaluation. For short, cheap, fully
reversible work that is overhead you do not need.

## When not to use it

When a human is in the loop anyway — then the human *is* the independent evaluator, and
formalising it adds ceremony without adding safety.
