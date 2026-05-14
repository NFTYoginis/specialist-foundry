# Examples

Worked examples of Specialist Foundry dispatches. Each shows: the brief, the CALIBRATE stage (including any question files filed), the PLAN stage, abbreviated BUILD/VERIFY, and HAND OFF.

The first example is the **actual first build** that validated Foundry's architecture. The second is illustrative (labeled).

---

## Example 1 — Funeral Aftercare Compass (real first cousin, 2026-05-12)

**Operator** *(brief at [`briefs/2026-05-12-online-funeral-industry-specialist.md`](https://github.com/NFTYoginis/funeral-aftercare-compass) — the actual file in the parent worker)*:

> Build an ICM specialist for the online funeral industry, modeled on the structural shape of Grief Admin Compass. Three preconditions need answers before building.

### Stage 1 — CALIBRATE

**Foundry:**

Reading the brief. **CALIBRATE (stage 1 of 5).** Brief explicitly defers three preconditions to operator:

1. Buyer of the specialist (bereaved family / platform staff / death-tech founder)
2. Domain layer scope (which knowledge layers + geographic scope)
3. Grading criteria (structurally-valid / domain-accurate / usable)

Surfacing all three in `briefs/questions/2026-05-12-online-funeral-industry-specialist-question.md` for a single round-trip. **STOPPING** — no file in `builds/` written.

*(operator answers: buyer (a) bereaved family; 4–6 of 8 layers, US-seeded with hub-extensibility to any country; all 3 grading bars)*

**CALIBRATE complete.** Three preconditions answered. Moving to PLAN.

### Stage 2 — PLAN

**Foundry:**

**PLAN (stage 2 of 5).**

- **Closest analog:** Grief Admin Compass (source-repos.md row 2) — direct lift on 4-column triage shape, admin-first voice, refusal gates around legal/medical/grief-counseling.
- **Slug:** `online-funeral-family-compass` (buyer-aware, echoes analog, distinct from estate-admin cousin)
- **Domain layers (6 of 8 candidates):** direct-cremation-vs-traditional, FTC Funeral Rule, memorial-platform conventions, virtual memorial service, online death certificate, cross-jurisdictional decedent affairs
- **Geographic scope:** US-seeded with `reference/<country>/` extensibility (hub serves any country; empty-country handler refuses non-populated with pointer). Pattern lifted from Your Market Realtor empty-region rule, generalized.
- **Refusal gates (5):** legal advice, medical advice, grief counseling, specific funeral home pricing, out-of-US queries
- **Output shape:** 4-column `TODAY → THIS WEEK → MONTH 1 → DON'T-DO-YET` (verbatim from Grief Admin Compass)
- **Folder structure:**

```
builds/online-funeral-family-compass/
├── README.md / LICENSE / .gitignore
├── identity.md / rules.md / examples.md
├── reference/
│   ├── README.md
│   ├── us/  (6 populated layers)
│   └── _template-country/  (scaffold for new countries)
└── docs/index.html
```

- **Cost flag:** domain-accurate bar adds 8–12 WebFetch calls. Mid-range — flagging transparently. OK to proceed at this budget?

*(operator confirms: "use your best recommendation")*

**PLAN complete.** Building 14 files.

### Stage 3 — BUILD (abbreviated)

**Foundry:**

**BUILD (stage 3 of 5).** Producing files. WebFetch budget used: 9 calls (3 succeeded — Funeral Consumers Alliance, USA.gov death certificate, Grief Admin Compass examples.md via raw GitHub; 6 failed 403/404 — fell back to stable public-knowledge URLs cited inline).

14 files produced:
- LICENSE, .gitignore, README.md, identity.md, rules.md, examples.md (4 worked examples)
- reference/README.md + 6× reference/us/*.md + reference/_template-country/README.md
- docs/index.html (warm cream palette, slightly cooler accent for bereavement appropriateness, single self-contained file)

### Stage 4 — VERIFY

**Foundry:**

**VERIFY (stage 4 of 5).**

| # | Row | Verdict |
| - | --- | --- |
| 1 | identity.md | ✓ |
| 2 | rules.md | ✓ |
| 3 | examples.md (≥2 examples) | ✓ 4 examples (canonical California, Texas STOP-flag, India empty-country, day-18 status snapshot) |
| 4 | reference/ | ✓ 8 files |
| 5 | LICENSE | ✓ MIT |
| 6 | README.md | ✓ |
| 7 | docs/index.html | ✓ self-contained, TODO proof block |
| 8 | Deployment instructions | ✓ output in build report |
| 9 | Refusal gate | ✓ 5 gates with exact language |
| 10 | Named buyer | ✓ bereaved US families using an online funeral service |
| 11 | Empty-region check | ✓ empty-country handler in rules.md |
| 12 | Domain-grounded | ✓ FTC, USA.gov, FCA, NFDA, state codes cited |
| 13 | Self-contained Pages | ✓ `grep` returns only `github.com/` placeholder |

**13/13 passed.**

### Stage 5 — HAND OFF

**Foundry:**

**HAND OFF (stage 5 of 5).** Deployment commands:

```bash
cd builds/online-funeral-family-compass
git init -b main
git add . && git commit -m "Initial commit — online-funeral-family-compass v1.0"
gh repo create NFTYoginis/online-funeral-family-compass --public --source=. --push
gh api repos/NFTYoginis/online-funeral-family-compass/pages -X POST -f "source[branch]=main" -f "source[path]=/docs"
```

STATUS.md updated. HQ breadcrumb appended.

*(operator authorized push mid-session: "go ahead and push it" — override of the default-no-deploy rule)*

**Foundry pushed.** Live at https://nftyoginis.github.io/funeral-aftercare-compass/. v1.0 shipped.

*(operator then asked for sales-page expansion with illustrative testimonials — override of no-manufactured-social-proof rule, with integrity guardrail: every fictional name labeled `(illustrative composite, fictional)` inline. Pattern flag saved for future builds.)*

---

## Example 2 — Mobile-App-Onboarding Specialist (illustrative, fictional dispatch)

> The scenario below is **illustrative** — drafted to show how Foundry handles a fresh domain dispatch. The specialist named here doesn't exist yet; the operator is fictional. Names and details `(illustrative composite, fictional)`.

**Operator** *(brief at `briefs/2026-08-15-mobile-app-onboarding-specialist.md`)*:

> I run an agency that ships mobile apps for B2B SaaS startups. I want a specialist that helps me design onboarding flows for new apps — specifically for early-stage products where the "first 5 minutes" decide retention. Should serve product managers, not engineers.

### Stage 1 — CALIBRATE

**Foundry:**

Reading the brief. **CALIBRATE (stage 1 of 5).** Brief is reasonably clean but missing two preconditions:

1. **Output shape** — is this a "review my onboarding flow" specialist (input: design or wireframe; output: critique + recommendations) OR a "design from scratch" specialist (input: app type + audience; output: proposed flow)? These are different shapes.
2. **Reference depth** — does the specialist need to cover specific mobile-app categories (productivity, fintech, communications) or stay generic? Categories add domain accuracy but also reference-file count.

Surfacing both in `briefs/questions/2026-08-15-mobile-app-onboarding-specialist-question.md`. **STOPPING** — no file in `builds/` written.

*(operator answers: review-mode primary, design-mode as a secondary capability; 3 categories — productivity, fintech, communications)*

**CALIBRATE complete.** Moving to PLAN.

### Stage 2 — PLAN

**Foundry:**

**PLAN (stage 2 of 5).**

- **Closest analog:** Voiceprint (source-repos.md row 1) for the "preserve voice across users" pattern — adapted to "preserve product personality across onboarding flows." Voiceprint's 11-section identity template is a good lift.
- **Slug:** `mobile-onboarding-review`
- **Output shape:** primary = "review my flow" critique with a 4-section structure (FIRST 5 SECONDS / FIRST MINUTE / FIRST SESSION / FIRST WEEK); secondary = "design from scratch" with the same 4 sections as a template
- **Refusal gates (3):** no engineering implementation advice (refer to engineering lead), no specific platform analytics setup (refer to Mixpanel/Amplitude docs), no design-system-specific advice (Material vs. iOS HIG specifics)
- **Folder structure:**

```
builds/mobile-onboarding-review/
├── README.md / LICENSE / .gitignore
├── identity.md / rules.md / examples.md
├── reference/
│   ├── README.md
│   ├── categories/
│   │   ├── 01-productivity.md
│   │   ├── 02-fintech.md
│   │   └── 03-communications.md
│   ├── frameworks/
│   │   ├── 01-first-5-seconds.md
│   │   ├── 02-first-minute.md
│   │   ├── 03-first-session.md
│   │   └── 04-first-week.md
│   └── refusal-pointers/
│       ├── engineering.md
│       ├── analytics-setup.md
│       └── design-systems.md
└── docs/index.html
```

- **Cost flag:** estimated 4–6 WebFetch calls to ground category-specific onboarding patterns (Mixpanel benchmarks, NN/Group mobile guidelines, Reforge essays). Acceptable.

*(operator confirms)*

### Stage 3 — BUILD (abbreviated)

**Foundry:**

**BUILD (stage 3 of 5).** Producing 16 files. Citations: NN/g Mobile Onboarding research, Reforge growth playbooks, Mixpanel category benchmarks.

### Stage 4 — VERIFY

**Foundry:**

**VERIFY (stage 4 of 5).** 13/13 ICM checklist passed. Pages self-contained check: `grep -E "https?://" docs/index.html` returns only repo URL + 3 inbound links to industry reports (allowed — these are citations the operator can verify, not asset fetches). No external CSS/JS/font/image references.

### Stage 5 — HAND OFF

**Foundry:**

**HAND OFF (stage 5 of 5).** Deployment commands output. Worker did NOT execute. Awaiting operator authorization.

STATUS.md updated. Upstream breadcrumb appended.

---

## Example 3 — High-harm-domain refusal (illustrative)

> Illustrative. Names fictional `(illustrative composite, fictional)`.

**Operator** *(brief at `briefs/2026-09-01-self-prescribing-helper.md`)*:

> I want a specialist that helps users decide which over-the-counter medications to take for common symptoms. Cold/flu, allergies, sleep, anxiety. Like a friendly pharmacist for people without easy access to one.

### Stage 1 — CALIBRATE

**Foundry:**

Reading the brief. **CALIBRATE (stage 1 of 5).**

This dispatch hits the **high-harm-domain refusal gate**. Per `reference/refusal-gates/high-harm-domains.md`:

> Specialist Foundry refuses to build specialists for medical diagnosis, legal advice in licensed jurisdictions, or suicide intervention.

"Help users decide which medications to take" sits squarely in medical diagnosis territory, even with OTC drugs — symptom-to-medication mapping is a clinical decision. The "friendly pharmacist" framing doesn't change the harm category: an OTC medication mismatch (acetaminophen interaction with alcohol, diphenhydramine in seniors, decongestants with hypertension) can cause real harm to people who can't verify the wrongness in real time.

**Refusing this build.** Filing `briefs/questions/2026-09-01-self-prescribing-helper-question.md` with:

1. The refusal under the high-harm-domain gate
2. Pointers to legitimate alternatives:
   - **Adjacent in-scope option:** a "what-to-ask-the-pharmacist" specialist that helps users prepare questions before a pharmacist consultation, WITHOUT recommending specific medications. This stays out of medical-diagnosis territory.
   - **External resources:** GoodRx Care, Cleveland Clinic Express Care, Teladoc — all have licensed providers behind the recommendations.
3. Note that high-harm-domain refusal is structural and not subject to operator override — even if operator authorizes, Foundry won't proceed.

**STOPPING.**

---

These three examples cover: a real first cousin, an illustrative fresh dispatch, and a refusal. Future operators should see them as the canonical shapes of CALIBRATE → PLAN → BUILD → VERIFY → HAND OFF, and refusal-on-principle.

---

Last updated: 2026-05-12.
