# Decision registry

Search this file before any significant architecture, gameplay or business decision. Follow an accepted decision unless new evidence justifies a change; a change is a new decision that supersedes the old one (never edit history away).

Status: proposed · accepted · superseded · rejected.

| ID | Date | Project | Title | Status |
|---|---|---|---|---|
| D-0001 | 2026-11-10 | studio | Research before code; owner approves the first game | accepted |
| D-0002 | 2026-11-10 | studio | Android first, iOS prepared later | proposed |
| D-0003 | 2026-11-10 | studio | Rewarded ads only by default; no forced interstitials | proposed |
| D-0004 | 2026-11-10 | studio | Repository structure: studio repo, framework repo, one repo per game | proposed |
| D-0005 | 2026-11-10 | studio | Technology: TypeScript + Capacitor 8, break_eternity.js, Vitest | proposed |
| D-0006 | 2026-11-10 | studio | Commercial scoring model with the brief's weights | accepted |

## D-0001 Research before code; owner approves the first game

- Problem: avoid building a game without evidence of demand.
- Alternatives: start prototyping a favourite idea at once.
- Selected: Phase 1 research and ranking first; no game code until the owner chooses.
- Reasons: the owner's brief requires it; ad revenue per player is low, so the choice of niche matters most.
- Consequences: first deliverable is `studio/market-research/phase1-report.md`.

## D-0002 Android first, iOS prepared later

- Problem: limited time; two stores double release work.
- Alternatives: both at once; iOS first.
- Selected (proposed): Android first; keep the code free of Android-only assumptions so iOS can follow.
- Reasons: owner's brief; no Mac needed to start; Apple Developer costs $99/year; research found no strong reason to launch both at once.
- Dependencies: D-0005 (the stack supports iOS).

## D-0003 Rewarded ads only by default

- Problem: forced ads are the most common cause of 1–2 star reviews in the competitor matrix.
- Alternatives: interstitials between sessions; banners.
- Selected (proposed): opt-in rewarded ads with a daily cap; a one-time "ad-free" purchase that makes rewards automatic; no interstitials or banners unless later evidence supports them for a specific game.
- Reasons: community and review evidence (`raw/player-sentiment-and-niches-2026-11.md`, `raw/competitors-store-data-2026-11.md`); Egg, Inc. shows optional ads work at scale.
- Consequences: lower ad revenue per player than aggressive competitors; balance must not depend on ads.

## D-0004 Repository structure

- Problem: several games over time must not break each other.
- Alternatives: one monorepo for everything; framework copied into each game.
- Selected (proposed): `MadGames` = studio control (research, registries, standards); `madgames-framework` = shared TypeScript package with semver tags; one repository per game pinning an exact framework version. Until game 001's vertical slice is proven, the framework lives in a `framework/` folder in game 001 and is split out afterwards.
- Reasons: isolation of released games; avoid designing a framework before knowing what is reusable.
- Dependencies: owner creates new GitHub repositories.

## D-0005 Technology

- Problem: choose an engine that an AI agent can build and test headlessly, with maintained ads and purchase plugins.
- Alternatives: Godot 4.7, Unity 6, Flutter + Flame, React Native/Expo (comparison in `studio/market-research/raw/tech-stack-2026-11.md`).
- Selected (proposed, to confirm in Stage B): TypeScript + Capacitor 8, break_eternity.js for big numbers, Vitest simulations in Node, @capacitor-community/admob with Google UMP consent, a maintained billing plugin; target SDK 36.
- Reasons: plain-text code and Node tests suit AI-assisted development; same family as G OPS, which the owner already runs; best maintained big-number library.
- Risks: community-maintained AdMob plugin (start AdMob-only, no mediation); WebView performance on low-end phones (keep effects modest, measure on a midrange device).

## D-0006 Commercial scoring model

- Selected: criteria and weights from the owner's brief (demand 20, competition 20, retention 20, monetization 15, dev efficiency 10, expansion 10, portfolio 5); scores 1–10 are judgement unless evidence is cited.
- Consequences: rankings in the Phase 1 report; re-score when validation data (fake-door tests, soft-launch KPIs) exists.
