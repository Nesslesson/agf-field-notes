# AGF Field Notes

AGF (Agent Governance Framework) is an early, public collection of field notes
and interface theses around agentic AI governance. It is a place to think out
loud about where today's agent-security guarantees stop and what providers and
interface designers might build next.

## In one minute

AGF (Agent Governance Framework) is a public field-notes project about one question:

> If an AI agent can use tools, move data, read memory, and act across workflows, how do we keep its actions aligned with the purpose the user actually authorized?

These notes explore agentic AI governance beyond plain chat: purpose/authority conformance, data-flow and egress boundaries, memory/RAG trust separation, visible governance UX, adaptive workspace interfaces, and responsible governance review.

AGF does not claim to be a finished system. It is an early map of problem classes, provider opportunities, and interface theses for critique. (The "Framework" in the name is aspirational — nothing here claims framework status yet.)

## Quick navigation

- Start with the core field map: [`field-maps/agf_field_map_purpose_drift_v0_1.md`](field-maps/agf_field_map_purpose_drift_v0_1.md)
- Read the Context Authority thesis — governing how context becomes authority, not only moderating output: [`field-maps/agf_context_authority_thesis_v0_1.md`](field-maps/agf_context_authority_thesis_v0_1.md)
- Compare the boundary against CaMeL / FIDES / MVAR: [`field-maps/camel_fides_mvar_boundary_map_v0_1.md`](field-maps/camel_fides_mvar_boundary_map_v0_1.md)
- See how purpose drift relates to scope creep, goal misgeneralization, instruction hierarchies, and principal–agent framing: [`field-maps/agf_adjacent_concepts_and_scope_boundary_v0_1.md`](field-maps/agf_adjacent_concepts_and_scope_boundary_v0_1.md)
- Browse provider-facing opportunities: [`provider-opportunities/agf_provider_opportunity_map_v0_1.md`](provider-opportunities/agf_provider_opportunity_map_v0_1.md)
- Read the interface theses: [`interface-theses/ai_interface_governance_theses_v0_1.md`](interface-theses/ai_interface_governance_theses_v0_1.md)
- Read the adaptive workspace note: [`interface-theses/adaptive_ai_workspace_ui_v0_1.md`](interface-theses/adaptive_ai_workspace_ui_v0_1.md)
- Read the ethics questions: [`checklists/ethics_responsible_governance_questions_v0_1.md`](checklists/ethics_responsible_governance_questions_v0_1.md)

## Why this matters

Most AI interfaces still look like chat boxes, even when the systems behind them can call tools, move data, use memory, and affect workflows. If AI systems become more agentic, governance should become visible in the product surface: what the agent is trying to do, what data it may move, which tools it wants to use, when human review is needed, and why a step should be stopped or allowed.

## Working terms

- **Purpose / authority conformance** — whether an agent's continuation still matches the purpose the user actually authorized, even when data, tools, and permissions remain formally valid.
- **Data-flow / egress boundaries** — where data may move, and making any crossing (especially internal → external) visible before it happens.
- **Memory / RAG trust separation** — remembered or retrieved content may inform a task, but must not act as permission.

The Ethics / Responsible Governance Layer asks review questions; it does not authorize action.

## What this repository is

- Early-stage public field notes — work in progress, version `v0.1`.
- An exploration of agentic AI governance: purpose/authority conformance,
  data-flow boundaries, governed data transitions, memory/RAG trust separation,
  and tool/runtime boundaries.
- A set of interface and UX theses about making governance visible in AI
  products.
- An attempt to map the problem space honestly, including the parts that are
  already well covered by existing research.

## What this repository is not

- Not a product and not production-ready.
- Not a security guarantee and not a finished mechanism.
- Not affiliated with any referenced project, company, or organization. See `NOTICE.md` for the current boundary note.
- Not a claim to have solved deterministic purpose conformance. AGF identifies a
  residual class of problems; it does not claim to have closed it.
- Not a disclosure of any private architecture, implementation logic, or
  protected mechanism.

## Core themes

1. **Purpose / authority conformance** — cases where data, tools, permissions,
   and access remain formally valid, but the authorized *reason* for continuation
   changes.
2. **Data-flow boundaries & egress** — when and why data crosses a boundary, and
   how to make that visible before it happens.
3. **Memory / RAG trust separation** — memory may inform, but should not
   authorize.
4. **Tool & runtime boundaries** — what an agent may touch, and under what
   reason.
5. **Governance as visible UX** — risk, plans, and approvals as first-class
   interface elements, not log lines.

## Current notes

- `field-maps/` — maps of where deterministic agent security stops, how AGF's
  residual hypothesis relates to existing systems (CaMeL, FIDES, MVAR), how
  purpose drift relates to adjacent public concepts, and a thesis on governing
  context authority (how context becomes authority, not only model output).
- `provider-opportunities/` — provider-facing idea map across ten opportunity
  areas.
- `interface-theses/` — theses on governance UX, adaptive workspaces, data
  egress review, memory control, and agent plan review, with wireframe sketches
  for the egress, plan-review, and memory-control surfaces.
- `examples/` — short concrete scenarios: purpose drift in invoice
  reconciliation, an email/calendar assistant, and a research assistant, plus a
  data-egress case.
- `checklists/` — a practical agentic governance review checklist, plus an
  Ethics / Responsible Governance review surface.

## External-safe boundary

This repository deliberately contains external-safe material only. It does not
reference or describe any private system, internal codenames, or protected
mechanisms. The boundary note in `NOTICE.md` applies here. Everything in this
folder is intended to be readable by external providers, researchers, and
reviewers.

## How these notes were made

These notes were written in dialogue with AI assistants — used as tools, the
way one uses any powerful tool: directed, reviewed, and bounded. The questions,
the judgments, the boundaries, and the mistakes are mine.

Writing about agentic AI governance while using AI assistants under explicit
boundaries is not a contradiction; it is the practice these notes describe.
Saying so plainly seemed more honest than leaving it unsaid.

## License

Unless otherwise noted, the original prose notes, field maps, checklists, and examples in this repository are licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

## Feedback

Feedback and corrections are welcome — especially where these notes overstate,
misattribute, or duplicate existing research. The goal is an honest map, not a
pitch. If something here is wrong or already solved elsewhere, please say so.

The simplest door: **open a GitHub issue** on this repository — for critique,
counterexamples, corrections, or pointers to prior work. No formality needed;
one-line issues are welcome.
