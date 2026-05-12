# Stage 3 — BUILD

**Produce files under `builds/<slug>/`.** Files start being written here, never earlier.

## What happens

1. **Read the relevant source-repo files and research reports first.** Don't write `identity.md` before you've read the analog repo's `identity.md`.
2. **Batch file writes in parallel where possible.** Independent files (e.g., 6 reference layer files in different sub-folders) can be written in a single tool-call message with multiple `Write` invocations.
3. **Use code-based scaffolding for repetitive structures.** If building 4 case-study folders with the same 6-file shape, write a small Bash script that generates the structure rather than authoring 24 files manually. The script lives alongside the build for reproducibility.
4. **Cite source repos and research reports** in every file that lifts a pattern. Two-level citation: (1) where the pattern came from originally, (2) which Foundry pattern file codifies it.
5. **Ship `docs/index.html`** — not optional. Model on Realtor Copilot v2's structural template but adapt visual palette to the brief's domain (e.g., the funeral compass uses a slightly cooler accent than Realtor Copilot v2's amber, for bereavement appropriateness).
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
This pattern is **lifted in shape with content swap** from [Realtor Copilot v2's `specialist/rules.md:57-63`](https://github.com/NFTYoginis/realtor-copilot-v2), codified in Foundry's [`reference/patterns/region-extensible-scaffold.md`](../patterns/region-extensible-scaffold.md).
```

Three things named: source, what was lifted, where Foundry codified it.

## Cost discipline during BUILD

- **Prefer government + NGO + raw-content URLs** for WebFetch over commercial/regulator-marketing pages. Pattern proven in the funeral build: `consumer.ftc.gov` and `forevermissed.com` 403'd; `usa.gov` and `funerals.org` and `raw.githubusercontent.com` rendered cleanly.
- **Flag big WebFetch budgets transparently.** If a build needs 12+ fetches, surface the choice at PLAN, not silently spend during BUILD.
- **Don't auto-clone source repos.** WebFetch on README + raw file URLs. Clone only if brief explicitly authorizes.

## Voice discipline during BUILD

The voice every Foundry-built specialist uses internally is the same voice the [Online Funeral Family Compass](https://github.com/NFTYoginis/online-funeral-family-compass) uses externally:

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

See `reference/patterns/pages-by-default.md` for the full template.

---

Last updated: 2026-05-12.
