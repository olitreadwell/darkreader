# darkreader/darkreader context
> refreshed 2026-09-03 | upstream default: main @ 6bfc605387a57fa329c64001db6e544ea9afc28a

## Identity & policies
- upstream: darkreader/darkreader, default branch main, primary language TypeScript, English-first (yes — README/CONTRIBUTING in English)
- CLA/DCO: none (no CLA bot, no signup required)
- AI-assisted PR policy: CONTRIBUTING says "Code changes predominantly generated with AI are not allowed" — applies to code; typo/doc fixes are not code changes. ai_disclosure_required=false in passport.
- signed commits required: no
- PR template: none (no .github/PULL_REQUEST_TEMPLATE.md) — use 3-section fallback body
- external tracker: github

## Conventions (verified from merged PRs)
- branch naming: mostly `Myshor-patch-*` / `patch-*` (GitHub web-edit default) and `fix-<kebab>` (e.g. fix-hmc-transcript-portal, fix-gmail-account-selector)
- commit style: short imperative summaries
- test command: `npm test`; lint: `npm run lint`; code-style: `npm run code-style`
- CI: GitHub Actions; substantive checks gate merge
- outside PRs merge: yes, frequently (Myshor, arturstat, CoolSpy3, etc. merged recently)

## Maintainer picture
- active maintainers: Myshor (very active, daily merges), arturstat, others
- areas actively worked: dynamic-theme-fixes.config site fixes, ironflex.pl, bestbuy.ca, garmin.com — avoid overlapping site-fix PRs

## Issue-area health
- high-volume site-fix config PRs dominate; docs/typo PRs are rare
- no contested/redesign signals relevant to trivial doc/typo fixes

## Gap ledger (dedupe — READ FIRST, never re-pick)
- (none yet — first run)

## Mined gaps (discovered, not yet attempted)
- 2026-09-03 CONTRIBUTING.md:126 "ommited" -> "omitted" — status: proposed
- 2026-09-03 CHANGELOG.md:11 "FIxed" -> "Fixed" — status: proposed
- 2026-09-03 src/ui/popup/components/loader/index.tsx:33 "A unknown error has occured" -> "An unknown error has occurred" — status: proposed
- 2026-09-03 README.md:5 `el="noreferrer noopener"` -> `rel="noreferrer noopener"` (broken HTML attr) — status: proposed
- 2026-09-03 docs/color-schemes-drconf.spec:49 `text: 3b4252` -> `text: #3b4252` (missing # prefix) — status: proposed

## Gap ledger (dedupe — READ FIRST, never re-pick)
- 2026-09-03 self-found typo/doc cleanup (5 fixes, 5 files) — outcome: pr-opened https://github.com/olitreadwell/darkreader/pull/1 — lesson: substantive CI (unit+lint) green; browser-test job fails on fork karma-adapter harness issue, unrelated to diff.
