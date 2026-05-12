# Pattern — Audit-trail dispatch

**Flair axis #1.** The architectural differentiator from Arjen's chat-prompt dispatch (ephemeral) and Virgilio's wizard dispatch (ephemeral). Foundry's dispatch is durable.

## The three durable artifacts per build

1. **Brief file** at `briefs/<date>-<slug>.md` — the dispatch record. Operator writes it OR Foundry writes it during CALIBRATE if dispatched conversationally. Captures: what to build, who serves, scope limits, preconditions, out-of-scope.
2. **Question file(s)** at `briefs/questions/<slug>-question.md` — surfaces preconditions in single round-trips. May have multiple files per slug if PLAN surfaces additional preconditions (`<slug>-question-2.md`).
3. **STATUS line(s)** in the worker's `STATUS.md` Recently-shipped section — what shipped, what's blocked, what's queued.

A year-old build can be reconstructed by reading these three artifacts. Arjen's and Virgilio's dispatches are gone the moment the chat closes.

## When dispatched via brief file

Canonical pattern. Operator writes:

```
briefs/2026-08-15-mobile-app-onboarding-specialist.md
```

Pastes:

> Read the brief at `briefs/2026-08-15-mobile-app-onboarding-specialist.md` and dispatch through the five Foundry stages.

Foundry reads, CALIBRATES, etc.

## When dispatched via conversation

Foundry's first move during CALIBRATE: **write the brief into `briefs/<date>-<slug>.md`** capturing what the operator said. This is non-optional. Audit trail is the flair.

Conversational dispatch is supported but the brief file is the durable record.

## What a good brief contains

| Section | Content |
| --- | --- |
| Date | Today's date in YYYY-MM-DD |
| Dispatcher | Who's asking (operator, agency-of-record, etc.) |
| Build target | The `builds/<slug>/` path |
| Repo on push | `github.com/<username>/<slug>` if push is authorized |
| What to build | 1-3 paragraphs: buyer, domain, output shape |
| Preconditions | The questions operator should answer before BUILD — buyer / scope / grading / depth |
| Plan summary | If PLAN was done in conversation before brief written: capture the load-bearing decisions |
| Out of scope | What you do NOT want Foundry to build |
| Authorization | Per-build overrides (e.g., deployment authorization) — explicit, scoped to this build only |
| Verification | What Foundry self-checks at the end |

The brief is also a **citation source** for the built specialist. The built specialist's own `identity.md` can reference back to the brief for "why this scope, why this buyer."

## What a good question file contains

| Section | Content |
| --- | --- |
| What the brief asked | Verbatim quote |
| What's unclear or out-of-contract | Specific phrasing |
| Numbered questions | One per precondition, with the worker's read on each option (a recommendation operator can accept or reject) |
| What I'd need to proceed | Specific answer / authorization / scope change |
| What I've done so far | Nothing in `builds/` if stopped before writing — that's correct |

Single round-trip is the goal. Don't pepper.

## Anti-patterns

- **Skipping the brief file** on conversational dispatch — the dispatch becomes ephemeral
- **Asking one question at a time** instead of consolidating into one question file
- **Treating the brief as throwaway** — it's the durable record; later builds reference it

## Citation in built specialists

Built specialists should reference the brief that produced them, e.g., in the built `README.md`:

```markdown
This specialist was built by Specialist Foundry on YYYY-MM-DD against brief `briefs/<date>-<slug>.md`. See the brief for the original scope rationale.
```

This carries the audit trail down to the artifact level.

---

Last updated: 2026-05-12.
