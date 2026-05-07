# OAK Lens — Demo Prep Handoff

**What this folder is:** the complete handoff package for OAK Lens front-end demo prep. Audit findings, design decisions, build plan, and supporting assets — produced Saturday 2026-05-02 by Kit Anderson + Claude (browser-driven audit session) and dropped here for execution by the Claude agent in Tim's project folder.

**Demo target:** Monday 2026-05-04. Hak (President of Digital Marketing, Grandstand) test-drives the live OAK Lens app at `oaklens.io` on a tenant pre-seeded with Grandstand's actual roster (6 artists / 616 videos / 8.1B views). Stakes: $250M Sequoia-backed AI roll-up acquisition conversation. The product currently works at deal-closing-grade; the polish target is removing tells that signal "shipped fast" without restructuring anything that's working.

---

## Files in this folder, in reading order

### 1. `LENS_AUDIT_FRONT_END.md`  (read first)

The punch list. Every visible look-and-feel issue identified during the audit, ranked by tier (Tier 1 critical / Tier 2 high-leverage / Tier 3 polish), with cross-app patterns and per-page reference tables. Locked design decisions are baked in: Klein Blue accent tier, Satoshi + JetBrains Mono typography, custom SVG icon set, dual-mode token system. The CSS tokens, font import, and SVG markup are inlined for direct drop-in.

### 2. `LENS_BUILD_PLAN.md`  (read second)

The autonomous execution plan covering Phases 1–5, 7, 8. Tim's Claude runs this without humans. Self-validation gates between phases. Pre-baked decisions (dark mode default, Phase 5 always-attempt, engagement column relabel = Tim's Claude decides) eliminate the need to ping Kit during the build. Phase 6 is deferred to the sprint doc.

### 3. `LENS_TIM_SPRINT.md`  (read before Phase 6 work begins)

The Phase 6 backend sprint. Six items that touch backend logic, database writes, LLM API calls, or auth scoping — each requires Tim's explicit approval before code lands. Approval-request format spec'd at the top so Tim's Claude knows exactly what to present to Tim. Skip-the-sprint contingency documented at the bottom.

### 4. `oaklens-tokens.css`  (drop-in source)

Self-contained CSS file with the full dual-mode token system (light cream paper + warm coffee dark). Identical content to §1 of `LENS_AUDIT_FRONT_END.md`. Provided as a separate file in case dropping a CSS file directly is easier than copy-pasting from markdown.

### 5. `oaklens-icon-preview.html`  (visual reference)

Standalone HTML preview of the 9 SVG icons in their card containers, plus a side-by-side comparison of the current emoji set vs the proposed SVG set. Open in a browser to see the icons rendered. Identical SVG markup is inlined in §3 of `LENS_AUDIT_FRONT_END.md`.

---

## Reading order for an agent picking this up cold

1. This README.
2. `LENS_AUDIT_FRONT_END.md` — understand the full punch list and design decisions.
3. `LENS_BUILD_PLAN.md` — understand the autonomous execution plan.
4. `LENS_TIM_SPRINT.md` — only when Phase 5 self-validation passes and the Phase 6 approval gate is reached.

The HTML and CSS files are referenced from the markdown — open them when the markdown points there.

---

## Roles

- **Tim's Claude** — sole executor for the build. Runs Phases 1–5, 7, 8 autonomously per `LENS_BUILD_PLAN.md`. Halts at the Phase 6 approval gate to engage Tim per `LENS_TIM_SPRINT.md`.
- **Tim** — only human in the loop. Approves Phase 6 work before any backend code lands. Resolves boundary-item escalations and runtime calls Tim's Claude can't decide from the spec.
- **Kit** — out of the loop after handoff. Provided these documents as the input; hands-off after that.

---

## Status (as of 2026-05-02 evening)

- Audit complete. All 11 routes audited from both superadmin and tenant-admin perspectives.
- Design decisions locked: accent (Klein Blue tier), typography (Satoshi + JetBrains Mono), iconography (9-icon SVG set + 3 trajectory icons), background (dark warm coffee default with light cream paper available).
- Build plan and Tim sprint docs delivered.
- Awaiting Sunday execution per the time-of-day schedule in `LENS_BUILD_PLAN.md`.

---

End of README.
