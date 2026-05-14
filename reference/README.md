# Reference layer

The dense knowledge that Specialist Foundry consults during every dispatch. Organized into three sub-folders:

```
reference/
├── README.md             ← this file
├── workflow/             ← the 5 named stages: CALIBRATE → PLAN → BUILD → VERIFY → HAND OFF
├── patterns/             ← 4 reusable architectural patterns Foundry applies during BUILD
└── refusal-gates/        ← 3 refusal gates with exact language
```

## How Foundry uses this folder

During every dispatch:

- **Stage announcements pull from `workflow/`** — each stage file describes the discipline of that stage. Foundry reads the relevant file before announcing the stage (e.g., reads `01-calibrate-stage.md` before "CALIBRATE (stage 1 of 5)").
- **Architectural choices pull from `patterns/`** — when applying a pattern (audit-trail dispatch, Pages-by-default, integrity-guardrails, region-extensible scaffold), Foundry cites the pattern file in its plan and build output.
- **Refusals pull from `refusal-gates/`** — when refusing a dispatch or scope item, Foundry quotes from the relevant gate file rather than improvising refusal language.

## Citation discipline carries down

A specialist built by Specialist Foundry inherits citation discipline. When that specialist's `rules.md` cites a pattern (e.g., the empty-region rule), it should cite back to both:

1. The original source (e.g., Your Market Realtor's `specialist/rules.md:57-63`)
2. The Foundry pattern file (e.g., `reference/patterns/region-extensible-scaffold.md`)

Two-level citation: where the pattern came from, AND where Foundry codified it. This is how the architecture stays inspectable across forks.

## Companion catalogue

For the source-repo catalogue (the 11 Skool-competition reference repos + Your Market Realtor), Foundry points to `~/Documents/specialist-builder/reference/source-repos.md` in its parent worker's repo. Forking that catalogue into Specialist Foundry's own repo is a deliberate non-choice — the catalogue belongs to the operator's research layer, not to the Foundry's architectural layer. Forks of Specialist Foundry can maintain their own catalogue or point upstream.

---

Last updated: 2026-05-12.
