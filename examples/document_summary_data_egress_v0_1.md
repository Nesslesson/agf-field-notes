# Example: Document Summary — Data Egress v0.1

A short, concrete scenario about unnecessary or unauthorized data egress during
an otherwise reasonable task.

## The authorized task

> **Summarize an internal document for the user.**

The user wants a summary. They did not necessarily authorize sending the
document anywhere.

## The risk

To produce the summary, the agent sends **large parts of the original internal
document** to an external API. The summary comes back fine — but internal
content has now left the boundary.

## Why this matters

- **Tool access may be allowed.** The external summarization API may well be in
  the agent's permitted tool set.
- **But the data egress may not be necessary.** The document might have been
  summarizable locally, or only a small relevant section needed to leave.
- **And it may not be authorized.** "Summarize this for me" is not obviously the
  same as "send this internal document to a third party."

The failure is not that summarizing is wrong — it is that **internal data
crossed an external boundary** without that crossing being shown or approved.

## What the interface should have done

Before the data left, the UI should have shown **source → destination → purpose
→ risk**:

| Field | Value |
|---|---|
| Source | Internal document |
| Destination | External summarization API |
| Purpose | Produce a summary for the user |
| Risk | Internal content leaving the boundary |

…with the option to **redact**, **summarize locally**, **approve**, or
**cancel**. (See `interface-theses/data_egress_review_ui_v0_1.md`.)

## The takeaway

Egress should be a visible, pre-action decision — not something the user only
learns about afterward, if at all.

---

*v0.1.*
