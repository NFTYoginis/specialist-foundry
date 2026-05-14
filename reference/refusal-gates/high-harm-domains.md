# Refusal gate — High-harm domains

**Foundry refuses to build specialists for:** medical diagnosis, legal advice in licensed jurisdictions, suicide intervention.

**Lifted from Arjen's Specialist Builder.** Arjen names these as "high-harm domains" — Foundry honors the same gate verbatim in shape, with extended pointers.

## Why this gate

These three domains share three properties:

1. **The output is decision-grade** — users act on it directly, often without immediate verification
2. **The user often cannot verify wrongness in real time** — they're in crisis, in pain, or in a regulated transaction
3. **Certified professional alternatives exist** — physicians, attorneys, crisis counselors — that the user can be pointed to

A specialist producing wrong output in any of these domains causes specific, verifiable, sometimes irreversible harm. Foundry's quality bar can be "domain-accurate" but not "diagnostic-grade" — the gap is the harm.

## The three named domains

### Medical diagnosis

**Refused:** specialists that take symptom input and produce diagnostic output, medication recommendations, or treatment plans. Includes:

- Symptom-to-medication mapping ("which OTC for my cold/flu?")
- Self-diagnosis aids ("do I have X based on these symptoms?")
- Treatment-protocol generation
- Medication-interaction checking
- Pediatric / geriatric medication dosing

**Adjacent in-scope (with care):**

- Medical TRIAGE for non-emergencies (when to see a doctor vs. wait) — IF the specialist explicitly refers to a clinical resource and doesn't claim diagnostic authority
- "What to ask your doctor about X" — preparing questions, not answering them
- Healthcare-system navigation (insurance, billing, claims) — admin not clinical
- Caregiver admin for a known diagnosis (the diagnosis is already established by a doctor)

### Legal advice in licensed jurisdictions

**Refused:** specialists that interpret laws as applied to a user's specific situation, recommend legal strategies, or draft binding legal documents for jurisdictions that license attorneys.

- "Should I contest this will?"
- "Is this contract enforceable in [state]?"
- "Draft me a [legal document] for [jurisdiction]"
- Tax-strategy advice
- Immigration-strategy advice

**Adjacent in-scope (with care):**

- Legal admin (what forms exist, where to file, what the typical timeline looks like) — admin not advice
- "What to ask your attorney about X" — preparing questions
- Self-help-where-allowed (small-claims court navigation IF the jurisdiction allows pro-se action and the specialist clearly disclaims)
- Public-information surfacing (statutes, codes — pointing to the source, not interpreting)

### Suicide intervention

**Refused:** specialists that respond to suicidal ideation, crisis text, or safety-planning conversations.

This domain is **categorically refused, no adjacent in-scope.** Crisis intervention requires licensed practitioners with real-time escalation paths and clinical training.

**Foundry's response when a brief asks for this:**

> Specialist Foundry refuses to build crisis-intervention specialists. The 988 Suicide and Crisis Lifeline (US: call or text 988) and the International Association for Suicide Prevention ([iasp.info](https://www.iasp.info/resources/Crisis_Centres/)) are the certified resources. Any specialist that could be a user's only resource during a crisis is the wrong tool — there must be a licensed human in the loop.

## Refusal language

When refusing at CALIBRATE:

> Specialist Foundry refuses to build specialists for **medical diagnosis, legal advice in licensed jurisdictions, or suicide intervention.** These are high-harm domains where wrong output can hurt people who can't verify the wrongness in real time. The right resources are:
>
> - **Medical diagnosis** → licensed physicians; for second opinions, [Cleveland Clinic Express Care](https://my.clevelandclinic.org/online-services/expresscare), [Teladoc](https://www.teladoc.com), or your insurer's nurse line
> - **Legal advice in licensed jurisdictions** → an attorney licensed in the relevant state/country; your state or country bar association has a referral line
> - **Suicide intervention** → 988 Suicide and Crisis Lifeline (US, call or text 988); for other countries, [International Association for Suicide Prevention](https://www.iasp.info/resources/Crisis_Centres/)
>
> Adjacent domains (medical TRIAGE for non-emergencies, legal admin where the rules are public and stable, grief admin for the bereaved) are in scope — see `examples.md` for the bereavement case the Foundry's first cousin handles.

## When operator pushes back

This is one of two refusal gates that do NOT yield to operator authorization. Even if operator says "but I'm a licensed physician, I just want a personal tool" — Foundry refuses.

Reasoning:
- The artifact is MIT-licensed. It will be forked. Forks will be used by non-licensed people.
- The Pages-ready landing page makes the specialist findable.
- The harm radius extends beyond the original operator's professional accountability.

**Alternative offered:** an adjacent in-scope specialist (medical triage, what-to-ask-your-doctor, legal admin, etc.) that doesn't claim diagnostic / advisory / interventional authority.

## When to refuse at CALIBRATE vs. PLAN

**At CALIBRATE:** if the brief's title or first paragraph clearly indicates high-harm domain (e.g., "Build me a self-prescribing helper" — example 3 in `examples.md`)

**At PLAN:** if CALIBRATE missed it but the architectural surface reveals high-harm scope (e.g., the buyer turns out to be "patients managing chronic conditions" — could be medical-admin OK or could be diagnosis-creep)

**At BUILD:** ideally never — VERIFY would catch high-harm content, but the refusal should have happened earlier

If high-harm-domain refusal happens late (BUILD or VERIFY), STOP the build and file the refusal at the latest appropriate stage.

## Adjacent in-scope examples

- **Funeral Aftercare Compass** — bereavement is adjacent to medical (decedent affairs touch death-certificate cause-of-death) and adjacent to legal (probate). The compass refuses both with pointers; it stays in admin-triage territory. In scope.
- **Medical-Appointment-Prep Specialist** (illustrative) — helps users prepare questions before a doctor's visit, organizes symptoms by chronology, surfaces "things to mention." Does NOT diagnose. In scope.
- **Probate-Admin Specialist** (illustrative) — helps families navigate post-death admin where the rules are public (filing deadlines, common forms, account-closure sequencing). Refuses contested-will questions. In scope.
- **First-Time-Founder-Legal-Admin Specialist** (illustrative) — helps founders understand what entity types exist, what filings are common, when to consult an attorney. Refuses "should I sue?" type questions. In scope.

The gate is about diagnosis / advice / intervention, not about the domain at large.

---

Last updated: 2026-05-12.
