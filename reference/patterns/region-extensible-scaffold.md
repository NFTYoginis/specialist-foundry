# Pattern — Region-extensible scaffold

**Architectural pattern** for specialists that scope by region, country, jurisdiction, category, platform, or language. Lift in shape from [Realtor Copilot v2's case-studies pattern](https://github.com/NFTYoginis/realtor-copilot-v2) (`case-studies/<region>/region/`) and its `specialist/rules.md:57-63` empty-region handler.

## When to use this pattern

When the specialist serves a domain that:

- Has stable universal principles AND material variation by region/jurisdiction/category
- Could plausibly extend to other regions/jurisdictions/categories in the future
- Has a "hub" buyer who works across the axis OR a "single-region" buyer who works within one

Common examples:
- **Bereavement** — funeral law varies by country and US state
- **Real estate** — market dynamics vary by metro
- **Compliance** — regulations vary by jurisdiction
- **Healthcare** (where in-scope) — payer rules vary by country
- **Education** — accreditation varies by region

## The folder shape

```
builds/<slug>/
├── identity.md
├── rules.md
├── examples.md
├── reference/
│   ├── README.md             ← "how to extend to another region"
│   ├── <populated-region>/   ← the seeded region, e.g., `us/`, `nyc/`, `productivity/`
│   │   ├── 01-<topic-1>.md
│   │   ├── 02-<topic-2>.md
│   │   └── ... (N domain layers)
│   └── _template-region/     ← scaffold for adding a new region
│       └── README.md         ← "fill in for [REGION]"
└── docs/
    └── index.html
```

The leading underscore on `_template-region/` keeps it visually distinct and (if your tooling sorts alphabetically) sorts it last. The trailing slash on every region keeps the structure obvious in tree views.

## The rules.md additions required

When this pattern is in use, the built specialist's `rules.md` must include:

### Empty-region handling (generalized from Realtor Copilot v2)

```markdown
## Empty-region handling

If the user's [region/country/jurisdiction/category] is not in `reference/<region>/`:

1. State directly: "This specialist is currently <seeded-region> only."
2. Point to the region-specific starting resources (cite the relevant authorities/NGOs/etc. for that region).
3. Offer to proceed with **universal output only** (the principles that transfer regardless of region) — **only if the user explicitly confirms** they understand the region-specific layer is missing.
4. Do **not** silently produce <seeded-region>-content output for a non-seeded region.
```

### Empty-region refusal in identity.md

```markdown
You serve <buyer> in <seeded-region> — see "Empty-region handling" in `rules.md`. Out-of-region queries are refused with a pointer, not guessed.
```

## The reference/README.md content

Should describe:

1. **The folder layout** (visually)
2. **How the specialist uses the folder** (the empty-region handler)
3. **How to add a new region** — copy `_template-region/` to `<region-code>/`, populate the standard files, validate locally before merging
4. **Validation discipline** for the new region — what makes a populated region "ready"
5. **Citation discipline** — what sources are acceptable for that domain's regional content

## The _template-region/README.md content

A scaffold guide that says, for each standard file in the populated region:

- What to populate
- What's universal (transfers from the seeded region or from cross-region principles)
- What's region-specific (must be regional source-grounded)
- What sources are acceptable

Plus a "when NOT to populate a region" section — preemptive population is discouraged in favor of user-driven population.

## Naming convention for region codes

Prefer **ISO 3166-1 alpha-2** codes for countries (`us`, `uk`, `de`, `au`, `mx`). For sub-national regions, use widely-recognized abbreviations (`ny`, `ca-on`, etc.).

For non-geographic axes (category, platform, language), use intuitive lowercase slugs (`productivity`, `fintech`, `communications` for categories; `ios`, `android`, `web` for platforms).

## Anti-patterns

- **Populating all regions preemptively** — creates stale content the moment regulations change. Populate one region; let user need drive the next.
- **Silent fallback to seeded region** — if user is in Mexico and asks about funeral law, don't silently give US output. Refuse with a pointer.
- **No `_template-region/` scaffold** — without it, the next contributor doesn't know what shape to populate. The scaffold is the contract.
- **Deep regional nesting** — `reference/us/california/los-angeles/` is usually over-decomposition. Stop at the regulatory boundary unless content genuinely varies at the finer grain.

## Worked example — funeral compass

```
builds/online-funeral-family-compass/reference/
├── README.md                 ← "how to extend to another country"
├── us/                       ← populated
│   ├── 01-direct-cremation-vs-traditional.md
│   ├── 02-ftc-funeral-rule.md
│   ├── 03-memorial-obituary-publishing.md
│   ├── 04-virtual-memorial-service.md
│   ├── 05-online-death-certificate.md
│   └── 06-cross-jurisdictional-decedent-affairs.md
└── _template-country/        ← scaffold
    └── README.md             ← UK / Canada / Australia / Ireland flagged as high-priority but unpopulated
```

The empty-country handler in `rules.md`:

> If `reference/<country>/` does not exist for the country the family names:
> 1. State directly: "This compass is currently US-seeded only."
> 2. Point to the country-specific starting resources.
> 3. Offer to proceed with universal output only — only if the family explicitly confirms.
> 4. Do not silently produce US-content output for a non-US family.

That's the operational shape.

## Citation back

Two-level citation in the built specialist:

1. **Original source:** Realtor Copilot v2's `specialist/rules.md:57-63` empty-region handler
2. **Foundry pattern:** this file (`reference/patterns/region-extensible-scaffold.md`)

Built specialists should cite both — the lineage is the architecture.

---

Last updated: 2026-05-12.
