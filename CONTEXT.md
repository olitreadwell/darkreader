# darkreader/darkreader context
> refreshed 2026-10-12 | upstream default: main @ a7c9dc70238245d90ce4ffdd3666a0861bf1c7ce

Fork main was 11 commits behind upstream at the start of this run and was
fast-forwarded with the repos merge-upstream API (fork main b4fb44b -> a7c9dc7,
now identical to upstream main).

## Identity & policies
- upstream: darkreader/darkreader, default branch main, primary language TypeScript, English-first (yes: README, CONTRIBUTING, SECURITY, issue templates and all recent PR/issue conversation in English)
- CLA/DCO: none (no CLA bot, no signup requirement found in CONTRIBUTING or on merged external PRs)
- AI-assisted PR policy: CONTRIBUTING.md:248 "Code changes predominantly **generated with AI are not allowed**." CONTRIBUTING.md:249 "All comments and conversations must be held by humans." Read as a CODE-ONLY ban: source/test/task-file changes are out of scope for this pipeline; docs-only corrections stay in scope (a previously disclosed-AI docs PR was reviewed by the maintainer without an AI objection). ai_disclosure_required=false in the policy passport.
- signed commits required: no
- PR template: none (no .github/PULL_REQUEST_TEMPLATE.md in the repo; darkreader/.github org repo returns 404 for contents) — use the 3-section fallback body
- external tracker: github
- other CONTRIBUTING rules that gate a merge: "**Low effort contributions** are not allowed"; "A single pull request should have a single purpose"; "**Keep the changes simple**"; "**Please preserve the code style**"; bugs/features need an issue + maintainer approval first (issue-first for those, not for docs)

## Conventions (verified from merged PRs, 2026-10-12)
- branch naming: no dominant convention — GitHub web-edit defaults `patch-<N>` (4073 merged) and `<user>-patch-*` (e.g. Myshor-patch-*, gusted-patch-*), plus `bump-dependencies`/`deps`; no docs/typo branch pattern is evident. Fall back to `fix/<kebab>`.
- commit style: short imperative summaries ("Fix updating filtered image selectors")
- test command: `npm test` (jest unit; 16 suites / 75 tests green on Node 20.20.2, 2026-10-12); lint: `npm run lint`; code-style: `npm run code-style` (alias of lint); browser/inject suites need a real browser (`npm run test:browser`, karma)
- CI: GitHub Actions — test.yml (unit) + test-code.yml (lint + lint:bundle) + test-browser.yml (karma); all workflows pin node-version 22.x
- outside PRs: merged frequently and quickly; Myshor reviews external PRs with detailed feedback within days

## Maintainer picture
- active maintainers: Myshor (very active — reviews and merges daily, writes specific review feedback), arturstat (daily site-fix config PRs), dependabot
- areas actively worked: dynamic-theme-fixes.config site fixes (bestbuy.ca, falke.com, burlington.de, ...); issue #16044 core CSS parser investigation (empty custom properties / Vuetify 4) — see issue-area health

## Issue-area health
- #16044 (label bug, OPEN, 10 comments, updated 2026-10-12): "[Bug] Dark Reader drops empty CSS custom properties, breaking Vuetify 4 grids". Myshor reproduced it himself and named the root cause ("Dark Reader drops empty custom properties"), and is working on a global `*`-section config workaround while keeping the issue open for the core-engine fix. NO-GO for this pipeline: the fix is a core parser CODE change (AI-code ban) and the area is claimed by the maintainer (duplicate risk).
- The rest of the open backlog is dominated by per-site Broken Website reports and site-fix config requests. They need a real browser plus the site itself to reproduce, so they are not verifiable with the repo's own CI here.
- Docs/typo PRs are rare in this repo but are accepted (see the gap ledger) and none of the findings below collide with a maintainer's in-flight work.

## Gap ledger (dedupe — READ FIRST, never re-pick)
- 2026-09-03 self-found doc/typo cleanup (5 fixes, 5 files) — outcome: pr-opened https://github.com/olitreadwell/darkreader/pull/1
  - maintainer review 2026-09-10 (Myshor, CHANGES_REQUESTED): "Please revert changes to CHANGELOG.md (we don't modify historical release logs). Also, changes to index.tsx belong in a separate PR or the PR title needs an update. README.md fix is valid. And the rest of the changes are fine as-is."
  - lesson: NEVER touch CHANGELOG.md — historical release logs are frozen. The README attribute fix and the CONTRIBUTING/spec typos are explicitly accepted by the maintainer. The index.tsx user-facing string is maintainer-sanctioned only as its OWN PR and it is a source file (AI-code ban) — Oli's call, not this pipeline's.
  - upstream promotion 2026-09-11: https://github.com/darkreader/darkreader/pull/15984 was CLOSED unmerged (closed by olitreadwell after the review above; not merged upstream).
- 2026-09-25 and 2026-09-26 engine failures (engine/run.sh exited 1, no trace left) — outcome: error.
- 2026-10-12 self-found doc corrections (3 fixes, 3 files) — outcome: pr-opened (this run) — lesson: see the mined-gaps entry below.

## Mined gaps (discovered, not yet attempted)
- 2026-10-12 README.md:4 `el="noreferrer noopener"` -> `rel="noreferrer noopener"` (invalid HTML attribute on the Thunderbird badge; all 20+ other badge anchors in the file use `rel=`) — status: attempted this run (maintainer already called it "valid" on #1)
- 2026-10-12 CONTRIBUTING.md:126 "The `www` part should be ommited." -> "omitted" — status: attempted this run (maintainer called it "fine as-is" on #1)
- 2026-10-12 docs/color-schemes-drconf.spec:49 `text: 3b4252` -> `text: #3b4252` (the doc's own syntax rule says `#6-or-3-length-hex-color`, and `isValidHexColor` in src/utils/colorscheme-parser.ts:36 requires the `#`) — status: attempted this run (maintainer called it "fine as-is" on #1)
- 2026-10-12 src/ui/popup/components/loader/index.tsx:33 "A unknown error has occured" -> "An unknown error has occurred" — status: proposed (maintainer asked for it as a separate PR; blocked here by the code-AI ban; Oli's call)
- 2026-10-12 src/utils/colorscheme-parser.ts:1-2 + tasks/code-style.js:58-65 misspelled identifier `SEPERATOR`/`promisses` — status: dropped (a rename is a code refactor, not a trivial fix, and source edits are under the AI-code ban)
- 2026-10-12 CHANGELOG.md:30 "FIxed", :190 "performace", :272 "loosing" — status: dropped (maintainer: do not modify historical release logs)

## Exhaustive-search evidence (so later runs need not repeat it)
- codespell 2.4.3 over the whole tree (2026-10-12): after the three fixes above the only remaining hits are deliberate test fixtures / config data (e.g. `caf`, `bund`, `rythm`, `fo`, `nd` inside src/config/*.config domain and selector strings) — no genuine docs typos left.
- Every URL in README.md, CONTRIBUTING.md, SECURITY.md, CODE_OF_CONDUCT.md, integrity/README.md and docs/color-schemes-drconf.spec was re-checked with `curl -sSL -o /dev/null -w '%{http_code}'` (2026-10-12): no 404/410/DNS failures. The only non-200s were anti-bot 403s (addons.thunderbird.net, two opencollective sponsor pages) and one transient 522 (opencollective sponsor page) — false positives per config.link_check.false_positive_rules.
- A doubled-word scan over all markdown files found no genuine repeats.
