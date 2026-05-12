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

## Visual defaults

Inherited from Realtor Copilot v2's palette unless brief specifies otherwise:

```css
:root {
  --bg: #faf8f3;          /* cream */
  --surface: #ffffff;
  --ink: #1a1a1a;
  --muted: #5b5b5b;
  --rule: #e6e2d8;
  --accent: #b5731a;      /* warm amber - default */
  --accent-soft: #fdf3e2;
  --code-bg: #f5f1e8;
}
```

**Per-domain palette adjustment:**
- **Bereavement / health / grief:** cooler accent (`#8a6a3d` rather than `#b5731a`). Less promotional warmth.
- **Financial / regulatory:** more reserved palette (less accent, more rule lines).
- **Creative / education:** can lean toward Realtor Copilot v2's warmer default.
- **Brief-specified brand colors:** override defaults.

Always: system font stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", "Helvetica Neue", Arial, sans-serif`). No Google Fonts, no web fonts, no external font requests.

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
