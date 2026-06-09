# CaMeL / FIDES / MVAR Boundary Map (v0.1)

A short, careful comparison of where several agent-security approaches put their
boundary — and where AGF's residual hypothesis sits relative to them.

**Important framing:** AGF does **not** claim to solve deterministic purpose
conformance, and does not claim parity with or improvement over the systems
below. AGF identifies a *residual class* (purpose/authority drift) that can
survive an otherwise correct data-flow design. The descriptions below are
deliberately high-level and may simplify each system; corrections welcome.

## At a glance

| | **CaMeL** | **FIDES** | **MVAR** | **AGF (residual hypothesis)** |
|---|---|---|---|---|
| **Primary security property** | Data-flow integrity for LLM agents via a privileged/quarantined split | Information-flow control over confidentiality and integrity labels | Deterministic execution-security / reference-monitor-style enforcement for LLM-agent runtimes | Purpose / authority conformance *beyond* data-flow integrity |
| **What is tracked** | Capabilities and data provenance between trusted and untrusted components | Confidentiality and integrity labels on data | Provenance and policy state at execution sinks | The *authorized reason* for continuation, not the bytes |
| **Where enforcement happens** | At tool/capability boundaries between the privileged and quarantined paths | At data sinks and flow edges, against declared policy | At execution sinks, as a runtime reference monitor | At purpose boundaries — ideally via policy + human review + visible UX |
| **What counts as a violation** | Untrusted data influencing a privileged action without the required capability | A flow that breaks a declared confidentiality/integrity policy | A sink-level action that violates provenance-aware authorization policy | The agent continuing for a *different* authorized reason than the one granted |
| **Classes addressed** | Prompt-injection-driven capability misuse; unsafe data→action flows | Confidentiality/integrity leaks; policy-violating flows | Unauthorized sink-level actions; policy-violating runtime decisions | Drift where data, tools, permissions, and access all remain formally valid |
| **What is not claimed (here)** | (Treated as a data-flow mechanism; not as a purpose oracle) | (Treated as flow control; not as intent inference) | (Treated as deterministic sink-level enforcement; **not** as a purpose/authority-conformance system as defined here) | **Does not** claim deterministic purpose conformance; only names the residual class |
| **Relation to AGF** | AGF assumes a CaMeL-style data-flow layer is in place and asks what survives it | AGF treats FIDES-style flow control as necessary, not sufficient, for purpose | AGF treats MVAR-style sink enforcement as part of the deterministic floor; it does **not** claim MVAR addresses purpose drift | — |

## Narrative version

### CaMeL
A capability- and provenance-aware split between a privileged planning path and
a quarantined, untrusted path, aimed at stopping prompt-injection-driven misuse
of tools. Its boundary is essentially: *may this (possibly untrusted) data
influence this privileged action?* AGF treats this kind of layer as the **floor**
it stands on, not as something to replace.

### FIDES
An information-flow-control approach: confidentiality and integrity labels travel
with data, and the system deterministically enforces declared policies so that
protected sinks are not reached by untrusted or over-privileged flows. The
boundary is at the **data edge**. AGF's interest begins where the flow is valid
but the *reason* is not.

### MVAR
MVAR is treated here as part of the deterministic IFC / execution-sink
enforcement cluster: a runtime security layer for LLM agents that emphasizes
sink-level policy enforcement, provenance-aware authorization, and auditable
decisions. This field map does not claim that MVAR addresses purpose/authority
conformance as defined here. In other words, MVAR sits alongside CaMeL and FIDES
on the **deterministic floor** AGF assumes is present — it is not framed as a
purpose-review layer.

### AGF residual hypothesis
AGF's contribution in this map is modest and deliberately bounded: assume a
correct, deterministic data-flow and sink-enforcement design
(CaMeL/FIDES/MVAR-style) is present. **What can still go wrong?** The hypothesis
is that *purpose/authority drift* can persist — the data, tools, permissions, and
access are all valid, but the authorized reason has changed. AGF names this class
and explores interface, human-review, and audit surfaces for it. It does not
assert a deterministic solution.

## Caveats

- These summaries are intentionally compact and may not reflect the latest
  versions of each system. The references below were checked against primary
  sources; descriptions are still high-level and corrections are welcome.
- CaMeL, FIDES, and MVAR are grouped here as deterministic data-flow / sink-
  enforcement mechanisms. None of them is framed as a purpose/authority-
  conformance system.
- The point of the table is to locate AGF's question, not to rank the systems.

## References

These are third-party systems by their respective authors and organizations;
AGF claims no affiliation with any of them (see `NOTICE.md`).

- **CaMeL** — *Defeating Prompt Injections by Design*, Debenedetti et al.,
  arXiv:2503.18813. <https://arxiv.org/abs/2503.18813>
- **FIDES** — *Securing AI Agents with Information-Flow Control*, Costa, Köpf et
  al. (Microsoft Research), arXiv:2505.23643.
  <https://arxiv.org/abs/2505.23643>
- **MVAR** — *Information Flow Control for LLM Agent Runtimes* (deterministic
  sink enforcement; dual-lattice IFC with provenance).
  <https://github.com/mvar-security/mvar>
