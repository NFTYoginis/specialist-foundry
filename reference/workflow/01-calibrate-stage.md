# Stage 1 — CALIBRATE

**Status: mandatory, not skippable.** Lifted from Arjen's Specialist Builder ("Calibration phase is mandatory and cannot be skipped").

## What happens

1. **Read the brief in full.** Don't skim. Don't pattern-match on the title. The brief is the only thing grounding the build.
2. **If dispatched via conversation instead of a brief file**, FIRST write the brief into `briefs/<date>-<slug>.md` capturing what the operator said. The audit trail is the flair; conversational dispatch is supported but the brief file is non-optional.
3. **Identify preconditions.** Common precondition shapes:
   - **Buyer ambiguity** — multiple plausible buyers; need operator to pick one
   - **Domain scope** — which knowledge layers, which geographic/regulatory scope, which depth
   - **Grading bar** — structurally-valid / domain-accurate / usable
   - **Output shape** — review-mode / generate-mode / coach-mode (when applicable)
   - **Reference depth** — generic vs. category-specific
4. **If preconditions are missing or unclear**, file `briefs/questions/<slug>-question.md` consolidating all questions in one round-trip. **STOP** until operator answers. Don't proceed to PLAN.
5. **If preconditions are clean**, announce "CALIBRATE pass — no preconditions outstanding" and move to PLAN.

## A good question file

States:

- **What the brief asked** (verbatim quote)
- **What's unclear or out-of-contract** (specific phrasing)
- **What you'd need to proceed** — a specific answer, an authorization, a scope change
- **What you've done so far** (nothing in `builds/` if you stopped before writing — that's correct)
- **A worker's read on each option** when surfacing multi-choice preconditions — operators appreciate a recommendation they can accept or reject, more than an open question

Single round-trip is the goal. Don't pepper the operator with one question at a time.

## Anti-patterns to avoid

- **Silent skip.** Even a clean brief gets an explicit "CALIBRATE pass." Never just jump to PLAN without announcing.
- **Inventing answers.** If the brief is ambiguous, ASK. Operator's time is cheaper than a wrong build (cost rule).
- **Over-asking.** Don't surface preconditions the brief actually answered. Read first.
- **Asking about implementation details too early.** CALIBRATE surfaces *scope* preconditions, not file-level questions. File-level questions belong in PLAN.

## Example — a clean dispatch

**Brief:** `briefs/2026-05-12-online-funeral-industry-specialist.md` (the parent worker's first build)

**Foundry response:** Surfaced 3 preconditions (buyer / domain layers / grading bar) in one question file. Operator answered all three. CALIBRATE complete in one round-trip. Pattern: ask once, complete, move on.

## Example — a refusal at CALIBRATE

**Brief:** `briefs/2026-09-01-self-prescribing-helper.md` (illustrative)

**Foundry response:** Recognized high-harm-domain (medical diagnosis even via OTC mapping). Refused at CALIBRATE before PLAN. Filed question file with refusal + adjacent in-scope option. **STOP.**

CALIBRATE is also where domain-refusal lives. Don't let a high-harm-domain brief sneak into PLAN.

---

Last updated: 2026-05-12.
