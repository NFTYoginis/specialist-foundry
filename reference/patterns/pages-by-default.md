# Pattern — Pages-by-default

**Flair axis #2.** The visible differentiator. Every Foundry-built specialist ships with `docs/index.html` — a single self-contained HTML file (inline CSS, no external dependencies). Push the repo + enable Pages from `/docs` → public URL at `<username>.github.io/<slug>/` in 60 seconds.

Neither Arjen's Specialist Builder nor Virgilio's ICM Workspace Builder produces a landing page. This is a real differentiator.

## The 9 canonical sections (in order)

Modeled on Realtor Copilot v2's `docs/index.html` template (validated live at [nftyoginis.github.io/realtor-copilot-v2/](https://nftyoginis.github.io/realtor-copilot-v2/)).

| # | Section | Required | What Foundry generates |
| - | --- | --- | --- |
| 1 | `<head>` + inline CSS + meta tags + Open Graph | Yes | Title grounded in built specialist's value prop. Description from brief. OG tags for share previews. CSS variables defined at top of `<style>`. |
| 2 | Sticky top nav | Yes | Brand + 3-4 anchor links + 1 CTA button (GitHub repo link). Smooth-scroll via CSS. |
| 3 | Hero | Yes | Headline grounded in brief's buyer + value prop. Sub-headline qualifier. 2 CTAs above the fold. |
| 4 | "What it does" / "What you get" | Yes | 3-5 jobs or capabilities. Mirrors the specialist's identity.md "what you do" section. |
| 5 | Sample outputs | Yes | 1-3 worked examples rendered inline from `examples.md`. Real intake → real reply. |
| 6 | Proof block | Yes | **Either** `<!-- TODO: operator -->` placeholder **OR** illustrative composites with `(illustrative composite, fictional)` labels inline. **Never** unlabeled fake testimonials. |
| 7 | Setup steps | Yes | Numbered ~5 steps, ~5-20 minutes. Adapted from specialist's `README.md` setup. |
| 8 | FAQ | Recommended | 5-10 questions in `<details>` elements. Pulls from rules.md "what you don't do" + brief's known objections. |
| 9 | Footer | Yes | License (MIT line), GitHub link, attribution if any, last-updated date. |

## Visual identity per build (refusal-grade discipline)

**Every Foundry-built specialist's `docs/index.html` must have a distinct visual identity.** Not "same template, different palette" — genuinely different look and feel, so the operator's specialist catalogue doesn't read as one production wearing slightly different paint.

This is a refusal-grade discipline. A built specialist whose landing page is visually indistinguishable from another Foundry-built specialist fails VERIFY and gets rebuilt.

### Why this discipline exists

Pages-by-default is a real flair only if every built specialist looks like its own artifact. If three Foundry specialists all share the same cream palette + system sans + sticky-nav + rounded-card components, the "Pages-by-default" claim becomes weak — operators correctly read it as "yes you get a landing page but it's a template."

Tested 2026-05-12: the first two Foundry-built specialists (the online-funeral-family-compass and Specialist Foundry itself) shipped with visually-near-identical pages. Operator caught it immediately. Discipline added to prevent recurrence.

### Axes that MUST vary per build

At PLAN stage, propose distinct choices on every axis:

| Axis | Range to span across builds |
| --- | --- |
| **Color palette** | Light cream / warm white / pale sage / dark slate / monochrome / etc. — pick what fits the domain personality |
| **Accent color** | Amber / sage green / dusty rose / deep teal / muted plum / etc. — distinct from the previous two builds at minimum |
| **Typography hierarchy** | All-sans / serif-headlines-sans-body / mono-labels-sans-body / serif-throughout — mix appropriate to the domain |
| **Layout density** | Spacious (taller margins, line-height 1.7+, narrow max-width ~720px) / Standard (1.55 line-height, ~880px) / Dense (tighter margins, line-height 1.4, wide max-width 1100px+) |
| **Component personality** | Rounded soft cards with shadows / sharp corners with hairline borders / no borders just dividers / heavy-bordered |
| **Hero treatment** | Centered classic / split-screen / full-bleed gradient / code-block-styled / asymmetric |
| **Section ornamentation** | Pill-tagline + eyebrow + h2 / minimal text only / decorative dividers / numbered sections |

### Axes that MUST NOT vary (the discipline floor)

| Axis | Why it can't vary |
| --- | --- |
| **Self-contained discipline** | No external CSS/JS/font/image fetches. Verified by `grep -E "https?://" docs/index.html`. |
| **9 canonical sections in order** | Head + sticky nav + hero + what-it-does + sample output + proof block + setup + FAQ + footer. Structural, not stylistic. |
| **Labeled-illustrative discipline** | Every fictional name carries `(illustrative composite, fictional)` inline. Refusal gate. |
| **Anchor-link integrity** | Every `href="#x"` has a matching `id="x"`. Mechanical. |
| **Font sourcing** | System fonts only OR base64-inlined fonts. NO Google Fonts, NO CDN, NO external font requests. |

### Worked aesthetic identities (canonical examples)

**Bereavement / grief / hospice / palliative care:**
- Warm white background (`#fdfaf6` or lighter), pure white surfaces
- Serif headlines (Georgia stack), sans body — adds dignity
- Sage green (`#8aa085`) or muted dusty rose accent — life-affirming, not promotional
- Minimal borders, no shadows, soft hairline dividers
- Spacious layout (line-height 1.7, narrow max-width ~760px)
- Hero: centered, smaller, more breath
- Validated: `online-funeral-family-compass/docs/index.html` v1.1+

