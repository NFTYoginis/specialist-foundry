# Stage 2 — PLAN

**Surface architecture in conversation, BEFORE writing files.** Arjen's "CONFIRM" stage renamed — what actually happens here is *planning* plus confirmation, not pure confirmation.

## What happens

1. **Identify the closest analog repo** from the source-repos catalogue. State which and why.
2. **Propose folder + file tree** in conversation, not as files yet.
3. **State key patterns being applied** with citations:
   - "Empty-region rule lifted in shape from Your Market Realtor `specialist/rules.md:57-63`, generalized as empty-country handling."
   - "4-column triage shape lifted verbatim from Grief Admin Compass."
   - "5-stage workflow naming lifted from Arjen's Specialist Builder."
4. **List open questions if any** — file-level questions that don't justify a question file but need operator input (slug choice, scope-boundary detail, etc.)
5. **Flag cost-relevant choices** transparently — WebFetch budget, depth-vs-time tradeoffs.
6. **Get operator sign-off** OR **file a follow-up question** if PLAN surfaces a precondition that didn't show up at CALIBRATE.

## What goes in the plan surface (the conversation message)

| Section | Content |
| --- | --- |
| Closest analog | Which repo, why, what specifically you're lifting (shape, voice, refusal pattern) |
| Slug | The folder name. Operator can override. |
| Folder tree | The full file list under `builds/<slug>/`. Tree format. |
| Refusal gates | Names + counts. Exact language goes in BUILD, not PLAN. |
| Output shape | What the specialist returns (4-column / 3-section / N-step / etc.) |
| Empty-input handling | What happens when the specialist's user gives incomplete input |
| Region/scope handling | If multi-region: which is populated, which is scaffolded, what the empty-region refusal looks like |
| Cost flag | Estimated WebFetch budget, estimated file count, anything else that warrants flagging |
| Open questions | Any |

## Anti-patterns to avoid

- **Writing files during PLAN.** Don't. The plan lives in conversation. Files come in BUILD.
- **Over-planning.** A 2000-word plan is too much. Surface the architecture in 150–300 lines max.
- **Hiding cost.** If WebFetch budget will be high, name it explicitly. Operators prefer the call.
- **Asking for sign-off on every detail.** Sign-off is for the architectural shape and the load-bearing choices. File-level details (which exact citations, which exact bullet wording) come during BUILD.

## Worked example — funeral compass PLAN

```
## Plan — `online-funeral-family-compass` specialist

### 1. Closest analog (cited per rules.md)
Repo #2 — Grief Admin Compass. Direct lift on structural shape: crisis-triage intake, admin-first not emotion-first framing, 4-column TODAY/THIS WEEK/MONTH 1/DON'T-DO-YET output, refusal gates around legal/medical/grief-counseling. Domain swap: estate-admin → online-funeral-family workflow.

### 2. Buyer (operator confirmed: option a)
Bereaved family currently engaging an online funeral service.

### 3. Slug
`online-funeral-family-compass`

### 4. Domain layers — 6 of 8 candidates
[table of 6 ✓ and 2 ⊘ with reasoning]

### 5. Geographic scope — recommend US-only
[reasoning]

### 6. Refusal gates (5)
[table of gates and draft refusal language]

### 7. Output shape
4 prioritized columns: TODAY → THIS WEEK → MONTH 1 → DON'T-DO-YET

### 8. Folder + file tree
[tree]

### 9. Grading bar — operator picked all 3
[how each bar is delivered]

### 10. Cost flag
Domain-accurate bar adds 8–12 WebFetch calls. Flagging transparently. OK to proceed or cap lower?

### 11. docs/index.html section outline
[9-section outline]

## Two things I need before building
1. Sign-off OR override on: slug, the 6 layer pick, US-only scope.
2. WebFetch budget: 8–12 fetches OK, or cap lower?
```

That's a PLAN surface. ~150 lines of conversation. One round-trip with operator. Then BUILD.

## When PLAN surfaces a precondition that CALIBRATE missed

If during PLAN you realize an additional precondition is needed (a scope detail, a depth tradeoff), file a follow-up question file `briefs/questions/<slug>-question-2.md`. Don't try to absorb the question into the plan surface — the audit trail is cleaner if it's a separate file.

---

Last updated: 2026-05-12.
