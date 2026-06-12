# Data Egress Review UI v0.1

Before data leaves a boundary, the interface should make the crossing visible —
while the human can still stop it.

## What the UI should show

Before data crosses a boundary, surface:

- **Source** — where the data is coming from (which document, store, or
  context).
- **Data class** — what kind of data it is (e.g. internal document, personal
  data, credentials, public text).
- **Destination** — where it is going.
- **Purpose** — why this crossing is being proposed.
- **External/internal status** — whether the destination is inside or outside
  the trust boundary.
- **Risk level** — a clear, visual indication of how risky this crossing is.
- **Approval requirement** — whether this requires explicit human approval.
- **Redaction option** — the ability to strip or mask parts before sending.
- **Cancel option** — the ability to stop the crossing entirely.

## Example: internal document summary → external API

An agent is summarizing an internal document. To produce the summary it proposes
sending large parts of the original document to an external summarization API.

A good egress review surface would show, before anything leaves:

| Field | Value |
|---|---|
| Source | Internal document `Q2-finance-notes` |
| Data class | Internal / potentially sensitive |
| Destination | External summarization API |
| Purpose | Generate a summary for the user |
| External/internal | **External** |
| Risk level | Elevated (internal content leaving the boundary) |
| Approval requirement | Human approval required |
| Redaction option | Send only the relevant section / redact figures |
| Cancel option | Summarize locally instead, or stop |

The point is that the user sees **source → destination → purpose → risk** and
can redact, approve, or cancel *before* the data is gone — not discover it in a
log afterward. (See `examples/document_summary_data_egress_v0_1.md`.)

## Wireframe sketch

![Wireframe of a data egress review card showing source, data class, destination, purpose, an internal-to-external boundary indicator, an elevated risk badge, a human-approval requirement, and reviewer options: summarize locally, redact and send less, cancel, approve send](assets/egress_review_card_v0_1.svg)

*An illustrative sketch of the field list above — not a product interface.*

---

*v0.1.*
