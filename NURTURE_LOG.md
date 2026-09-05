# NURTURE_LOG — greenReporter.eu API Docs

> **Repo**: `greenreporter-api-docs`
> **Product**: greenReporter.eu — Public API Documentation
> **Tech Stack**: MkDocs Material | Python | GitHub Pages | Custom domain: docs.greenreporter.eu

---

## Market Readiness Score: 5.1/10 ➡️ (corrected from incorrect 6.5)

> **Updated**: 2026-08-25 16:06 IST | Cycle #48 (5.1 held — repo untouched 79 days (1786fef, Jun 7). June's P0 git-auth blocker RESOLVED portfolio-wide (verified again this cycle). New verified facts: docs.greenreporter.eu root serves **404** (user-visible symptom of the no-auto-deploy gap); the main app repo now tracks the OpenAPI YAML suite AND runs its own `docs.yml` — the machine-readable spec June wanted exists upstream, shifting this repo's question to *revive vs consolidate*.)
> **HEADLINE** (superseded Jun-17 note): score 5.1 unchanged; all June gaps except git-auth persist.

|| Dimension | Score | Trend | Notes |
|-----------|---------|-------|-------|
|| Architecture | 6.5/10 | ➡️ | MkDocs Material configured with full nav, plugins, extensions. 14 content pages. 50 nav entries in mkdocs.yml. |
|| Test Coverage | 2/10 | ➡️ | No validation. No `mkdocs build --strict` in CI. Broken nav links are undetected. |
|| Documentation | 7.0/10 | ➡️ | 14 content pages present. README still aspirational. |
|| Compliance Alignment | 5/10 | ➡️ | `openapi-spec.md` present (manually written). Still no machine-readable `openapi.yaml`. API contract could drift from implementation. |
|| Deploy Readiness | 5/10 | ➡️ | deploy-docs.ps1 exists (Windows only). CNAME configured. No CI/CD. No auto-deploy on push. Git auth broken. |

**Trend**: ➡️ Steady. The repository remains unchanged since the last content update (commit 1786fef on 2026-06-14). The previous Market Readiness Score of 6.5 was incorrect due to a calculation error; the correct average of the five dimensions is 5.1. All previously identified gaps persist.

---

## Unmet Compliance/Feature Traps

- 🔴 **Git auth broken (CROSS-PORTFOLIO P0 — 10th consecutive cycle)** — `gh auth status` = not logged in. Fix: `gh auth login` + `gh auth setup-git`.
- 🔴 **No CI/CD for auto-deployment** — Changes pushed to main don't trigger rebuild. Manual deployment only.
- 🔴 **No machine-readable OpenAPI spec** — `openapi-spec.md` is manually written. No `openapi.yaml`. Likely to drift from live API implementation.
- 🟡 **README claims non-existent features** — Lists auto-deployment, broken link detection, analytics — none actually implemented.
- 🟡 **Windows-only deploy script** — `deploy-docs.ps1` is PowerShell. No macOS/Linux equivalent.
- 🟡 **No `mkdocs build --strict` validation** — Broken internal links won't be caught before deploy.
- 🟡 **Content accuracy unknown** — Pages haven't been verified against the live API implementation.

---

## Next Sequential Implementation Target

### 1. [P1] Add CI/CD Pipeline for Auto-Deployment
Create `.github/workflows/docs.yml` that runs `mkdocs build --strict` on PR and `mkdocs gh-deploy` on merge to main. Catches broken links before they go live.

### 2. [P1] Generate Machine-Readable OpenAPI Specification
Create `docs/openapi.yaml` from the actual Supabase API surface. Wire into MkDocs via `redoc` or `swagger-ui-tag` plugin.

### 3. [P2] Verify Content Against Live API
Audit each documentation page against the actual API endpoints in the main app repo (`EU-Sustainability-Reporting-Tool-Development-1526`).

---

## Delta Since Last Cycle (Cycle #34, 2026-06-14)

- ➡️ **No content changes** — The last commit remains `1786fef docs: add 8 missing API documentation pages` (2026-06-14).
- ➡️ **All gaps unchanged** — No CI/CD, no openapi.yaml, git auth still broken.
- ✅ **Score correction** — Previous score of 6.5 was incorrect; the true average of the five dimensions is 5.1.
- Score: 6.5 (incorrect) → 5.1 (corrected).

---

### Delta Since Cycle #41 (2026-06-17 — first re-evaluation in 69 days; Cycle #48, 2026-08-25 16:06 IST)

- ➡️ **Repo completely unchanged**: origin/main = 1786fef (Jun 7, idle 79 days). No merged PRs since; `gh pr list --state merged` returns empty.
- ✅ **June's cross-portfolio P0 (git auth) RESOLVED** — restored 2026-08-25 (cycle #47) and re-verified green this cycle (`gh auth status` → iamasuperuser via keyring; `git credential fill` OK). The "10th/12th consecutive cycle" counters in this file are historical.
- 🔴 **New verified symptom**: `https://docs.greenreporter.eu/` → **HTTP 404** (GitHub Pages). The no-auto-deploy gap now has a user-visible failure: the docs domain serves nothing at root.
- ➕ **Upstream shift**: the main app repo (`EU-Sustainability-…-1526`) now tracks `openapi-main.yaml` + 4 companion OpenAPI YAMLs AND runs its own `docs.yml` workflow. The June gap "no machine-readable spec" is effectively closed *upstream* — the spec lives in the app repo, not here. Strategic question for the owner: revive this repo (port the YAML suite + add `mkdocs build --strict` CI) or consolidate docs into the app repo and archive this one.
- Score held 5.1/10 (dimension scores unchanged — nothing in this repo moved).

### Delta Since Cycle #48 (2026-08-25 16:06 IST — Cycle #49, 20:06 IST)

- ➡️ **Repo unchanged**: origin/main = 1786fef (Jun 7 — idle 79 days). No commits, no PRs, no reviews.
- 🔴 docs.greenreporter.eu root → **404 re-verified** (live probe) — the docs domain still serves nothing at root.
- ➡️ Revive-vs-consolidate decision still open (owner decision; see cycle #48 entry). Upstream app repo tracks the OpenAPI suite + its own `docs.yml`.
- Score held 5.1/10.

*Last evaluated: 2026-08-25 20:06 IST — Wintermute Repo Nurturer, Cycle #49*