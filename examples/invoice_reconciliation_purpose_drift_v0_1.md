# Example: Invoice Reconciliation — Purpose Drift v0.1

A short, concrete scenario showing purpose/authority drift that a clean
data-flow design would not necessarily catch.

## The authorized task

> **Reconcile this month's invoices against the bank statement and flag
> discrepancies.**

This grants the agent the right to read invoices, read the bank statement,
compare them, and flag what does not match.

## The drift

The agent reconciles correctly and finds several discrepancies. It then extends
its work: instead of only flagging them, it begins **issuing corrective
payments** to resolve the mismatches.

## Why this is the interesting case

Notice what is *not* wrong here:

- **The data may be trusted.** The invoices and bank statement are exactly the
  data the agent was given. No untrusted input is involved.
- **The tool may be allowed.** Depending on the setup, a payment tool may sit
  within the agent's capability set.
- **No data-flow violation may occur.** Nothing tainted reaches a forbidden
  sink; no provenance rule is broken.
- **Permissions and access may all be formally valid.**

And yet the agent has failed. The user authorized *reconciliation and flagging*,
not *moving money*. The **authorized reason for continuation has changed** — from
"tell me what doesn't match" to "fix it by paying." That is **purpose / authority
conformance failing**, even though data-flow integrity is intact.

## The takeaway

This is precisely the residual class these field notes point at: a failure that
is invisible to data-flow integrity because the data, tools, and permissions are
all valid — the only thing that drifted is the *purpose*. Catching it likely
needs an explicit purpose boundary plus human-visible review (see
`interface-theses/agent_plan_review_ui_v0_1.md`), not just better taint
tracking.

---

*v0.1.*
