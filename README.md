# Specialist Foundry

**An ICM meta-builder for operators who ship multiple specialists across domains. Brief in → folder of markdown + Pages-ready landing page out. Built by an operator, for operators.**

A folder of Claude-project knowledge that turns Claude into a meta-builder. You write a brief into `briefs/`, paste a one-line dispatch, and Specialist Foundry produces a full ICM-canonical specialist repo: identity, rules, examples, reference, LICENSE, README, and a self-contained `docs/index.html` Pages-ready landing page. About 30 minutes per specialist from brief to public URL.

---

## Who it's for

**The operator-grade builder.** Specifically:

- Solo founders, agencies, internal-tools people who ship multiple specialists across domains
- People who want an **audit trail per build** (knows what was decided, when, and why)
- People who ship **Pages-by-default** — their specialists are public-facing artifacts, distributed to real users, not just internal helpers
- People who treat **integrity as a feature** — refuses to mislead end-users of the specialist's output (no manufactured testimonials, no invented domain content, no unlabeled fake proof)

This is the empty slot between [Arjen's Specialist Builder](https://github.com/astetic-dev/specialist-builder) (which targets developers who want fast inline output via chat-prompt) and [Virgilio's ICM Workspace Builder](https://workflowcreate.netlify.app) (which targets non-technical archetype-pickers via wizard UX). Specialist Foundry sits between them: brief-file dispatch, durable artifacts, audit trail, Pages output.

## Who it's NOT for

- **Casual hobbyists who want one quick specialist** → use Arjen's chat-prompt version, it's 10 minutes and zero ceremony
- **Non-technical users who want a wizard** → use Virgilio's ICM Workspace Builder, archetype-driven and friendly
- **Anyone building specialists for medical diagnosis, legal advice in licensed jurisdictions, or suicide intervention** → Foundry refuses these on principle (lifted from Arjen's gate). Refer to certified professionals.
- **Anyone wanting SaaS or a hosted builder** → Foundry is a folder you upload to a Claude project, not a hosted service

## What it does

Specialist Foundry runs every build through five named stages:

| # | Stage | What you do | What Foundry does |
| - | --- | --- | --- |
| 1 | **CALIBRATE** | Drop a brief file into `briefs/` | Reads brief; surfaces preconditions as questions (`briefs/questions/<slug>.md`) if any are missing; **STOPS** until you answer. Calibration is mandatory and not skippable. |
| 2 | **PLAN** | Confirm or redirect | Surfaces closest analog repo, proposed folder + file tree, key patterns being applied, open questions. You sign off or file a question. |
| 3 | **BUILD** | Wait briefly | Produces files under `builds/<slug>/`. Cites source repos and research reports. Ships a Pages-ready `docs/index.html`. |
| 4 | **VERIFY** | Review the build report | Runs the 13-row ICM checklist + Pages self-contained discipline check. Reports pass/fail per row. |
| 5 | **HAND OFF** | Optionally authorize deployment | Outputs operator-side `gh` CLI commands for repo creation + Pages enablement. Updates `STATUS.md`. Appends an upstream-orchestrator breadcrumb. Worker does NOT execute deployment by default. |

## What every Foundry-built specialist ships with

- **`identity.md`** — who the specialist is, who it serves, how it sounds
- **`rules.md`** — Always / Never / refusal gates / empty-input handling
- **`examples.md`** — at least two worked examples (canonical input → canonical output)
- **`reference/`** — dense domain knowledge the specialist would otherwise hallucinate, organized as the domain requires (sub-folders by region, by topic, etc.)
- **`LICENSE`** — MIT by default
- **`README.md`** — setup + first-run prompts + what the specialist does/doesn't
- **`docs/index.html`** — **Pages-ready self-contained landing page** (inline CSS, no external dependencies). Push the repo and enable Pages from `/docs` → live public URL at `<username>.github.io/<repo-name>/`

The Pages-by-default discipline is the visible differentiator. Every specialist is its own self-promoting artifact from day one.

## The three flair axes that make this Foundry, not a clone

1. **Audit-trail dispatch.** Every build has a brief file, optional question files, and a status update. You can read a year-old build's `briefs/<date>-<slug>.md` and `STATUS.md` and reconstruct what was decided and why. Neither cousin does this.

2. **Pages-by-default.** Every specialist ships with a self-contained `docs/index.html`. Push + enable Pages → public URL in 60 seconds. Neither cousin does this.

3. **Integrity-guardrails for high-trust domains.** Foundry refuses to manufacture testimonials, engagement metrics, or case studies. If you want fake examples on a built specialist's landing page (for pre-launch warming), Foundry insists on labeling them `(illustrative composite, fictional)`. The bereavement-product test case proves this matters.

## Setup (about 5 minutes, one time)

1. **Clone or download this repo.**
   ```bash
   git clone https://github.com/NFTYoginis/specialist-foundry.git
   ```

2. **Create a new Claude Project** at [claude.ai/projects](https://claude.ai/projects).

3. **Upload these files as Project Knowledge:**
   - `identity.md`
   - `rules.md`
   - `examples.md`
   - All files under `reference/`

4. **Create a working folder** somewhere on disk (e.g., `~/Documents/my-specialists/`) with two sub-folders: `briefs/` and `builds/`.

5. **First-run prompt:**

   Write a brief into `briefs/<date>-<slug>.md` describing the specialist you want built (target buyer, domain, output shape, scope limits). Then paste this verbatim into your Claude project chat:

   > Read the brief at `briefs/<filename>` and dispatch through the five Foundry stages.

   Foundry will run CALIBRATE → PLAN → BUILD → VERIFY → HAND OFF.

## Sample brief

```markdown
# Build Brief — <specialist name>

**Date:** YYYY-MM-DD
**Build target:** `builds/<slug>/`
**Repo on push:** `github.com/<username>/<slug>`

## What to build
[1-3 paragraphs: who the specialist serves, what domain, what output shape]

## Preconditions (answer before any file is written)
1. Buyer specifics — [if multiple buyer shapes possible, name the one you want]
2. Domain scope — [which knowledge layers, geographic/regulatory scope]
3. Grading bar — [structurally-valid / domain-accurate / usable]

## Out of scope
[What you do NOT want Foundry to build]
```

A worked brief lives at `examples.md` — read it before writing your first one.

## What Specialist Foundry refuses (three named gates)

- **Launch-layer work** — no SaaS, no wizards, no marketing sites beyond the specialist's own `docs/index.html`. Press kits, outreach kits, paid-tier infrastructure are out of scope.
- **High-harm domains** — no specialists for medical diagnosis, legal advice in licensed jurisdictions, or suicide intervention. Refer to certified professionals.
- **Unlabeled fake proof** — Foundry will not manufacture testimonials, engagement metrics, or case studies for a specialist's `docs/index.html` unless they are explicitly labeled `(illustrative composite, fictional)`. The bereavement-product use case shaped this rule.

## Comparison to the cousins

| Axis | **Specialist Foundry** | Arjen's Specialist Builder | Virgilio's ICM Workspace Builder |
| --- | --- | --- | --- |
| Dispatch | Brief file in `briefs/` | Single-line chat prompt | Wizard UX |
| Output medium | Pre-built folder on disk | Inline markdown code blocks | Downloadable .zip |
| Pages landing page | ✓ self-contained `docs/index.html` | ✗ | ✗ |
| Audit trail | ✓ brief + question files + STATUS | ✗ chat-ephemeral | ✗ wizard-ephemeral |
| Integrity-guardrails | ✓ explicit refusal gates | High-harm-domain gate only | Archetype-gated |
| Workflow stages | 5 named (CALIBRATE → HAND OFF) | 5 named (CALIBRATE → HAND OFF) | Archetype-driven |
| Buyer | Operator-grade builder | Developer | Non-technical |

Specialist Foundry's CALIBRATE→HAND OFF workflow is lifted from Arjen's Specialist Builder; the rest of the architecture (folder layout, refusal gates, Pages-by-default, integrity-guardrails) is distinct.

## Repository structure

```
specialist-foundry/
├── README.md             ← this file
├── LICENSE               ← MIT
├── .gitignore
├── identity.md           ← who Foundry is, who it serves
├── rules.md              ← Always / Never / refusal gates / ICM checklist
├── examples.md           ← worked dispatches
├── reference/
│   ├── README.md
│   ├── workflow/         ← 5 stage files
│   ├── patterns/         ← 4 named patterns
│   └── refusal-gates/    ← 3 gate files
└── docs/
    └── index.html        ← Pages-ready public landing page
```

## License

MIT — see [LICENSE](LICENSE).

## Acknowledgments

Built side-by-side with:
- [Arjen's Specialist Builder](https://github.com/astetic-dev/specialist-builder) — workflow naming (CALIBRATE / CONFIRM / BUILD / SELF-REVIEW / HAND OFF) and high-harm-domain refusal gate lifted from this work.
- [Virgilio's ICM Workspace Builder](https://workflowcreate.netlify.app) — architectural cousin; their 6-layer system informed the workflow/patterns/refusal-gates substructure.
- [Grief Admin Compass](https://github.com/astetic-dev/grief-admin-compass) — the 4-column triage shape and admin-first voice we used to validate Foundry's first build.
- [Realtor Copilot v2](https://github.com/NFTYoginis/realtor-copilot-v2) — the empty-region pattern we generalized into Foundry's integrity-guardrail framework, and the Pages-by-default visual template.

The first specialist built with Specialist Foundry's architecture is the [Online Funeral Family Compass](https://github.com/NFTYoginis/online-funeral-family-compass) ([live](https://nftyoginis.github.io/online-funeral-family-compass/)) — built 2026-05-12 on the architecture this Foundry now codifies.

## Status

**v1.0 at first ship, 2026-05-12.** Architecture is operator-tested via the online-funeral-family-compass build. Cold-test with an external operator (someone other than the author) is the next validation step.
