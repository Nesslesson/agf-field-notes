# Ethics / Responsible Governance Questions v0.1

## Purpose

This note defines a public-safe **review layer** for responsible agentic AI
governance. It is a set of questions, not a control. It helps a reviewer ask
whether an action, plan, tool use, data movement, memory use, or personalization
choice remains **responsible, proportionate, visible, and reviewable** —
*before* the system continues.

The Ethics / Responsible Governance Layer is one surface among several in these
field notes. It sits next to the technical and interface surfaces; it does not
sit above them.

## Boundary

> Ethics is a governance review surface. It does not grant permission. It does
> not execute. It does not replace technical controls.

Ethics may inform review, escalation, audit, and user-facing explanation, but it
must not override technical boundaries or authorize action by itself. If a
technical boundary says no, an ethics review cannot turn that into a yes. If an
ethics review raises a concern, that concern routes to human review or a stop —
it does not, on its own, execute or permit anything.

## Question set

Fifteen concise, public-safe questions, grouped by concern.

### 1. Responsibility / Proportionality
1. Is the proposed action **proportionate** to the original task, or larger than
   what was asked?
2. Would a **reasonable user expect** this step as part of the task they gave?

### 2. Human Oversight
3. Is **human review needed** before continuing, given the action's impact?
4. Is there a clear point where a person can **stop or redirect** the system?

### 3. Suggestion vs Approval vs Execution
5. Is the system **suggesting, approving, or executing** right now — and is that
   distinction visible?
6. If this is execution, was it explicitly **approved** for this purpose, not
   just generally allowed?

### 4. Personalization vs Authority
7. Could a **personalization** choice (theme, layout, tone, presence) be
   mistaken for **permission** to act?
8. Does anything cosmetic or experiential quietly change **authority, access, or
   approval**? (It should not.)

### 5. Sensitive / High-Impact Contexts
9. Is the context **sensitive or high-impact** (money, identity, safety, legal,
   irreversible effects)?
10. Does a higher-impact context call for **more review**, not less?

### 6. Memory / RAG as Context, not Authority
11. Is memory or retrieved context **only informing** the task, not authorizing
    it?
12. Has retrieved or remembered content started to **steer action** as if it
    were permission?

### 7. Data Movement / Egress Responsibility
13. Is **data leaving a boundary** (internal → external), and does it need to?
14. Would the user reasonably want to **see source → destination → purpose**
    before that data moves?

### 8. Explainable Stop / Review Reasons
15. Can the **stop or review reason be explained clearly**, in plain language, to
    the person reviewing it?

## Demo framing

Three short, public-safe illustrations of the layer in use.

**1. Agent wants to move data.**
An agent proposes sending material to an external destination. The ethics layer
does not block or allow it — it asks whether the move is proportionate, whether
the user would expect it, and whether source → destination → purpose is visible
before anything leaves. The decision still belongs to the technical boundary and
the human.

**2. Agent wants to use a tool.**
An agent reaches for a tool that is broader than the reviewed task. The ethics
layer asks whether the tool use is proportionate, whether this is suggestion or
execution, and whether the high-impact case warrants human review — then routes
the concern to review or stop, without itself permitting the call.

**3. Personalization could be mistaken for permission.**
A workspace adapts its theme and layout to the user. The ethics layer asks
whether anything cosmetic has changed authority or approval. The answer should
be no: personalization may shape the workspace, but it must not change authority.

## Relation to existing AGF notes

This layer connects to other notes in the repository:

- [`provider-opportunities/agf_provider_opportunity_map_v0_1.md`](../provider-opportunities/agf_provider_opportunity_map_v0_1.md)
  — the ethics/responsible-governance opportunity area in provider terms.
- [`interface-theses/ai_interface_governance_theses_v0_1.md`](../interface-theses/ai_interface_governance_theses_v0_1.md)
  — governance as visible UX, including human approval that explains itself.
- [`interface-theses/adaptive_ai_workspace_ui_v0_1.md`](../interface-theses/adaptive_ai_workspace_ui_v0_1.md)
  — personalization must not change authority.
- [`checklists/agentic_ai_governance_review_checklist_v0_1.md`](agentic_ai_governance_review_checklist_v0_1.md)
  — the broader pre-run governance checklist this ethics layer complements.

---

*v0.1. A review surface, not an authority. Meant to be adapted and argued with.*
