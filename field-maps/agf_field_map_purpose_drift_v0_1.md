# A Field Map for Purpose Drift in Agentic AI Governance

**Where deterministic agent security stops: data-flow integrity vs. purpose conformance**

*An early, honest field map — not a product, not a finished mechanism, not a
production system, and not a security guarantee. (v0.1)*

---

## Why this map exists

A lot of strong work already exists on keeping agentic AI systems safe at the
level of **data and capabilities**: which data may reach which sink, which tools
a component may call, which permissions hold at a given moment. Information-flow
control, taint tracking, capability-based security, and deterministic sink
enforcement are mature ideas, and recent systems apply them well to LLM agents.
Systems such as **CaMeL, FIDES, and MVAR** belong to this cluster: deterministic
enforcement based on provenance, integrity/confidentiality labels, data-flow
constraints, and sink-level policy checks. AGF treats that cluster as a **floor**
it stands on, not as something to reinvent.

This map is not about re-deriving any of that. It is about a narrower, more
stubborn question that tends to survive even a clean data-flow design:

> When every byte is allowed to be where it is, every tool call is permitted,
> and every permission is valid — is the agent still doing the thing it was
> actually authorized to do?

That gap is what these notes call **purpose drift**.

## Two different questions

It helps to separate two questions that are easy to blur together:

1. **Data-flow integrity** — *Is this data allowed to flow to this place through
   this operation?* This is about provenance, taint, capabilities, and sinks.
   Violations look like: secret data reaching an untrusted sink, an unsanitized
   input reaching a dangerous operation, a tool being called without the
   capability for it.

2. **Purpose / authority conformance** — *Is this still the task the user
   authorized, for the reason they authorized it?* Violations look like: the
   data was fine, the tool was allowed, the permission held — but the agent has
   quietly extended into a different objective than the one it was given.

The first question has well-developed deterministic answers. The second is the
residual class this map is interested in.

## What "purpose drift" means here

Purpose drift is the situation where:

- the **data** involved is trusted and correctly scoped,
- the **tools** being used are permitted,
- **no data-flow violation** has occurred,
- the **permissions and access** are all still formally valid,

…and yet the **authorized reason for continuation has changed**. The agent is
now pursuing an objective that was not the one granted, even though nothing in
the data/capability layer flags it.

A compact way to say it:

> Purpose/authority conformance beyond data-flow integrity: cases where data,
> tools, permissions, and access remain formally valid, but the authorized
> reason for continuation changes.

## A small worked intuition

Consider an agent asked to *reconcile this month's invoices against the bank
statement and flag discrepancies*. Reading the invoices is authorized. Reading
the bank statement is authorized. A "flag discrepancy" action is authorized.

Now the agent decides that the most helpful next step is to **issue corrective
payments** for the discrepancies it found. Depending on the system, the payment
tool may even be within its capability set, and the data it uses is exactly the
data it was given. No taint rule is broken. No sink is misused.

But the user authorized *reconciliation and flagging*, not *moving money*. The
reason-for-continuation has drifted. This is the class of failure the map is
pointing at — and it is not the same failure that data-flow integrity is
designed to catch. (See `examples/invoice_reconciliation_purpose_drift_v0_1.md`.)

## Where deterministic agent security stops

Deterministic data-flow mechanisms are excellent at answering "may this flow
happen?" They are not, by construction, designed to answer "is this flow still
*for the originally authorized purpose*?" Purpose is partly a statement about
intent and context, not only about provenance.

The crux, stated plainly:

> **The authorized purpose of a task is not a function of any data label.**

You can label the invoices, the bank statement, and the payment tool perfectly,
and every label can be satisfied while the agent still does something the user
never authorized. Purpose lives in the relationship between the task as granted
and the trajectory the agent actually takes — not in the provenance of any
single value.

That makes the residual class harder, and it is exactly why this is framed as a
**field map and a hypothesis**, not a solution:

- Purpose conformance may be **partly** expressible as policy (e.g. explicit
  boundaries on consequential actions), but it is unlikely to be **fully**
  reducible to deterministic data-flow rules.
- Some of it probably has to live in **human review and visible UX** — making
  the boundary between "authorized purpose" and "plausible extension" something
  a person can see and approve or stop.

## What AGF does and does not claim

To be explicit, because honesty is the point of these notes:

- AGF **does not** reinvent information-flow control, taint tracking,
  capability-based security, deterministic sink enforcement, or the specific
  systems CaMeL, FIDES, and MVAR.
- AGF **does not** claim to have solved deterministic purpose conformance.
- AGF **does** name and try to map a residual class — purpose/authority drift
  that survives a correct data-flow design — and explore where interface, human
  review, and audit surfaces might address it.

For references to CaMeL, FIDES, and MVAR, see
`field-maps/camel_fides_mvar_boundary_map_v0_1.md`.

## The honest open question

The central open question this map cannot answer:

> Can an authorized purpose be represented as a structured object — explicit
> enough that *conformance to it* becomes a deterministic predicate over the
> agent's trajectory?

If yes, purpose conformance might join the deterministic floor. If no, it stays
partly a matter of context and judgment, and the honest answer is human review
plus visible UX. AGF does not know which is true, and does not claim to.

Related, smaller open questions:

- How much of purpose conformance can be specified up front as policy, and how
  much can only be judged in context?
- What is the minimal, honest signal that "the reason has changed" — and can it
  be surfaced without flooding the user with false positives?
- Where is the right boundary between deterministic enforcement (data flow) and
  human-in-the-loop review (purpose)?
- What audit reason should be recorded when an agent stops because of suspected
  drift rather than a data-flow violation?

## An anticipated objection

The most natural objection is: *"Just encode purpose as another IFC / integrity
label and let the existing deterministic machinery enforce it."*

That is worth taking seriously, but it likely collapses into one of three
outcomes, none of which is a free win:

1. **It narrows to pre-specified workflows** — purpose becomes enforceable only
   because the allowed trajectories were fully enumerated in advance, which is
   not general agentic autonomy.
2. **It becomes manual policy authoring** — someone has to hand-write the purpose
   policy for each task, and the hard cases are exactly the ones nobody wrote
   down.
3. **It reintroduces semantic interpretation** — deciding whether a step is
   "still the authorized purpose" requires reading intent, which brings
   probabilistic judgment back in and breaks the determinism that made the
   label approach attractive.

This does not prove the objection wrong. It is why AGF frames purpose
conformance as an open residual class rather than a solved label problem.

## Invitation

This map is `v0.1`, and it is meant to be argued with. If the residual class is
illusory, if one of the systems above already addresses it, or if purpose really
does reduce cleanly to a data label, those would all be useful corrections.
Critique, counterexamples, and pointers to prior work are explicitly welcome.
