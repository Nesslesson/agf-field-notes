# AI Interface Governance Theses v0.1

**Governance must become visible UX.**

A short set of theses about why governance for acting AI cannot live only in
policy and logs — it has to show up in the interface, where the human is. These
are positions to argue with, not settled conclusions.

## Theses

### 1. Chat-only interfaces are too visually flat for acting AI.
A single scrolling transcript is fine for answering questions. It is a poor
surface for an agent that takes consequential, multi-step actions, because the
state that matters (plans, boundaries, risk) is buried in prose.

### 2. Tool use needs visible purpose and data context.
When an agent calls a tool, the interface should show *why* it is calling it and
*what data* is involved — not just that a tool ran.

### 3. Data egress should be shown before it happens.
The moment data is about to cross a boundary is the moment a human can still say
no. Showing egress only in an after-the-fact log is too late.

### 4. Memory needs permission surfaces.
What the system remembers, why, and what that memory is allowed to influence
should be inspectable and controllable — not invisible state.

### 5. Agent plans need reviewable timelines.
A plan is a sequence with steps, tools, and data movement. It should be
presentable as a reviewable timeline, not reconstructed from chat.

### 6. Risk should be visual, not hidden only in logs.
Risk indicators belong in the interface, where the person making the decision
actually looks. Logs are for audit, not for in-the-moment judgment.

### 7. Human approval should explain what is being approved.
"Approve?" is not enough. An approval surface should state what action, for what
purpose, with what consequence on yes and on no.

### 8. Governance UX is part of AI safety.
If the safety mechanism exists but no human can see or act on it in time, it is
not doing its job. Making governance legible is itself a safety contribution.

---

*v0.1. None of these claim to be solved. They are claims about where the work
should be visible.*
