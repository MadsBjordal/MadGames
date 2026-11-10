# MadGames studio: conventions for every session

- This repository is the **studio control** repository: research, portfolio registry, decision registry, function registry index, standards. Game code lives in per-game repositories (D-0004).
- **Owner is not a professional developer** and uses Windows. Explain in plain language; at the end of each milestone say how to run it and what to test by hand.
- **Start of every session:** identify the game from the request (never assume the most recently modified one); read `studio/portfolio-registry/registry.md`, the game's docs, `studio/decision-registry/decisions.md`, the function registries and the backlog; check the branch, versions and repository state; then continue.
- **Reuse before you write (owner's rule, 2026-11-10, very important):** before adding any new function, read all `.md` files of the studio and of the game (registries, decisions, design docs, framework docs). Use an existing function, or extend it if needed, rather than making a new one. Make a new function **only** when no existing function can cover the requested feature, or when extending one would make the app slow to run. When you do make or extend one, record it in the function registry in the same commit.
- **Decisions:** search the decision registry first; record every notable choice there; never silently reverse one (a new decision supersedes it).
- **Numbers:** never invent downloads, revenue, eCPM or KPIs. Mark [V] verified, [E] estimate, [H] hypothesis.
- **Approval needed for:** game selection, major gameplay or architecture changes, paid services, production credentials, live monetization changes, any publishing/release, destructive changes. Never merge, deploy or release silently.
- **Never commit secrets** (ad unit IDs for production, signing keys, tokens). Use test ads in development.
- **Studio Status:** when asked, report every game from the portfolio registry (stage, version, priority, next action), plus risks, blockers and dependencies; KPIs only from connected sources.
- Phase 1 report: `studio/market-research/phase1-report.md`; raw research with sources: `studio/market-research/raw/`.
