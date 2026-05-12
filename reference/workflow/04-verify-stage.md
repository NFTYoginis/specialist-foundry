# Stage 4 — VERIFY

**Run the 13-row ICM checklist. Run the Pages self-contained discipline check. Report pass/fail per row.** Arjen's "SELF-REVIEW" renamed to match the discipline this Foundry's parent worker already uses (and to be more honest — VERIFY is a discrete pass/fail check, not a vague review).

## The 13-row ICM checklist

| # | Requirement | Pass criteria |
| - | --- | --- |
| 1 | `identity.md` | Who you are / who you serve / what you do / what you don't / how you sound |
| 2 | `rules.md` | Always / Never / routing (if multi-job) / refusal gates / empty-input handling |
| 3 | `examples.md` | ≥2 worked examples, canonical input → canonical output |
| 4 | `reference/` | Folder holding dense domain knowledge; sub-organized as the domain requires |
| 5 | `LICENSE` | MIT default unless brief specifies otherwise |
| 6 | `README.md` | Setup + first-run prompts + what the specialist does/doesn't |
| 7 | `docs/index.html` | Pages-ready single-file landing page. Self-contained. Hero grounded in brief's buyer + value prop. Proof block carries `(illustrative composite, fictional)` labels OR `<!-- TODO: operator -->` placeholder — never unlabeled fake proof. Anchor links resolve. |
| 8 | Deployment instructions | `gh` CLI sequence output as part of build report. Worker does NOT execute by default. |
| 9 | Refusal gate | ≥1 named in rules.md with exact refusal language quoted |
| 10 | Named buyer | ≥1 buyer in identity.md; no generic "anyone who wants X" |
| 11 | Path/region check | If specialist has region/jurisdiction-specific data, an empty-region-handling rule. For non-regional specialists: still confirm no implicit-region drift. |
| 12 | Domain-grounded | No invented regulations, terminology, or workflows; every domain claim references the brief or a public source. No unlabeled manufactured social proof. |
| 13 | Self-contained Pages output | `grep -E "https?://" docs/index.html` returns only intra-repo paths, GitHub repo URLs, or social URLs. File must work via `file://` protocol. |

## Self-contained discipline check (mechanical)

```bash
cd builds/<slug>
grep -oE 'https?://[A-Za-z0-9./_:?#=&%-]+' docs/index.html | sort -u
```

Acceptable URLs in the output:
- The repo's own GitHub URL (e.g., `https://github.com/<username>/<slug>`)
- GitHub Issues URL (for "open an issue" links)
- Social URLs (Twitter, LinkedIn) for the operator's links
- Citation URLs operator wants surfaced (e.g., FTC consumer page) IF they don't fetch assets

Unacceptable URLs:
- Google Fonts (`fonts.googleapis.com`)
- CDN-hosted CSS (`cdn.jsdelivr.net`, `unpkg.com`)
- External image hosts
- Any URL that downloads runtime resources

If any unacceptable URL is found: VERIFY fails. Fix BUILD output and re-run.

## Verify-stage anti-patterns

- **Skipping rows.** Run all 13. Even on a clean-looking build.
- **Marking pass on row 12 without checking citations.** Open at least one reference file and confirm citations are real URLs, not invented ones.
- **Marking pass on row 7 without grep-checking row 13.** They're related. Pages-ready isn't pass until self-contained is also pass.
- **Skipping anchor-link integrity.** If `docs/index.html` has `href="#setup"`, there must be an element with `id="setup"`. Mechanical check.

## When VERIFY fails a row

1. **Surface the specific failure** — which row, which file, what's wrong
2. **Fix the file** if the failure is mechanical (missing section, missing citation, broken anchor)
3. **Escalate to operator** if the failure is structural (e.g., domain-grounded fails because the brief didn't supply enough domain content — operator needs to expand the brief, not Foundry's call to invent)
4. **Re-run VERIFY** after the fix
5. **Don't declare BUILD complete until all 13 pass**

## Example VERIFY report (good)

```
**VERIFY (stage 4 of 5).**

| # | Row | Verdict |
| - | --- | --- |
| 1 | identity.md | ✓ |
| 2 | rules.md | ✓ |
| 3 | examples.md (≥2 examples) | ✓ 4 examples |
| 4 | reference/ | ✓ 8 files |
| 5 | LICENSE | ✓ MIT |
| 6 | README.md | ✓ |
| 7 | docs/index.html | ✓ self-contained |
| 8 | Deployment instructions | ✓ output in build report |
| 9 | Refusal gate | ✓ 5 gates with exact language |
| 10 | Named buyer | ✓ bereaved US families using an online funeral service |
| 11 | Empty-region check | ✓ empty-country handler in rules.md |
| 12 | Domain-grounded | ✓ FTC, USA.gov, FCA, NFDA cited |
| 13 | Self-contained Pages | ✓ grep returns only github.com placeholder |

**13/13 passed.** Moving to HAND OFF.
```

---

Last updated: 2026-05-12.
