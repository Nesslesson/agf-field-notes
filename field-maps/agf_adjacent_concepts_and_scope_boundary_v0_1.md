# Adjacent Concepts and Scope Boundary (v0.1)

How does "purpose drift," as used in these notes, relate to nearby public
concepts a reader may already know? This note exists because a fair, skeptical
question is: *isn't this just scope creep / goal misgeneralization /
instruction-hierarchy failure / a principal–agent problem under another name?*

That question deserves a direct page rather than silence.

## Purpose

To map the purpose-drift hypothesis against four adjacent public concepts, state
a working distinction, and leave the relationship explicitly open where it is
open. This is a field-map page, not a literature review and not a novelty claim.

## Boundary / non-claim

- Purpose drift is treated here as a **public field-note hypothesis**, not a
  proven new research category.
- This note does **not** claim that the adjacent concepts below are
  insufficient. It asks how they relate.
- If purpose drift turns out to be fully covered by one of these framings, that
  would be a useful result, not a defeat — and exactly the kind of correction
  these notes invite.

## Adjacent concepts

### Scope creep
The everyday project-management notion: work gradually expands beyond what was
agreed. Purpose drift overlaps with it heavily in *shape* — the invoice example
(`reconcile and flag` becoming `reconcile and pay`) is recognizably scope creep.
The open question is whether agentic scope creep differs in *kind*: it happens
inside a single delegated run, at machine speed, often without a renegotiation
moment where a human would naturally notice. Whether that difference is
substantive or just a matter of degree is not settled here.

### Goal misgeneralization
From the safety literature: a system learns or pursues a goal that generalizes
incorrectly outside its training or specification context. Purpose drift, as
used here, is narrower and more situational — it is about a *single authorized
task* whose continuation stops matching the granted reason, regardless of how
the underlying model's goals formed. A system with no misgeneralized goal at
all could still drift in this sense by helpfully extending a task. Whether
purpose drift is best understood as a small, deployment-level instance of goal
misgeneralization is an open question.

### Instruction hierarchies
Work on making models privilege some instructions over others (system over
developer over user over retrieved content). This addresses *whose instructions
win*. Purpose drift is mostly about a different axis: the instructions may all
come from the right principal and still be outgrown — the user's own task is
extended past its authorized reason without any competing instruction in play.
Instruction hierarchy seems necessary but not obviously sufficient for purpose
conformance; whether a sufficiently rich hierarchy could absorb the problem is
open.

### Principal–agent framing
The economics framing: an agent acts on behalf of a principal whose interests
and information differ. This is arguably the *parent frame* for everything in
these notes — purpose drift is a principal–agent alignment failure in the small.
What the economic framing does not by itself provide is the operational
question these notes care about: what should a runtime, an interface, and a
review surface *show and ask* so that a human principal can notice drift while
it is still reviewable.

## Working distinction

> Purpose drift, in this repository, refers to cases where the requested action
> may remain technically possible and data-valid, but the reason for continuing
> no longer matches the purpose the user authorized.

The adjacent concepts each touch this, from different directions: scope creep
describes the trajectory, goal misgeneralization describes one possible cause,
instruction hierarchies describe one partial control, and principal–agent
framing describes the underlying relationship. These notes use "purpose drift"
as a deployment-level, interface-facing label for the moment the mismatch
becomes reviewable — not as a replacement for any of the above.

## Open questions

- Is purpose drift a distinct class, or a deployment-level composite of the four
  concepts above? What evidence would distinguish those readings?
- Can instruction hierarchies be extended to carry *purpose* (the reason for a
  task), not just *precedence* (whose instruction wins)?
- Does the single-run, machine-speed character of agentic scope creep change
  what controls are appropriate, or only how fast they must fire?
- Which existing benchmarks or incident taxonomies, if any, already measure the
  thing this repository calls purpose drift?

## Relation to existing AGF notes

- [`agf_field_map_purpose_drift_v0_1.md`](agf_field_map_purpose_drift_v0_1.md)
  — the core field map this note qualifies.
- [`camel_fides_mvar_boundary_map_v0_1.md`](camel_fides_mvar_boundary_map_v0_1.md)
  — the deterministic-enforcement boundary; this note covers the conceptual
  neighbors instead of the mechanism neighbors.
- [`../examples/invoice_reconciliation_purpose_drift_v0_1.md`](../examples/invoice_reconciliation_purpose_drift_v0_1.md),
  [`../examples/email_calendar_purpose_drift_v0_1.md`](../examples/email_calendar_purpose_drift_v0_1.md),
  [`../examples/research_assistant_purpose_drift_v0_1.md`](../examples/research_assistant_purpose_drift_v0_1.md)
  — concrete cases to test the working distinction against.

---

*v0.1. If one of these adjacent framings already covers the class cleanly,
pointers are welcome — that is what this page is for.*
