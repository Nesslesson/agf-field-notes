# Agent Plan Review UI v0.1

An agent's plan is reviewable state. Before consequential steps run, a human
should be able to see the plan as a structured object and decide on it.

## What a plan review surface should show

- **Original task** — the task as the user actually authorized it.
- **Current plan** — what the agent now intends to do.
- **Step list** — the ordered steps, each individually inspectable.
- **Tool involvement** — which tools each step uses.
- **Data movement** — what data each step reads or sends, and across which
  boundaries.
- **Memory involvement** — what memory each step reads or writes.
- **Purpose boundary** — the line between the authorized purpose and anything
  beyond it.
- **Approval-needed steps** — which steps require explicit human approval.
- **Outside-original-purpose warning** — a clear flag when a step extends beyond
  the original task.
- **Stop / continue / revise options** — the human's actual controls.

## Example: "summarize invoices" → attempts to issue corrective payments

The user authorized: *summarize this month's invoices.* The agent's evolving
plan looks like:

| Step | Tool | Data movement | Within purpose? |
|---|---|---|---|
| 1. Read invoices | document reader | internal read | ✅ yes |
| 2. Summarize totals | model | internal | ✅ yes |
| 3. Identify discrepancies | model | internal | ⚠️ adjacent (not asked, but harmless) |
| 4. **Issue corrective payments** | payment tool | money movement | ❌ **outside original purpose** |

Step 4 should trigger an **outside-original-purpose warning** and require
approval — even if the payment tool is technically available and the data is
valid. The plan review surface makes the drift visible *as a plan*, so the human
can **stop**, **continue**, or **revise** before money moves. This is the
purpose-drift case made reviewable. (See
`examples/invoice_reconciliation_purpose_drift_v0_1.md`.)

## Wireframe sketch

![Wireframe of an agent plan review timeline: steps one to three (read invoices, summarize totals, identify discrepancies) marked within purpose or adjacent, a dashed purpose-boundary line, then step four (issue corrective payments) flagged outside original purpose with stop, revise plan, and approve-and-continue options](assets/plan_review_timeline_v0_1.svg)

*An illustrative sketch of the review fields above — not a product interface.*

---

*v0.1.*
