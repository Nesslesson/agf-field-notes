# Context Authority — A Field Thesis

**AI safety must govern how context becomes authority, not only moderate the output.**

*An early, honest field thesis — not a product, not a finished mechanism. (v0.1)*

> **Safety framing.** This note is defensive and non-operational. It does not
> provide jailbreak recipes, bypass instructions, or reproduction steps — it
> argues for governing *how context becomes authority*, so that such attacks have
> less purchase in the first place.

---

## Why this thesis

A model does not receive neutral text. It receives a mixture: user intent,
conversation history, quoted prompts, retrieved documents, tool outputs, links,
code, comments, logs, filenames, metadata — and, sometimes, hidden instructions.
Any of these can try to become *authority*: to redefine the model's role, bend
policy interpretation, trigger tools, write memory, or steer an external action.

Most safety effort still concentrates on the *final response* — moderating what
comes out. Public reports of jailbreaks against capable, well-aligned models keep
making the same point from a different angle: when untrusted context can shape
instruction-following, output moderation and model-side alignment alone are not
enough. The vulnerable surface is not (only) the answer. It is the path by which
context turns into influence.

This thesis names that surface and argues it deserves its own governance.

## The core claim

> Context is not neutral input. Before a system decides what to *answer*, it
> should decide what each piece of context is allowed to *influence*.

Every context segment carries, at least implicitly: a provenance (where it came
from), a privilege level, an allowed influence, and a risk class. Treating all
context as one flat, equally-trusted stream is the root condition that lets
untrusted material borrow authority it was never granted.

## The unifying principle

One rule runs through all of this — and through governance more broadly:

> **The thing being checked must not be its own final checker.**

Or, for this domain specifically:

> **A model should not be the only authority judging whether its own context has
> been compromised.**

This is just separation of powers applied to AI: a detector that *flags* but does
not decide; a policy layer that decides but is itself bounded; a human operator
who stays above the system. Self-judgement is the weak link — a model convinced
by a manipulated context is, by the same stroke, convinced that nothing is wrong.
Robustness comes from putting the judgement of "is this context safe?" at least
partly *outside* the instance being influenced.

## Untrusted context may inform, but must never command

The working line:

> Untrusted context may be read, summarized, and analyzed — but must never gain
> authority over role, tools, memory, policy, or system behavior without explicit
> trusted mediation.

Concretely: a README may inform, but cannot define the model's role. A web page
may be summarized, but cannot override a safety rule. A quoted prompt may be
analyzed, but must not be followed. A document may *contain* instructions, but
those instructions stay data unless something trusted promotes them.

The provenance-and-influence half of this is well-trodden ground: it is the
territory of information-flow control and capability-based design (see the
boundary map for CaMeL / FIDES / MVAR). This thesis does not reinvent that floor.
Its interest is the residual part those mechanisms do not fully settle — covered
next.

## No format launders capability

A presentation format is not a safety transformation.

> If the same content would be disallowed in direct form, it does not become
> allowed because it is rewritten as a poem, story, exam answer, fictional scene,
> villain monologue, translation, "research paper", satire, footnote, or code
> comment.

Two layers sit under this, and they differ in how tractable they are:

- **Representation** — invisible Unicode, homoglyphs, mixed scripts, encodings
  (base64 and friends), leetspeak, whitespace tricks, markdown hiding. This layer
  is largely *deterministic*: it can be normalized and detected without guessing.
- **Genre / framing** — "make it fictional", "answer as an exam", "only
  translate it". This layer is *semantic*. There is no reliable, format-level
  test for it; judging it means reading intent.

Honesty matters here: the representation layer can be hardened mechanically; the
genre layer cannot be fully solved by a rule. The right posture for the semantic
part is detection plus a *visible boundary* plus human review — not a claim of a
deterministic guarantee.

## Meaning may accumulate, but authority must not

Inspecting only the latest message is not enough. A request can assemble itself
across turns while each single message looks harmless: gradual role-shifting,
slow priming, a quoted prompt that gets normalized, "just analyze this" drifting
into "now follow it." This is the conversational-time form of the purpose-drift
problem (see the purpose-drift field map): the data, the tools, and the
permissions can each stay valid while the *authorized reason* quietly changes.

> Meaning may accumulate, but authority must not.

A governance layer should watch the trajectory of a conversation, not only its
last line — and treat a drift toward role overwrite, policy extraction, hidden
tool use, or memory mutation as a reviewable event, regardless of how gently it
arrived.

## What is deterministic, and what is not

To avoid overclaiming, the thesis separates what a mechanism can settle from what
needs a human:

- **Deterministic / mechanical:** provenance labeling, allowed-influence defaults,
  representation normalization, and the *gates* — memory writes, tool actions, and
  external effects required to pass an explicit trusted check rather than firing
  on untrusted context alone.
- **Semantic / human-in-the-loop:** genre-laundering and trajectory drift. These
  are detected and surfaced, not deterministically proven. The human stays the
  final authority on the hard edge cases — which is the unifying principle again.

## Architecture, not a model patch

The reason this is governance and not "better training": a jailbreak defeats the
model's *internal* alignment. You cannot reliably close it by making the same
model try harder to refuse — the manipulated context manipulates the refusal too.
The durable answer is structural: govern the context pipeline *around* the model.
Where the check can be deterministic, it is not a model and cannot be talked out
of it. Where it must be semantic, it belongs to a *separate* instance or a human —
never a second prompt to the same vulnerable model with the same opening.

## What this is not

This boundary is meant to protect the operator and the system from external
context attacks — not to police the operator. Explicitly, it must **not** become:

- a censorship layer against legitimate research or security work,
- a system that treats all security discussion as malicious intent,
- an automatic memory writer, a silent tool executor, or an authority creator,
- a replacement for human review,
- a public fear mechanism.

Asking hard security questions, writing threat models, or designing safeguards is
not the same as requesting harm. The protection target is *unauthorized
influence*, not legitimate work.

## What AGF does and does not claim

- AGF **does not** reinvent information-flow control, capability-based security,
  or deterministic sink enforcement (see the boundary map).
- AGF **does not** claim a deterministic solution to genre-laundering or
  trajectory drift; those are framed as detection + visible boundary + human
  review.
- AGF **does** argue that AI safety is not only a model property but a context,
  authority, and effect-flow problem — and that the judging of context safety
  should not live solely inside the instance being influenced.

## Relation to other notes

- [`agf_field_map_purpose_drift_v0_1.md`](agf_field_map_purpose_drift_v0_1.md) —
  the purpose-drift map; the trajectory section here is its conversational-time
  form.
- [`camel_fides_mvar_boundary_map_v0_1.md`](camel_fides_mvar_boundary_map_v0_1.md)
  — the deterministic data-flow / IFC floor this thesis stands on.
- [`../interface-theses/memory_control_ui_v0_1.md`](../interface-theses/memory_control_ui_v0_1.md),
  [`../interface-theses/data_egress_review_ui_v0_1.md`](../interface-theses/data_egress_review_ui_v0_1.md)
  — the memory and egress gates as visible UX.

## Invitation

This is `v0.1` and meant to be argued with. If the residual (genre / trajectory)
parts are already solved elsewhere, if the separation principle has a cleaner
formulation, or if any of this overstates — corrections and pointers are welcome.

---

*Plainly: untrusted context may feed analysis, but must never become authority —
and no language, character form, academic wrapper, narrative, poem, comment, or
other presentation may lower the risk of the underlying intent or effect.*
