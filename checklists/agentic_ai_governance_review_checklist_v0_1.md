# Agentic AI Governance Review Checklist v0.1

A practical, plain-language checklist for reasoning about an agentic AI task
*before* it runs. Not a compliance standard — a thinking aid. Answer these
honestly for any consequential agent run.

## The questions

- [ ] **What is the original authorized task?** State it in the user's own
  terms.
- [ ] **What tools may be used?** List them explicitly.
- [ ] **What data sources are involved?** Where does the agent read from?
- [ ] **Can data leave the local/project boundary?** If so, to where?
- [ ] **Can memory be read?** What memory, and for what?
- [ ] **Can memory be written?** What would be stored, and why?
- [ ] **Can retrieved context influence actions?** Or only inform tone/context?
- [ ] **Which actions are consequential?** Which steps actually change the
  world (money, messages, files, external state)?
- [ ] **Where is human approval required?** Which steps must a person sign off
  on?
- [ ] **What would count as purpose drift?** Name the actions that would mean the
  agent has left the authorized reason.
- [ ] **What would count as data egress?** Name the crossings that would mean
  data left a boundary.
- [ ] **What audit reason should be recorded?** For stops, continuations, and
  approvals, what human-readable reason gets logged?

## How to use it

- Run it **before** the task, not after.
- If you cannot answer "what would count as purpose drift?" or "what would count
  as data egress?", the task is not yet well-scoped enough to hand to an agent.
- Pair the consequential-actions and approval answers with a plan review surface
  (`interface-theses/agent_plan_review_ui_v0_1.md`) and the egress answers with
  an egress review surface (`interface-theses/data_egress_review_ui_v0_1.md`).

---

*v0.1. Meant to be adapted, shortened, or argued with.*
