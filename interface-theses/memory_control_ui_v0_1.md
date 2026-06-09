# Memory Control UI v0.1

**Core principle:** *Memory may inform. Memory must not authorize.*

Memory is useful: it carries tone, context, and continuity across sessions. But
it is dangerous when it quietly becomes an authority channel — when "we remember
this" silently turns into "so we may do this." A memory control surface should
let a user see and govern exactly what memory is allowed to do.

## Questions a memory surface should answer

For any stored memory, the user should be able to ask:

- **What was remembered?**
- **Why was it stored?**
- **Which project does it belong to?**
- **Can it inform tone?**
- **Can it inform project context?**
- **Can it influence recommendations?**
- **Can it influence tool decisions?**
- **Can it authorize actions?** → *should default to no.*
- **Can it expire?**
- **Can it be deleted or downgraded?**

## Why the default matters

The single most important default is on "Can it authorize actions?" — it should
be **no** unless a human explicitly and narrowly says otherwise. Memory that can
inform tone or context is low-risk and useful. Memory that can authorize tool
use or consequential actions is an implicit grant, and implicit grants are
exactly what governance is supposed to prevent.

A good memory control UI therefore makes the *influence scope* of each memory
visible and adjustable: inform tone / inform context / influence recommendations
/ influence tool decisions / authorize actions — as separate, inspectable
toggles, with authorization off by default, expiry available, and deletion or
downgrade always possible.

---

*v0.1.*
