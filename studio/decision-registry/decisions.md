# Decision registry

Search this file before any significant architecture, gameplay or business decision. Follow an accepted decision unless new evidence justifies a change; a change is a new decision that supersedes the old one (never edit history away).

Status: proposed · accepted · superseded · rejected.

| ID | Date | Project | Title | Status |
|---|---|---|---|---|
| D-0001 | 2026-11-10 | studio | Research before code; owner approves the first game | accepted |
| D-0002 | 2026-11-10 | studio | Android first, iOS prepared later | accepted |
| D-0003 | 2026-11-10 | studio | Rewarded ads only by default; no forced interstitials | accepted |
| D-0004 | 2026-11-10 | studio | Repository structure: studio repo, framework repo, one repo per game | accepted |
| D-0005 | 2026-11-10 | studio | Technology: TypeScript + Capacitor 8, break_eternity.js, Vitest | accepted |
| D-0006 | 2026-11-10 | studio | Commercial scoring model with the brief's weights | accepted |
| D-0007 | 2026-11-10 | all | Reuse or extend existing functions; new ones only when needed | accepted |
| D-0008 | 2026-11-10 | game-001 | First game: Abyss Station | accepted |
| D-0009 | 2026-11-10 | studio | Publish with a personal Google Play developer account | accepted |
| D-0010 | 2026-11-10 | game-001 | Prestige currency (Charts) grows logarithmically | accepted |
| D-0011 | 2026-11-10 | studio | First-session pacing goals are measured in play time | accepted |
| D-0012 | 2026-11-10 | game-001 | Return-bonus ad: +50% of the offline haul, once a day | accepted |

## D-0001 Research before code; owner approves the first game

- Problem: avoid building a game without evidence of demand.
- Alternatives: start prototyping a favourite idea at once.
- Selected: Phase 1 research and ranking first; no game code until the owner chooses.
- Reasons: the owner's brief requires it; ad revenue per player is low, so the choice of niche matters most.
- Consequences: first deliverable is `studio/market-research/phase1-report.md`.

## D-0002 Android first, iOS prepared later

- Problem: limited time; two stores double release work.
- Alternatives: both at once; iOS first.
- Selected (accepted by the owner 2026-11-10): Android first; keep the code free of Android-only assumptions so iOS can follow.
- Reasons: owner's brief; no Mac needed to start; Apple Developer costs $99/year; research found no strong reason to launch both at once.
- Dependencies: D-0005 (the stack supports iOS).

## D-0003 Rewarded ads only by default

- Problem: forced ads are the most common cause of 1–2 star reviews in the competitor matrix.
- Alternatives: interstitials between sessions; banners.
- Selected (accepted by the owner 2026-11-10): opt-in rewarded ads with a daily cap; a one-time "ad-free" purchase that makes rewards automatic; no interstitials or banners unless later evidence supports them for a specific game.
- Reasons: community and review evidence (`raw/player-sentiment-and-niches-2026-11.md`, `raw/competitors-store-data-2026-11.md`); Egg, Inc. shows optional ads work at scale.
- Consequences: lower ad revenue per player than aggressive competitors; balance must not depend on ads.

## D-0004 Repository structure

- Problem: several games over time must not break each other.
- Alternatives: one monorepo for everything; framework copied into each game.
- Selected (accepted by the owner 2026-11-10): `MadGames` = studio control (research, registries, standards); `madgames-framework` = shared TypeScript package with semver tags; one repository per game pinning an exact framework version. Until game 001's vertical slice is proven, the framework lives in a `framework/` folder in game 001 and is split out afterwards.
- Reasons: isolation of released games; avoid designing a framework before knowing what is reusable.
- Dependencies: owner creates new GitHub repositories.

## D-0005 Technology

