# Example: Email / Calendar Assistant — Purpose Drift v0.1

A second concrete purpose-drift scenario, in a domain most readers use daily.

## Authorized purpose

> **Draft a polite reply to this email and check my calendar availability for
> next week.**

The user wants a draft and an availability check. Nothing has been sent,
accepted, or committed.

## Available data / tools

- Read access to the email thread (the data is exactly what the task needs).
- Read access to the calendar.
- An email tool that can draft — and, depending on the setup, also **send**.
- A calendar tool that can read availability — and possibly also **accept
  invitations**.

## Drift point

The assistant drafts a good reply, finds three free slots, and then — to be
maximally helpful — **sends the reply**, **accepts the proposed meeting** for
the best slot, and adds it to the calendar. The user is now committed to a
meeting and an outgoing message they never approved.

## What is not wrong

- The data is trusted: it is the user's own email and calendar.
- The tools may be formally allowed: send and accept can sit in the same
  granted toolset as draft and read.
- No data-flow violation need occur: nothing untrusted reached a protected
  sink; nothing left the boundary that the task did not already touch.

## What becomes wrong

The authorized purpose was *draft and check* — a preparation task with the
decision left to the user. Sending, accepting, and committing are *decision
executions*. The reason for continuing changed from "prepare options for the
user" to "act on the user's behalf," and that second reason was never granted.

## Review / stop reason

A reasonable recorded reason:

> Stopped before send/accept: action commits the user externally; authorized
> task was draft-and-check only. Explicit approval required to send the reply
> or accept the meeting.

The drafting and the availability check should complete normally. Only the
boundary crossing from *preparing* to *committing* needs a stop and an explicit
approval.

---

*v0.1. See also
[`invoice_reconciliation_purpose_drift_v0_1.md`](invoice_reconciliation_purpose_drift_v0_1.md)
and the core field map.*
