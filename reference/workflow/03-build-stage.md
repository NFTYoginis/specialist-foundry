# Stage 3 — BUILD

**Produce files under `builds/<slug>/`.** Files start being written here, never earlier.

## What happens

1. **Read the relevant source-repo files and research reports first.** Don't write `identity.md` before you've read the analog repo's `identity.md`.
2. **Batch file writes in parallel where possible.** Independent files (e.g., 6 reference layer files in different sub-folders) can be written in a single tool-call message with multiple `Write` invocations.
3. **Use code-based scaffolding for repetitive structures.** If building 4 case-study folders with the same 6-file shape, write a small Bash script that generates the structure rather than authoring 24 files manually. The script lives alongside the build for reproducibility.
4. **Cite source repos and research reports** in every file that lifts a pattern. Two-level citation: (1) where the pattern came from originally, (2) which Foundry pattern file codifies it.
5. **Ship `docs/index.html`** — not optional. Model on Your Market Realtor's structural template but adapt visual palette to the brief's domain (e.g., the funeral compass uses a slightly cooler accent than Your Market Realtor's amber, for bereavement appropriateness).
6. **Verify cross-file consistency before announcing BUILD complete.** If `rules.md` references `reference/us/02-ftc-funeral-rule.md`, that file must exist.

## File-writing order

There's no fixed order, but a reasonable default:

1. LICENSE / .gitignore (mechanical)
2. README.md (sets the surface)
3. identity.md (sets who/serves/does/sounds)
4. rules.md (relies on identity.md being consistent)
5. examples.md (relies on rules.md output shape being defined)
6. reference/ files in parallel (independent of each other)
7. docs/index.html (last — pulls hero copy from identity.md, sample output from examples.md, FAQ from rules.md)

## Citation discipline

When writing a file that lifts a pattern, the file should contain:

```markdown
This pattern is **lifted in shape with content swap** from [Your Market Realtor's `specialist/rules.md:57-63`](https://github.com/NFTYoginis/your-market-realtor), codified in Foundry's [`reference/patterns/region-extensible-scaffold.md`](../patterns/region-extensible-scaffold.md).
```

Three things named: source, what was lifted, where Foundry codified it.

## Cost discipline during BUILD

- **Prefer government + NGO + raw-content URLs** for WebFetch over commercial/regulator-marketing pages. Pattern proven in the funeral build: `consumer.ftc.gov` and `forevermissed.com` 403'd; `usa.gov` and `funerals.org` and `raw.githubusercontent.com` rendered cleanly.
- **Flag big WebFetch budgets transparently.** If a build needs 12+ fetches, surface the choice at PLAN, not silently spend during BUILD.
- **Don't auto-clone source repos.** WebFetch on README + raw file URLs. Clone only if brief explicitly authorizes.

## Voice discipline during BUILD

The voice every Foundry-built specialist uses internally is the same voice the [Funeral Aftercare Compass](https://github.com/NFTYoginis/funeral-aftercare-compass) uses externally:

> Calm. Practical. Direct. No platitudes after the first acknowledgment.

No "transformative journey" / "unlock potential" / "empower" / "level up" / "sacred space" / "hold space" / "mindfulness journey" / "leverage" / "streamline" / "simply" / "effortless" / "game-changer" vocabulary.

This is structural, not stylistic. The operator-grade buyer has read enough marketing copy to spot it.

## What BUILD does NOT do

- **No deployment** by default — `gh repo create` / `git push` / `gh api pages` belong in HAND OFF, and worker doesn't execute them by default.
- **No editing of files in the parent worker's directory** — Foundry produces ONLY into `builds/<slug>/`.
- **No HQ writes** — only HAND OFF appends the breadcrumb.
- **No skipped ICM files** — identity / rules / examples / reference / LICENSE / README / `docs/index.html` are all written. VERIFY catches misses.

## Pages-by-default during BUILD

`docs/index.html` is a load-bearing file, not a footnote. It must:

1. Be a single self-contained HTML file
2. Have inline CSS (no `<link rel="stylesheet">`)
3. Have no external resource references (no Google Fonts, no CDN images, no external JS)
4. Open via `file://` protocol cleanly
5. Use the warm-cream palette by default (override per brief's domain — bereavement = slightly cooler accent; financial = slightly more reserved palette)
6. Hit all 9 canonical sections in order: head + sticky nav + hero + what-it-does + sample output + proof block + setup + FAQ + footer
7. **Include OG / Twitter Card meta tags** pointing to `docs/og-image.png` (an absolute Pages URL). These ship even before the PNG exists — until the PNG lands, social shares fall back to text-only previews. Required tags: `og:title`, `og:description`, `og:type`, `og:url`, `og:image`, `og:image:width` (1200), `og:image:height` (630), `og:image:alt`, `twitter:card` (`summary_large_image`), `twitter:title`, `twitter:description`, `twitter:image`.

See `reference/patterns/pages-by-default.md` for the full template.

## OG-image design brief — also written during BUILD

Alongside `docs/index.html`, BUILD also produces an OG-image design brief at `briefs/og-images/<YYYY-MM-DD>-<repo-slug>-og-image.md`. This brief is forwarded by operator to a design-team worker; the design team delivers the PNG; operator drops it in at `docs/og-image.png` and pushes.

The brief includes (paste-ready for design team — they have no build context):

- 2-sentence product description
- Visual identity table extracted from the live `docs/index.html` (exact hex codes, type stack, density, accent-usage rules)
- Composition diagram (ASCII layout or written description)
- Visual hook — the one distinctive thing the OG image leads with (e.g., verdict trichotomy / four-column triage / dispatch architecture diagram / 4-populated-markets cards)
- No-go list (no testimonials, no competitor names, no stock photography, no emojis, no external fonts, no AI badges)
- Output specs (1200×630 PNG, sRGB, edge-to-edge background, ≤1MB, deliver path)
- Design-team self-check list (thumbnail legibility, exact dimensions, accent restraint, no-go compliance)

Looking at any existing brief in `~/Documents/specialist-builder/briefs/og-images/` is the canonical template. Pattern fully spec'd in `reference/patterns/pages-by-default.md` §OG-image-brief.

VERIFY (stage 4) checks that the brief file exists alongside the build. Without it, the build is not done.

---

Last updated: 2026-05-15 (added OG meta tags to Pages-by-default requirement #7; added OG-image-design-brief as standard BUILD output).