**Operator tooling / developer-grade / technical-trade:**
- Dark slate background (`#0f1419`), warm off-white text (`#e8e0d4`)
- Monospace section labels + nav + stage tags (`ui-monospace, SFMono-Regular, Menlo, Consolas, monospace`)
- Warm amber accent (`#d4943c`) for contrast against dark
- Sharp corners (4px), hairline borders (`1px solid var(--rule)`), no soft shadows
- Dense layout (wider container, tighter vertical rhythm)
- Hero: code-block-styled framing for the dispatch example
- Validated: `specialist-foundry/docs/index.html` v1.1+

**Realtor / sales tooling / market-facing professional:**
- Warm cream background (`#faf8f3`), white surfaces — Realtor Copilot v2's canonical
- All-sans system stack, larger headlines
- Warm amber accent (`#b5731a`)
- Rounded cards (12px), soft shadows, backdrop-blur on nav
- Standard density (line-height 1.55, max-width 880-1100px)
- Hero: centered with pill-tagline
- Validated: Realtor Copilot v2's existing `docs/index.html` (the original template the others diverged from)

These three are starting points, NOT a closed set. Brief at PLAN stage should propose a fourth, fifth, sixth aesthetic for new domains — financial, creative, education, hospitality, etc.

### What to do at PLAN stage

For every build, propose visual identity choices alongside the folder tree:

```
### Visual identity for docs/index.html
- Palette: [warm white / dark slate / pale sage / etc.]
- Headlines: [system sans / Georgia serif / monospace]
- Body: [system sans (default) / serif for long-form]
- Section labels: [eyebrow uppercase / monospace / small caps]
- Accent: [#hex code — distinct from previous 2 builds]
- Components: [rounded soft / sharp hairline / borderless dividers]
- Layout density: [spacious / standard / dense]
- Hero treatment: [centered classic / code-block / split / asymmetric]
- Justification: [why this aesthetic fits the domain personality]
```

Operator can confirm or override. NEVER ship a build where this section wasn't explicitly considered.

### What VERIFY checks (stage 4)

In addition to the 13-row ICM checklist, VERIFY for any build after the first now includes:

- **Visual differentiation check** — compare the proposed `docs/index.html` palette + type + components against the most recent 2 Foundry-built specialists. If any of (palette family, type system, component personality) match closely, flag for rework.
- This is a judgment check, not mechanical. Foundry surfaces the comparison and operator confirms differentiation is sufficient.

## Self-contained discipline (enforced by VERIFY)

The file must:

1. Have **inline CSS only** — no `<link rel="stylesheet">`
2. Have **no external resource references** — no Google Fonts, no CDN images, no external JS
3. Open via `file://` protocol cleanly
4. Pass the mechanical check:

```bash
grep -oE 'https?://[A-Za-z0-9./_:?#=&%-]+' docs/index.html | sort -u
```

Acceptable URLs in the grep output:
- The repo's own GitHub URL
- GitHub Issues URL
- Social URLs (Twitter, LinkedIn) for operator links
- Inbound citation URLs operator wants surfaced (e.g., FTC consumer page) IF they don't fetch assets

Unacceptable URLs:
- `fonts.googleapis.com`, `fonts.gstatic.com`
- `cdn.jsdelivr.net`, `unpkg.com`, any CDN
- External image hosts
- Any URL that the browser would fetch during page render

## Why self-contained matters

- **Pages serves it** — GitHub Pages does no preprocessing, so no Jekyll, no plugin dependencies
- **`file://` protocol works** — operator can preview locally before pushing
- **Email-shareable** — the whole file can be attached and viewed offline
- **Archive.org snapshots cleanly** — no broken external references in the snapshot

## Anti-patterns

- **Adding a Google Font** because "it looks nicer" — breaks self-contained discipline
- **Hosting images externally** because they're large — base64-inline or use SVG inline
- **Adding interactive JS** that fetches from a CDN — defeats the offline-readable promise
- **Manufactured social proof** in the proof block — see `refusal-gates/unlabeled-fake-proof.md`

## When operator wants more than docs/index.html

If brief asks for:
- A press kit → out of scope, file launch-layer refusal
- A demo video → out of scope, different worker
- A pricing page → could be in scope as a second `docs/<slug>-pricing.html` file IF brief explicitly authorizes; otherwise out of scope
- A blog → out of scope

The Pages-by-default page is one file. Anything beyond that is launch-layer.

## Worked example — the funeral compass

The Online Funeral Family Compass's `docs/index.html` ([live](https://nftyoginis.github.io/online-funeral-family-compass/)):

- ~750 lines of single self-contained HTML
- Warm cream background, cooler accent (`#8a6a3d`) for bereavement appropriateness
- 9 canonical sections present
- 2 sample outputs rendered inline (canonical California intake + Texas STOP-flag pre-signature review)
- Proof block populated with 3 illustrative composites, each labeled `(illustrative composite, fictional)` inline
- Self-contained discipline check: `grep` returns only the repo URL + issues URL
- HTTP 200 live within 60 seconds of `gh api pages` enable

That's the operational shape.

---

Last updated: 2026-05-12.
