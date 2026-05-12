# Stage 5 — HAND OFF

**Output operator-side deployment commands. Update STATUS. Append upstream-orchestrator breadcrumb.** Lifted from Arjen's Specialist Builder ("HAND OFF" as the final stage); the name carries forward unchanged.

## What happens

1. **Output the `gh` CLI deployment sequence** as part of the build report — operator runs these.
2. **Update `STATUS.md`** in the worker's directory (NOT in the built specialist's directory). What shipped, what failed, what's queued.
3. **Append an upstream-orchestrator breadcrumb** — a single line to whatever STATUS the operator's parent orchestrator maintains (e.g., HQ STATUS, agency-level STATUS, or a personal `~/STATUS.md`).
4. **Worker does NOT execute deployment by default.** Operator may authorize per-build override; that authorization does not carry across builds.

## Deployment sequence template

```bash
# 1. Navigate to the build directory
cd builds/<slug>

# 2. Initialize git + first commit
git init -b main
git add .
git commit -m "Initial commit — <slug> v1.0"

# 3. Create the public GitHub repo and push (assumes gh CLI authenticated)
gh repo create <username>/<slug> --public --source=. --remote=origin --push --description "<one-line description>"

# 4. Enable GitHub Pages serving from /docs
gh api repos/<username>/<slug>/pages \
  -X POST \
  -f "source[branch]=main" \
  -f "source[path]=/docs"

# 5. Wait ~30–60 seconds, then verify the live Pages URL
open https://<username>.github.io/<slug>/
```

For private repos: replace `--public` with `--private`. Pages requires a paid GitHub plan for private repos.

If `gh` isn't authenticated: web-UI fallback. GitHub → New Repository → push the directory → Settings → Pages → Source = `main` branch / `/docs` folder → Save.

## When operator authorizes per-build deployment

If operator says "go ahead and push it" (the funeral build precedent), Foundry can:

1. **Replace the GitHub URL placeholder in `docs/index.html`** with the actual repo URL BEFORE first commit (so Pages deploys with working links)
2. **Run the deployment sequence** above
3. **Poll the Pages build** until built/errored via `gh api repos/<u>/<s>/pages/builds/latest`
4. **HTTP-check the live URL** once built
5. **Report the live URL** in the HAND OFF summary

Use Bash `run_in_background: true` with an `until` loop for the poll — single notification when complete. **Don't poll inline.**

Note: `status` is a read-only variable in zsh. Use a different name in the until-loop (`pgs_state` works).

## STATUS update template

Add to the worker's `STATUS.md` Recently-shipped section:

```markdown
- **YYYY-MM-DD — <slug> v1.0.** Buyer: <buyer>. Closest analog: <repo>. Architecture: <one-line>. Files: <count>. Grading: <which bars passed>. WebFetch budget: <used / planned> (<successes>/<attempts>; failure pattern: <if any>). Build at [`builds/<slug>/`](builds/<slug>/). Deployed to [<URL>](<URL>) (HTTP 200). Upstream breadcrumb appended.
  - <any per-build overrides operator authorized — name them explicitly>
  - <any pattern flags worth saving for future builds>
```

## Upstream-orchestrator breadcrumb

A single substantial line appended to whatever STATUS file the operator's parent orchestrator maintains. Format:

```markdown
- YYYY-MM-DD — **specialist-foundry** SHIPPED <slug> v1.0 at `<path-to-build>`. Buyer: <buyer>. Architecture: <one-line citing source-repo lifts>. Deployed to <URL> (HTTP 200). <key-overrides-or-pattern-flags>. <one-line about-what-HQ-orchestrator-should-know>.
```

The breadcrumb is **the only allowed write outside the worker's directory and the built specialist's directory.** Don't write elsewhere.

## When VERIFY failed but operator wants HAND OFF anyway

Refuse. VERIFY pass is a precondition for HAND OFF. If a row failed structurally (e.g., domain-grounded fails because the brief lacked content), file `briefs/questions/<slug>-question-final.md` surfacing what's needed. STOP.

If operator overrides — "ship it anyway, I'll fix later" — Foundry can comply BUT:

1. Tag the HAND OFF as `vUNVERIFIED-1.0` not `v1.0`
2. Note the override in STATUS.md
3. Note the override in the upstream breadcrumb

Don't silently ship a failing build.

---

Last updated: 2026-05-12.
