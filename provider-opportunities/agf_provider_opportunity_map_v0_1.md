# AGF Provider Opportunity Map v0.1

A provider-facing idea map: where governance for agentic AI could turn into
concrete product surfaces. These are openings to explore, not specifications and
not claims that any of them are solved.

## Purpose

To sketch, honestly and at a high level, where AI providers might invest to make
agentic systems more governable — across execution, purpose, data flow, memory,
tools, human review, audit, intake, interface, and ethics. The aim is to be
useful to someone building these products, not to pitch a finished design.

## How to read this map

- Each area lists a **Problem**, a **Provider opportunity**, an **Example
  feature**, and an **Open question**.
- "Opportunity" means *plausible place to build*, not *validated requirement*.
- Several areas overlap deliberately; governance is not cleanly separable.
- Nothing here claims to solve deterministic purpose conformance. Where an area
  touches purpose/authority, treat it as a residual class to be reduced, not
  closed.

## Opportunity areas

### 1. Agent execution governance
- **Problem:** Agents take multi-step actions where each step is locally
  reasonable but the trajectory is hard to supervise.
- **Provider opportunity:** First-class run-level controls — pause, step,
  bound, and roll back agent execution.
- **Example feature:** A run console that lets an operator halt an agent between
  steps and inspect what it is about to do.
- **Open question:** What is the right granularity of a "step" for human
  oversight without making agents unusable?

### 2. Purpose / authority conformance
- **Problem:** Data, tools, and permissions can all be valid while the agent
  drifts to a different authorized reason than the one it was given.
- **Provider opportunity:** Surfaces that capture the original authorized
  purpose and check ongoing actions against it.
- **Example feature:** An "outside original purpose" warning when a plan extends
  beyond the granted task.
- **Open question:** How much of purpose can be specified up front vs. judged in
  context — and who judges?

### 3. Data flow & egress control
- **Problem:** Agents move data across boundaries (internal → external) in ways
  users do not see until after the fact.
- **Provider opportunity:** Pre-egress review surfaces and policy hooks.
- **Example feature:** A confirmation that shows source, data class,
  destination, and risk before data leaves a boundary.
- **Open question:** How to keep egress review informative without training
  users to click through it reflexively?

### 4. Memory / RAG trust separation
- **Problem:** Retrieved or remembered content can quietly influence — or appear
  to authorize — actions.
- **Provider opportunity:** Trust tiers for memory and retrieved context, with
  clear limits on what they may influence.
- **Example feature:** Memory entries tagged with whether they may inform tone,
  context, recommendations, or (by default, no) actions.
- **Open question:** How to let memory be genuinely useful while keeping it from
  becoming an implicit authority channel?

### 5. Tool & runtime boundary control
- **Problem:** Tool access tends to be coarse; "can call this tool" rarely
  encodes "for this reason, in this context."
- **Provider opportunity:** Context- and purpose-scoped tool grants.
- **Example feature:** Tool permissions that carry the task context they were
  granted under, and re-prompt when context changes.
- **Open question:** How to express purpose-scoped grants without a combinatorial
  explosion of policy?

### 6. Human review / escalation
- **Problem:** When agents should ask a human, the ask is often unclear or
  poorly timed.
- **Provider opportunity:** Structured escalation with enough context to decide.
- **Example feature:** An approval card that states what is being approved, why,
  and what happens on yes/no.
- **Open question:** What signals should trigger escalation, and how to avoid
  both under- and over-escalating?

### 7. Audit & explainable stop reasons
- **Problem:** "The agent stopped" or "the agent acted" is hard to explain after
  the fact.
- **Provider opportunity:** Recorded, human-readable reasons for stops,
  continuations, and approvals.
- **Example feature:** An audit log entry like "stopped: action outside
  authorized purpose (issuing payments not part of reconcile task)."
- **Open question:** What is the minimal reason vocabulary that is both honest
  and machine-consistent?

### 8. AI-assisted responsible innovation intake
- **Problem:** New agent capabilities ship faster than anyone reviews their
  governance implications.
- **Provider opportunity:** An intake surface that helps teams reason about
  governance before launch.
- **Example feature:** A guided checklist that flags purpose, egress, and memory
  risks for a proposed capability.
- **Open question:** How to make responsible-innovation intake lightweight
  enough that teams actually use it?

### 9. Interface personalization and adaptive workspace UI
- **Problem:** Acting AI is mostly shown through flat chat, which underserves
  governance and focus.
- **Provider opportunity:** Adaptive workspaces that adapt to project, mode, and
  user — while keeping authority and risk visible.
- **Example feature:** Project-themed workspaces with modes (focus, creative,
  technical, night-shift) that never hide governance state.
- **Open question:** How to personalize without letting aesthetics obscure risk?

### 10. Ethics / responsible governance layer
- **Problem:** Governance can become a checkbox rather than a practice.
- **Provider opportunity:** An explicit ethics/governance layer that is visible
  to users and reviewable.
- **Example feature:** A standing "what this agent may and may not do, and why"
  panel tied to the current task.
- **Open question:** How to keep an ethics layer concrete and honest rather than
  performative?