- Problem: choose an engine that an AI agent can build and test headlessly, with maintained ads and purchase plugins.
- Alternatives: Godot 4.7, Unity 6, Flutter + Flame, React Native/Expo (comparison in `studio/market-research/raw/tech-stack-2026-11.md`).
- Selected (accepted by the owner 2026-11-10; confirmed technically by a tiny Android test build in Stage B): TypeScript + Capacitor 8, break_eternity.js for big numbers, Vitest simulations in Node, @capacitor-community/admob with Google UMP consent, a maintained billing plugin; target SDK 36.
- Reasons: plain-text code and Node tests suit AI-assisted development; same family as G OPS, which the owner already runs; best maintained big-number library.
- Risks: community-maintained AdMob plugin (start AdMob-only, no mediation); WebView performance on low-end phones (keep effects modest, measure on a midrange device).

## D-0006 Commercial scoring model

- Selected: criteria and weights from the owner's brief (demand 20, competition 20, retention 20, monetization 15, dev efficiency 10, expansion 10, portfolio 5); scores 1–10 are judgement unless evidence is cited.
- Consequences: rankings in the Phase 1 report; re-score when validation data (fake-door tests, soft-launch KPIs) exists.

## D-0007 Reuse or extend existing functions; new ones only when needed

- Problem: duplicate functions that do nearly the same thing make the games harder to maintain.
- Selected (owner's instruction, 2026-11-10): read all `.md` files before adding a function; use or extend an existing function; make a new one only when no existing function can cover the feature or the extension would make the app slow to run; record it in the function registry.
- Consequences: every session reads the registries first (see `CLAUDE.md`); commit messages say why a new function was needed.

## D-0008 First game: Abyss Station

- Problem: choose the first game (Phase 1 Task 10).
- Alternatives: Alchemist's Atelier (7.20), Dig & Display (6.70), a one-week fake-door test of the top two.
- Selected: Abyss Station (score 7.55), the owner's choice 2026-11-10 ("let's go with your recommendations").
- Reasons: Phase 1 report §8 (current ocean demand, no polished deep-sea exploration idle on Play, zones as a content pipeline, code-drawn art).
- Consequences: game-001 starts Stage A; docs in `game-projects/game-001-abyss-station/docs/` until its repository exists.
- Known counter-arguments: Phase 1 report §8 (PC evidence, Alchemist's Atelier has the clearer mobile gap).

## D-0009 Personal Google Play developer account

- Problem: a personal or an organisation account.
- Selected: personal (owner, 2026-11-10).
- Consequences: before production access, a closed test with ≥ 12 testers opted in for ≥ 14 continuous days; testers are recruited during development (aim 15–20). The store shows the owner's name as developer unless changed later.
- Owner time: about 8 hours a week for testing and decisions; the roadmap is planned around one test build a week.

## D-0010 Charts grow logarithmically (game-001)

- Problem: with Charts = (Samples ÷ base)^0.33, each new station made the next run richer and Charts snowballed; the calibration could not hold back the late zones even with extreme requirements.
- Alternatives: lower power; caps per run.
- Selected: Charts on offer = floor(3 × (log10(Samples ÷ base) + 1)); each Chart +40% yield; the chart gate costs 29× more per ocean.
- Reasons: steady growth across oceans; calibrated so the average player reaches ocean 3 around day 53–59 and the hadal trench around day 160 (`abyss-station/reports/economy/latest.md`).

## D-0011 First-session goals in play time (studio)

- Problem: the brief's goals for the first 30 seconds / 5 minutes / 30 minutes are about playing time; measured in calendar time, a player whose first session ended after 8 minutes looked 10 hours late.
- Selected: the shared simulation runner records milestones in both calendar time and play time; each game lists which milestones count play time; profiles have a longer first session (new players look around).
- Consequences: applies to every future game using `@madgames/framework`.

## D-0012 Return-bonus ad +50%, once a day (game-001)

- Problem: doubling the offline haul (the biggest income for most players) made non-watchers 1.44–1.6× slower to the first new station, above the 1.3× fairness target (D-0003).
- Selected: +50% of the haul, once a day, after ≥ 30 min away. Non-watchers are now ~1.3× slower; the report flags anything above 1.35×.
