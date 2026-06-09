# AGF Field Notes

AGF (Agent Governance Framework) is an early, public collection of field notes
and interface theses around agentic AI governance. It is a place to think out
loud about where today's agent-security guarantees stop and what providers and
interface designers might build next.

## What this repository is

- Early-stage public field notes — work in progress, version `v0.1`.
- An exploration of agentic AI governance: purpose/authority conformance,
  data-flow boundaries, governed data transitions, memory/RAG trust separation,
  and tool/runtime boundaries.
- A set of interface and UX theses about making governance visible in AI
  products.
- A competence and field-literacy signal: notes that try to map the problem
  space honestly, including the parts that are already well covered by existing
  research.

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

**Start here:**
[`field-maps/agf_field_map_purpose_drift_v0_1.md`](field-maps/agf_field_map_purpose_drift_v0_1.md)
— the core field map on purpose drift.

- `field-maps/` — maps of where deterministic agent security stops and how AGF's
  residual hypothesis relates to existing systems (CaMeL, FIDES, MVAR).
- `provider-opportunities/` — provider-facing idea map across ten opportunity
  areas.
- `interface-theses/` — theses on governance UX, adaptive workspaces, data
  egress review, memory control, and agent plan review.
- `examples/` — short concrete scenarios (purpose drift, data egress).
- `checklists/` — a practical agentic governance review checklist.

## External-safe boundary

This repository deliberately contains external-safe material only. It does not
reference or describe any private system, internal codenames, or protected
mechanisms. The boundary note in `NOTICE.md` applies here. Everything in this
folder is intended to be readable by external providers, researchers, and
reviewers.

## Feedback

Feedback and corrections are welcome — especially where these notes overstate,
misattribute, or duplicate existing research. The goal is an honest map, not a
pitch. If something here is wrong or already solved elsewhere, please say so.
