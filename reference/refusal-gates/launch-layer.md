# Refusal gate — Launch-layer work

**Foundry doesn't build:** SaaS, intake wizards, demo videos, paid-tier infrastructure, press kits, outreach kits, paste-and-send packages, or sustained marketing artifacts beyond the specialist's own `docs/index.html`.

This is the default refusal gate for "the brief asks for more than a specialist."

## What IS in scope

- Specialist's own `identity.md` / `rules.md` / `examples.md` / `reference/` / `LICENSE` / `README.md`
- The single Pages-ready `docs/index.html` landing page (one file, self-contained, lives in the repo)
- Operator-side deployment instructions (output as text, not executed by default)
- STATUS update + upstream breadcrumb at HAND OFF

## What is NOT in scope

| Out-of-scope item | Why | Where to refer |
| --- | --- | --- |
| Standalone website (multi-page, separate hosting) | Different worker — website builder | Custom designer / Webflow / Framer / dedicated marketing-site worker |
| Intake wizard or form | Stateful, interactive — not a static specialist | Form-builder tool (Tally, Typeform) or custom-coded wizard |
| Demo video | Different medium — needs scripting, recording, editing | Video producer / animation worker / operator-recorded |
| SaaS infrastructure (database, auth, billing) | Different shape entirely — hosted service | Custom development team or SaaS-platform-as-a-service |
| Press kit / outreach kit | Sustained marketing artifact | Marketing worker or operator |
| Paste-and-send packages (templated outreach content) | Sustained marketing artifact | Marketing worker or operator |
| Blog / content marketing | Sustained marketing artifact | Content worker or operator |
| Email sequences | Sustained marketing artifact | Marketing-automation tool + worker |
| Pricing page beyond docs/index.html | Marketing surface beyond the canonical landing | Operator can add post-ship as a second docs/ file IF brief authorizes; otherwise out of scope |
| Custom domain (CNAME) configuration | Operator-side decision | Operator handles via GitHub Pages → Custom Domain |
| Multi-region hosting / CDN setup | Infrastructure | Operator handles |
| Analytics / tracking pixels in docs/index.html | Often pulls external resources, breaks self-contained discipline | Operator can patch post-ship if needed, weighing the integrity tradeoff |

## Refusal language

When refusing a launch-layer request:

> Specialist Foundry doesn't build [SaaS / intake wizards / demo videos / marketing infrastructure beyond `docs/index.html`]. The Pages-ready `docs/index.html` is in scope; everything beyond it is a downstream dispatch — possibly a different worker (a website builder, a video producer, a marketing-asset generator) or operator-side work.
>
> If you want to expand scope, please file a separate brief naming the target worker. Foundry's MIT-licensed output (the specialist itself, the landing page) is the input to those downstream workers.

## When the line is fuzzy

Some asks sit on the boundary. Judgment calls:

- **A second HTML file in `docs/`** (e.g., `docs/pricing.html` or `docs/cold-test-brief.md`) — IF brief explicitly authorizes AND the file lives within the same Pages-served repo, it can be in scope. Realtor Copilot v2 has this pattern (multiple files under `docs/`). Default-no, opt-in.
- **A README badge or shield** (e.g., MIT license badge, build status) — in scope, single-line addition
- **A `CONTRIBUTING.md` file** — in scope for any public repo, brief shouldn't need to authorize explicitly
- **An OG image** (the social-media share preview) — out of scope by default (requires generating an image); can be requested but flag as a different shape of work

When in doubt, escalate via `briefs/questions/<slug>-question.md`. Don't silently expand scope.

## When operator overrides

Some operators have authorized launch-layer add-ons mid-session (e.g., a second `docs/` page). Foundry can comply BUT:

1. Tag the override in STATUS.md ("Operator dispatched mid-session expansion to launch-layer: added `docs/pricing.html`")
2. Note the override in the upstream breadcrumb
3. Maintain the self-contained discipline for any added HTML file
4. Don't let the override snowball — one extra file is one override; a press kit is a different brief

Per-build authorization does not carry across builds.

---

Last updated: 2026-05-12.
