# Phase 1 report: market research and first-game recommendation

Date: 2026-11-10 · Status: **waiting for the owner's decision** (Task 10) · No game code has been written.

How to read the numbers in this report:

- **[V] verified:** read on an official page (store listing, platform docs, developer statement).
- **[E] estimate:** a third-party tracker (AppGoblin, SteamDB/nodal.gg review counts, DataEye) or a vendor benchmark. These are directional, often several times apart between sources.
- **[H] hypothesis:** my judgement or assumption. All scores and all revenue scenarios are [H].

The raw notes with every source URL are in `raw/`. Reddit itself could not be read from this session (blocked); Reddit evidence comes from a public archive of r/incremental_games. The specific thread in the brief (`1rjistw`) could not be read; a closely matching thread ("what happened to long incrementals?", April 2026) was used instead.

---

## 1. Summary for decision

1. **Recommended first game: _Abyss Station_** (working title), a deep-sea research idle game. You run a research station that sends probes and crews ever deeper. Each depth zone has its own rules (light, pressure, heat vents, the trench). You catalogue living species, keep them in a living reef whose food web gives bonuses, and you prestige by founding the next station in a new ocean with a different twist.
2. **Why this one:** ocean-themed idle games have the strongest *recent* evidence of demand (Shelldiver 18,200 Steam reviews at 99% [E], Chillquarium 8,422 [E], Cast n Chill 8,756 [E]). Yet on Google Play I found **no current, well-made deep-sea exploration idle game** (searches turned up casual submarine games and browser prototypes only). It fits the long-term structure players praise (new zones = new rules), the collection loop mainstream mobile players like, and a glowing-on-black art style that we can largely draw in code (cheap and consistent).
3. **Close second: _Alchemist's Atelier_**, discovery plus production. It has proven adjacent demand (Little Alchemy 2 ≈ 17.8M Android installs [E]) while existing *idle* alchemy games on Play are small (≤ ~180K installs [E]). It's the clearer gap; the ocean has the stronger trend and visual hook.
4. **Business reality:** ads alone pay little per player. A planning figure is **~$0.01–0.05 per daily player per day** [E/H]. 1,000 daily players ≈ $10–50/day. Paid advertising will not pay back at first, so the game must grow through Play Store search, word of mouth and long retention. Quality and retention matter far more than release speed.
5. **Technology (proposed, to confirm in Stage B):** TypeScript + Capacitor 8 (the same family as G OPS), with `break_eternity.js` for big numbers, simulation tests in Node, AdMob rewarded ads with Google's consent form, and optional one-time purchases.
6. **What I need from you:** pick the concept (Task 10, section 11).

---

## 2. Task 1 — The market

### 2.1 Two markets, not one

| | Hardcore incremental players | Mainstream mobile idle players |
|---|---|---|
| Where | r/incremental_games, Steam, browser, Discord | Google Play / App Store, portrait |
| Want | interlocking systems, real choices, automation, offline progress, an active developer | short sessions, offline earnings, tidy upgrades, collecting, events |
| Money | happily pays once ($5–20); hates games balanced around ads or pay-to-win | accepts optional rewarded ads; hates forced ads |
| Length | split: 80–100 h to years, *and* 2–10 h polished games | endless if there are goals |

Our design target sits where these overlap: **a simple, attractive first hour (mainstream) that keeps opening new systems for months (hardcore)**. CIFI is the proof on mobile: the most-named "long and still enjoyable" game in the community thread, played daily for three years by one commenter.

### 2.2 Scale of the field (selected)

- Idle Miner Tycoon: 150M downloads by Sept 2022 [V, Kolibri press release].
- The Tower – Idle Tower Defense: ~$65M lifetime revenue with 4 staff [E, DataEye]; ~5.9M Android installs [E].
- Idle Museum Tycoon: Art Empire: ~5.5M installs, ~68.9K ratings [E], reviews complain of aggressive purchases.
- Little Alchemy 2: ~17.8M Android installs [E] (not an idle game; discovery puzzle).
- Steam breakouts 2023–26: Nodebuster 14,078 reviews, Gnorp Apologue 9,971 (120K+ sold in a month), The Farmer Was Replaced 9,633 ($1.65M in 3 weeks), Rusty's Retirement 14,872 (200K sold in ~2 weeks) [E/dev statements].

### 2.3 Competitor matrix (40 titles)

Read from the live US store listings on 2026-11-10 [V]. Play installs are the public band; ratings are Play's star average (number of ratings). Steam = % positive of reviews (EN = English only). "Updated" = last store update; a date within ~3 months means actively updated. Money: A = ads (mostly rewarded), I = in-app purchases, S = subscription, P = premium price. Full data, review quotes and sources: `raw/competitors-store-data-2026-11.md`.

| Title | Kind | Google Play installs | Play rating (count) | Steam | Updated | Money | Strength | Main complaint |
|---|---|---|---|---|---|---|---|---|
| Idle Miner Tycoon | mainstream | 100M+ | 4.5 (5.87M) | — | Nov 2026 | A I | relaxing, polished | pop-up flood even for no-ads buyers; "plays itself" |
| Idle Lumber Empire | mainstream | 100M+ | 3.9 (1.13M) | — | Oct 2026 | A I | scale | crashes returning from ads; 10-min ads |
| Eatventure | mainstream | 50M+ | 4.7 (423K) | — | Oct 2026 | A I | no forced ads | repetitive later |
| Grow Castle | mainstream | 10M+ | 4.3 (473K) | — | Nov 2026 | A I | fair purchases, depth | wants more content |
| Idle Bank Tycoon | mainstream | 10M+ | 4.6 (772K) | — | Nov 2026 | A I S | short optional ads | "wrapper around ads/spending" |
| Cell to Singularity | crossover | 10M+ | 4.5 (400K) | 85% of 11,444 (EN) | Nov 2026 | A I | educational, calm, not pushy | crashes, lost progress after updates |
| Egg, Inc. | mainstream | 10M+ | 4.7 (1.41M) | — | Aug 2026 | A I | ads fully optional; missed days not punished; humour | none recurring |
| AdVenture Capitalist | mainstream | 10M+ | 4.5 (1.64M) | 85% of 38,595 (EN) | Nov 2026 | A I S | simple, events | intrusive ads; ~$15/month ad-free plan |
| Idle Outpost | mainstream | 10M+ | 4.5 (168K) | — | Aug 2026 | A I | scale | stingy events; 120 s ads without reward |
| Tap Titans 2 | mainstream | 10M+ | 4.6 (1.07M) | — | Nov 2026 | A I | polished, ads by choice | inventory bugs |
| AdVenture Communist | mainstream | 10M+ | 4.3 (261K) | 62% of 3,318 (EN) | Oct 2026 | A I | long time-killer | rework removed purchases; scam ads |
| Idle Factory Tycoon | mainstream | 10M+ | 4.6 (342K) | — | Jun 2026 | A I | time-spender | 24 h unlock timers; reworks |
| Make It Rain | mainstream | 10M+ | 3.8 (313K) | — | Nov 2026 | A I | — | ads "every five seconds" |
| Realm Defense | mainstream | 5M+ | 4.4 (441K) | — | Oct 2026 | A I | — | (not sampled) |
| Idle Slayer | crossover | 5M+ | 4.6 (135K) | 78% of 4,375 (EN) | Oct 2026 | A I | pixel art, music | dev slowed game; failed rewarded ads |
| Clicker Heroes | crossover | 5M+ | 4.2 (128K) | 88% of 28,690 (EN) | Oct 2026 | A I | not pay-to-win | needs an auto-clicker |
| Shop Titans | mainstream | 5M+ | 4.2 (182K) | 76% of 6,348 (EN) | Nov 2026 | I S | charming art | unworkable without paying |
| Idle Planet Miner | mainstream | 1M+ | 4.4 (102K) | — | Nov 2026 | A I | depth; no-ads purchase worth it | tournament pay-to-win |
| AdVenture Ages | mainstream | 1M+ | 4.3 (38.1K) | — | Sep 2026 | A I S | easy to leave running | premium sub still shows ads; "re-skin" |
| Realm Grinder | deep | 1M+ | 4.0 (39.9K) | 86% of 4,113 (EN) | Oct 2026 | A I | factions make runs differ | slow gaps, flat late game |
| Antimatter Dimensions | deep | 1M+ | 4.8 (36.2K) | 91% of 3,453 (EN) | Nov 2026 | A I | layered resets; finishable (~194 days) | long walls |
| Swarm Simulator: Evolution | deep | 1M+ | 4.3 (11.2K) | 77% of 561 | Feb 2026 | A I | graphics | need ~$10 no-ads; slow first ascension |
| Exponential Idle | deep | 1M+ | 4.7 (33.9K) | — | Sep 2026 | A I | cheap permanent ad bonus; nothing behind ads | progress graph not useful |
| Leaf Blower Revolution | deep | 1M+ | 4.7 (9.46K) | 94% of 22,647 (EN) | Nov 2026 | I | new mechanics keep appearing; no ads | wants more offline |
| Melvor Idle | deep | 500K+ | 3.7 (12.6K) | 92% of 8,675 (EN) | Sep 2026 | P I | "RuneScape without playing it" | won't run when servers down; paywall |
| Idle Research | deep | 500K+ | 4.3 (8.32K) | 83% of 1,915 | May 2026 | A I | dev commentary | forced landscape; mixed text sizes |
| Revolution Idle | deep | 500K+ | 4.8 (44.5K) | 86% of 7,636 (EN) | Sep 2026 | A I | strategy keeps opening | mid-game needs a Discord guide |
| CIFI | deep | 500K+ | not shown | — | Oct 2026 | A I | "years of content" (community) | (not sampled) |
| Farmer Against Potatoes Idle | deep | 100K+ | 4.0 (3.41K) | 94% of 4,701 (EN) | Aug 2026 | I | content, offline, earnable premium | crude art; cluttered phone UI |
| Kittens Game | deep | 50K+ | 4.5 (3.37K) | 94% of 78 | Jul 2026 | I (donations) | no ads or pressure | few |
| Unnamed Space Idle | deep | 50K+ | 4.4 (818) | 92% of 3,026 (EN) | Nov 2026 | I | fair pacing | too many tabs and terms early on mobile; small buttons |
| Your Chronicle | deep | 50K+ | 4.3 (563) | 80% of 1,521 (EN) | Aug 2026 | A I | story-driven, endings | quality-of-life behind paywall; no dark mode |
| Synergism | deep | 1K+ | 4.8 (33) | 73% of 308 | Aug 2026 | I | NGU-level depth | confusing UI; stacked modifiers |
| Idle Wizard | deep | not found on Play | iOS 4.85 (1,811) | 86% of 1,869 | Nov 2026 (iOS) | I | not pay-to-win | ~10 currencies within 2 h |
| NGU Idle | deep | not on mobile | — | 95% of 10,966 (EN) | — | I | depth, honest | time sink |
| NGU Industries | deep | not on mobile | — | 77% of 1,574 | — | I | — | (not sampled) |
| Trimps | deep | not on mobile | — | 90% of 1,514 | — | I (optional) | generous offline, attentive dev | addictive |
| Evolve | deep | web only | — | — | GitHub active | free | cult classic | — |
| Theresmore | deep | web only | — | — | v1.2 | free | — | — |
| Gooboo | deep | web/itch only | — | — | v1.6.3 | free | — | — |

### 2.4 What the matrix tells us [H]

1. **The mainstream top (10M–100M+) is owned by large publishers** (Kolibri/Ubisoft, AppQuantum, Hyper Hippo, Miniclip). We should not compete head-on with their themes.
2. **The deep games that are on mobile sit at 50K–1.5M installs** and are rated very well (4.4–4.8). Several of the best-loved deep games are **not on mobile at all** (NGU, Trimps, Evolve, Theresmore, Gooboo) or are badly adapted (landscape, small buttons, too many tabs). A deep game that is **properly designed for a phone** is a gap.
3. **The same complaints repeat across the big mainstream games:** forced or failing ads, subscriptions that still show ads, pop-up floods, pay-to-win events. Egg, Inc. (4.7 from 1.41M ratings) shows that optional ads and not punishing missed days can work at scale.
4. **Mobile UI quality is a recurring weakness of deep games** (Unnamed Space Idle, Synergism, Farmer Against Potatoes, Idle Research, Idle Wizard). This is where we can be better by design: progressive tabs, large touch targets, portrait, dark mode.

Reported business figures [V/E]: Ubisoft took 75% of Kolibri Games (2020, price undisclosed; €160M valuation reported); Idle Miner Tycoon + Idle Factory Tycoon ≈ $1.6M/month (2020 report, E); Hyper Hippo's AdVenture games 80M+ installs; Eatventure's studio sold to Miniclip (≈ $29.4M IAP, 69.3M downloads, AppMagic E).

---

## 3. Task 2 — Why players quit, and what we do instead

| Why players quit (evidence) | Our rule |
|---|---|
| Forced ads; balance built around ads ("people don't mind ads, they mind when the balance was formed with ads", top reply, 61 points) | Rewarded only, opt-in, capped per day. The game is balanced **without** ads; an ad gives convenience, never a requirement. No forced interstitials. |
| Paid ad removal that still shows ads | "Remove ad offers" purchase turns rewards automatic; tested in CI. |
| Prestige with negligible benefit | Each prestige layer unlocks a new *rule* or system (a new ocean, a new zone mechanic), not only a multiplier. |
| Number goes up, nothing changes | Every 10–40 minutes early, every few days later, something that changes how you play. |
| Long games go stale ("just collecting more bonuses of the same thing") | New zones with different rules; finite, completable collections; an ending per layer. |
| Too little automation / no offline progress | Automation is an early unlock; full offline progress with a clear "while you were away" summary. |
| Abandoned games, lost saves | Versioned saves with migrations and backups from day one; a visible public roadmap. |
| Landscape-only, PC-first UI | Portrait first, one-thumb play. |
| Overwhelming choice for casual players ("overwhelms my peanut sized brain") | Every system has a sensible default and a "recommended" hint; depth is optional, not required. |
| Excessive time gates | Waits are short early; long waits are always paired with something else to do. |

Little direct 2025–26 evidence was found for lost saves and time gates as *current* complaints [H: still worth guarding against].

---

## 4. Task 3 — Niches (12+ evaluated)

Scale 1–5 (5 = best for us). Evidence in `raw/player-sentiment-and-niches-2026-11.md`.

| Niche | Demand evidence | Competition (direct) | Dev difficulty | Content upkeep | Retention | Ads fit | Differentiation | Main risk | Confidence |
|---|---|---|---|---|---|---|---|---|---|
| Deep sea / ocean exploration | 5: Shelldiver, Chillquarium, Cast n Chill on Steam; Abyssrium on mobile (older, aquarium) | 4: no current deep-sea exploration idle found on Play | 3 | 3 (zones + species) | 4 | 4 | 4 | Steam trend may not carry to mobile | Medium |
| Alchemy / discovery | 4: Little Alchemy 2 ~17.8M [E]; Potion Craft ~16K Steam reviews | 4: idle alchemy apps ≤ ~180K installs [E] | 3 | 3 (recipes) | 4 | 4 | 4 | Discovery is finite; needs production depth | Medium |
| Archaeology + museum | 4: Digseum 8,169 (98%); Idle Museum Tycoon ~5.5M [E] | 3 | 3 | 3 (artifacts) | 4 | 4 | 3 | Art volume; museum tycoons exist | Medium |
| Programming / automation | 4 on PC (Farmer Was Replaced, Bitburner, Upload Labs) | 4 on mobile | 2 (hard on a phone UI) | 3 | 5 | 3 | 4 | Typing logic on a phone is awkward | Low-medium |
| Power grid / infrastructure | 2: no game found, no demand found | 5 | 3 | 3 | 4 | 4 | 4 | May be dull to mainstream | Low |
| Logistics / transport | 3: several small apps, Supply Chain Idle 384 reviews | 3 | 2 (maps, routing) | 3 | 4 | 4 | 3 | Map UI is costly | Low-medium |
| Ecosystem / evolution | 4: Cell to Singularity 28,213 reviews | 2: one dominant game | 3 | 3 | 4 | 4 | 2 | Head-on with Cell to Singularity | Medium |
| Space colony / terraforming | 3: Space Colonizers ~1M [E] | 2 (space common) | 3 | 3 | 4 | 4 | 3 | Crowded space theme | Medium |
| Civilisation / history | 3: CivIdle ~1,076 reviews; Kittens, Theresmore (browser) | 3 | 2 | 2 (heavy) | 5 | 3 | 3 | Complex, hardcore-only | Medium |
| Beekeeping | 2: emerging cozy titles (Beellionaire Idle, demos) | 4 | 3 | 3 | 3 | 4 | 3 | Small, cozy-desktop focus | Low |
| Mushroom / fungus networks | 1–2: prototypes only | 5 | 3 | 3 | 3 | 4 | 4 | Unproven demand | Low |
| Library / knowledge | 1: nothing found | 5 | 4 | 3 | 3 | 3 | 4 | Unproven demand | Low |
| Weather / geology | 1: nothing found | 5 | 3 | 3 | 3 | 3 | 4 | Unproven demand | Low |
| Railway | 2–3: small apps only | 3 | 2 | 3 | 3 | 4 | 2 | Generic tycoon trap | Low |
| Restaurant / mining / farming | 5 | 1: saturated | 4 | 3 | 3 | 5 | 1 | Can't stand out | High (that it's crowded) |
| Dungeon / RPG idle | 5 | 1: well served (Melvor, IdleOn, Idle Champions) | 2 | 2 | 5 | 4 | 2 | Content-hungry | High |

**Cheap ways to validate a niche before building it** [H]:

1. Store search check: search Play for the theme in English, German, Polish, Norwegian; note top results' install bands and last update.
2. "Fake door" store page: put a styled landing page with art and a newsletter/pre-register link; count sign-ups from a small Reddit / Discord post (r/incremental_games allows dev posts on certain days).
3. Pre-registration on Google Play once the closed test exists.
4. A playable web prototype (vertical slice) on itch.io: measure session length and return visits before building the Android app.

---

## 5. Task 4 — Concepts (16 original)

Each concept is described compactly; the top three are expanded in section 7. "Ads" = rewarded-ad placements; "IAP" = optional purchases.

**C01 Abyss Station** (deep-sea research). Theme: a research station descending into an alien-feeling but real ocean. Audience: broad, cozy-curious and hardcore. Loop: send probes → collect samples and data → fund deeper dives → automate with drones and crews. USP: each depth zone has its own rule (sunlight zone: photosynthesis; twilight: bioluminescent lures; midnight: pressure limits hull upgrades; vents: heat economy; trench: rare one-off discoveries), and a living reef where species form a food web that gives bonuses. Satisfaction: discovering and naming species, the descent counter, the reef growing. Automation: drones, crew shifts, auto-sampling. Prestige: found a new station in another ocean (Arctic: ice; volcanic: unstable vents) keeping knowledge (research) and some species. Mid-game: expeditions (choose crew/gear for timed dives), the reef food web. Endgame: the Hadal layer, ocean-wide research, completable codex, challenge oceans. Ads: double samples on return, an extra expedition slot for an hour, "sonar ping" reveals the next discovery. IAP: remove ads/auto rewards, cosmetic station skins, a supporter pack. Difficulty: medium. Competition: low on Play for this exact take; Abyssrium is an older aquarium tapper. 12+ months: yes, via oceans and zones. Opportunity: strongest balance.

**C02 Alchemist's Atelier** (discovery + production). Loop: combine reagents to discover recipes → produce potions on automated benches → sell to a shifting market of customers with requests. USP: discovery (like Little Alchemy) inside an idle economy; recipes are hints, not a wiki chore. Automation: apprentices, distillation chains. Prestige: the Great Work (transmutation) moves you to a new school (astral, elemental, living) with new rules. Ads: an instant customer rush, doubled brew, a hint. IAP: ad removal, cosmetic atelier styles, hint pack (never required). Difficulty: medium. Competition: idle alchemy small. 12+ months: yes if schools are distinct.

**C03 Dig & Display** (archaeology + museum curation). Loop: excavate layers → clean and identify finds → curate exhibits; themed sets give visitor bonuses. USP: curation as strategy (set bonuses, room layout). Automation: dig teams, conservators. Prestige: new site and civilisation. Ads: extra visitors, fast restoration. IAP: ad removal, cosmetic halls. Difficulty: medium-high (art volume). Competition: Idle Museum Tycoon (~5.5M [E]) on the museum side.

**C04 Clockwork Guild** (programmable automatons). Loop: build automatons and give them simple rule cards ("when bin is full → carry to furnace") on a tile workshop. USP: the automation-by-programming trend, made touch-friendly with cards instead of code. Prestige: new workshop with new parts. Difficulty: high (UI). Competition: none on mobile found. Risk: complexity for mainstream.

**C05 Gridline** (power grid through the eras). Loop: build generation, match a day/night demand curve, add storage and transmission; prestige = new era (steam → renewables → fusion). USP: balancing supply and demand is a real decision. Difficulty: medium. Risk: unproven demand.

**C06 Parcel Atlas** (logistics network). Loop: hubs and routes on a stylised map, sorting automation, contracts. Prestige: new continent with new geography rules. Difficulty: high (map, routing). Competition: small apps.

**C07 Mycelium** (fungal network under a forest). Loop: spread hyphae, trade nutrients with trees, grow fruiting bodies, survive seasons. USP: symbiosis web. Difficulty: medium. Risk: unproven.

**C08 Terraform** (one planet, interacting parameters). Loop: atmosphere, temperature, water, life; each parameter changes the others. Prestige: next planet type. Competition: space theme is crowded.

**C09 The Endless Library** (knowledge collection). Loop: scribes copy, scholars research, rare books unlock branches; Borges-style humour. Difficulty: low-medium. Risk: unproven.

**C10 Apiary** (bees and genetics). Loop: hives, flower fields, breeding queens with traits, honey market. USP: breeding as long-term depth. Competition: emerging cozy titles.

**C11 Ministry of Forms** (humorous bureaucracy). Loop: stamp, file, expand ministries; absurd regulations as upgrades. USP: humour, Universal Paperclips-style narrative. Retention: lower; best as a shorter premium game.

**C12 Lighthouse & Tide** (sailing trade routes from a harbour). Loop: ships, routes, tides, weather. Competition: moderate.

**C13 Railbound Frontier** (railway). Generic tycoon risk.

**C14 Polar Expedition Company** (expeditions with crews and supplies). Risk: demand unclear.

**C15 Stormchaser Observatory** (weather). Risk: demand unproven.

**C16 Deep Time** (geology across aeons: plates, minerals, fossils). Risk: abstract for mainstream.

---

## 6. Task 5 — Scoring

Scores 1–10 per criterion [H], weights from the brief. Weighted score = Σ(score × weight) / 100 %.

| # | Concept | Demand 20% | Competition 20% | Retention 20% | Monetization 15% | Dev efficiency 10% | Expansion 10% | Portfolio 5% | **Score** |
|---|---|---|---|---|---|---|---|---|---|
| 1 | C01 Abyss Station | 8 | 7 | 8 | 7 | 7 | 8 | 8 | **7.55** |
| 2 | C02 Alchemist's Atelier | 7 | 8 | 7 | 7 | 7 | 7 | 7 | **7.20** |
| 3 | C03 Dig & Display | 7 | 6 | 7 | 7 | 6 | 7 | 7 | **6.70** |
| 4 | C04 Clockwork Guild | 7 | 7 | 8 | 5 | 4 | 7 | 6 | **6.55** |
| 5 | C05 Gridline | 4 | 8 | 7 | 6 | 6 | 6 | 7 | **6.25** |
| 6 | C06 Parcel Atlas | 5 | 7 | 7 | 6 | 5 | 7 | 6 | **6.20** |
| 7 | C07 Mycelium | 4 | 8 | 6 | 6 | 7 | 6 | 7 | **6.15** |
| 8 | C08 Terraform | 5 | 6 | 7 | 6 | 6 | 7 | 7 | **6.15** |
| 9 | C10 Apiary | 5 | 6 | 7 | 6 | 6 | 6 | 7 | **6.05** |
| 10 | C09 The Endless Library | 3 | 8 | 6 | 5 | 8 | 6 | 6 | **5.85** |
| 11 | C12 Lighthouse & Tide | 5 | 6 | 6 | 6 | 6 | 6 | 6 | 5.80 |
| 12 | C11 Ministry of Forms | 4 | 8 | 5 | 6 | 8 | 4 | 5 | 5.75 |
| 13 | C16 Deep Time | 3 | 8 | 6 | 5 | 6 | 6 | 6 | 5.65 |
| 14 | C13 Railbound Frontier | 5 | 5 | 6 | 6 | 5 | 6 | 6 | 5.50 |
| 15 | C14 Polar Expedition | 3 | 7 | 6 | 6 | 6 | 5 | 6 | 5.50 |
| 16 | C15 Stormchaser | 3 | 8 | 5 | 6 | 6 | 5 | 6 | 5.50 |

"Competition" scores high when there is *little* direct competition. A high competition score with a low demand score (Gridline, Library, Weather) means "empty, but perhaps empty for a reason".

### Top 10: short business cases [H]

1. **Abyss Station:** a theme with rising demand and no current direct rival on Play; zones give a natural content pipeline; strong screenshots. Bet: the ocean trend reaches mobile.
2. **Alchemist's Atelier:** proven discovery hook, weak idle competitors; content is recipes (cheap to add). Bet: discovery can be made to last.
3. **Dig & Display:** proven museum demand on mobile and digging on Steam; set-collection monetises well. Bet: we can make enough attractive artifact art.
4. **Clockwork Guild:** the most original and hardcore-loved mechanic; hard to make easy on a phone. Better as game 2 or 3 once the framework is mature.
5. **Gridline:** empty niche, satisfying balancing; mainstream appeal unproven. A cheap fake-door test could change its rank.
6. **Parcel Atlas:** logistics is underserved but map/routing UI is costly.
7. **Mycelium:** distinctive and pretty; demand unproven.
8. **Terraform:** good systems interplay; space theme crowded.
9. **Apiary:** breeding depth, cozy appeal; emerging competitors.
10. **The Endless Library:** cheapest to build; demand unproven, could be a small side project.

---

## 7. Task 6 — The best three in depth

### 7.1 Abyss Station

- **Gameplay:** one-thumb portrait screen: a vertical cross-section of the ocean with the station at the top and a depth gauge. Tap to ping sonar (active play), probes descend automatically. Samples become research, research buys hull, lights, drones and crew.
- **Progression (targets):** 30 s first sample and first upgrade; 5 min first drone (automation); 30 min twilight zone with bioluminescent lures (a new rule); day 1 first expedition and the reef; week 1 midnight zone pressure system + crew specialisations; month 1 first new ocean (prestige) with a twist; months 2–6 vents (heat economy), trench (rare one-offs), challenge oceans; 12+ months completable codex, Hadal layer, seasonal "currents" events.
- **Unique features:** zones with different rules; a reef food web (placing species next to prey/predators/symbionts gives bonuses: a light puzzle with a "recommended layout" for casual players); species codex with real-ish biology.
- **Competitors:** Abyssrium (aquarium tapper, older), Steam ocean idlers (Shelldiver, Chillquarium) on PC, browser prototypes. Indirect: every idle game.
- **Development:** core engine, ~6 zones × ~20 species for launch (~120 entries), expeditions, reef, 1 prestige layer + 2nd ocean at launch. Art: species and UI as code-drawn glowing line art (SVG) on deep blue/black, with a few illustrated hero pieces.
- **Monetization:** rewarded: return bonus ×2 (daily cap), sonar ping, an extra expedition slot, faster reef growth for 30 min. IAP: "Ad-free station" (one-time, rewards become automatic, capped), cosmetic station/submarine skins, a supporter pack.
- **Technical risks:** offline simulation of the reef food web (needs a closed-form or coarse step), keeping 60 fps glow effects in a WebView on midrange phones, big numbers late game.
- **Why players return:** the next zone, unfinished codex pages, expeditions coming home, reef growth, a weekly current.

### 7.2 Alchemist's Atelier

- **Gameplay:** a workbench screen; drag two or three reagents into a crucible to discover; known recipes go onto automated benches; customers arrive with requests and pay more for rare potions.
- **Progression:** discovery → production → market → schools (prestige). Each school changes the combining rules (astral: timing; living: potions grow; elemental: balance of four).
- **Unique:** discovery inside an idle economy; requests make choices matter (what to produce).
- **Competitors:** Little Alchemy 2 (puzzle, not idle), small idle potion shops (≤ ~180K installs [E]), Potion Craft / Potionomics (premium PC).
- **Development:** recipe graph data (~150 recipes at launch), market simulation, 2 schools. Art: ~150 potion/reagent icons (can be partly procedural: bottle shapes × colours × symbols).
- **Monetization:** rewarded: a hint, a customer rush, doubled batch. IAP: ad removal, hint bundle (never required), cosmetic ateliers.
- **Technical risks:** keeping discovery satisfying without a wiki; balancing a market.
- **Why players return:** undiscovered recipes, customer orders, the next school.

### 7.3 Dig & Display

- **Gameplay:** a dig site cross-section (layers by era) and a museum with rooms; finds are cleaned, identified and exhibited; themed sets give visitor bonuses.
- **Progression:** shovel → teams → conservation lab → museum wings → new site/civilisation (prestige).
- **Unique:** curation as strategy (sets, room adjacency); history facts as flavour.
- **Competitors:** Idle Museum Tycoon (~5.5M [E]; purchase complaints), small fossil diggers, Digseum (PC).
- **Development:** heaviest art load (each artifact should look distinct), ~200 artifacts at launch.
- **Monetization:** rewarded: a visitor rush, instant cleaning, a second dig attempt. IAP: ad removal, cosmetic halls.
- **Technical risks:** art volume and licensing; content upkeep.
- **Why players return:** missing set pieces, new wings.

### 7.4 Revenue scenarios for the top three [H]

Model: revenue per day = average DAU × ARPDAU. ARPDAU = ad impressions per DAU × fill × eCPM ÷ 1000 + IAP per DAU. Inputs from `raw/monetization-benchmarks-2026-11.md`. Google takes 15% of purchases (EEA, first $1M/year, Play Billing) [V]. Figures are **gross, before tax and costs**, first 12 months after public launch, with no paid marketing.

| Scenario | Installs, year 1 | Average DAU over the year | Ad imps/DAU | eCPM (blended Android) | IAP per DAU per day | ARPDAU | Gross year 1 |
|---|---|---|---|---|---|---|---|
| Conservative | 20,000 | 300 | 2 | $4 | $0.003 | ≈ $0.011 | ≈ $1,200 |
| Expected | 150,000 | 2,500 | 3.5 | $6 | $0.008 | ≈ $0.028 | ≈ $25,500 |
| Optimistic | 1,000,000 | 20,000 | 4.5 | $8 | $0.015 | ≈ $0.049 | ≈ $360,000 |

Assumptions: fill 95%; rewarded viewers = ~35–45% of DAU, so imps/DAU is an average over all players; average DAU ≈ installs × a share still playing (D30 1–3%, long-tail retention typical of idle games). The three concepts would use the same scenarios, adjusted [H]: Abyss Station and Alchemist's Atelier similar; Dig & Display slightly lower expected installs because of the existing museum rival, slightly higher IAP from collection completion.

The honest base case is the **conservative-to-expected** range. Most small idle games earn little [E: AppGoblin shows most small Android idle games under $10K/month; a 2018 devlog earned $84 in total]. The portfolio strategy exists precisely because one game is unlikely to carry the studio.

### 7.5 DAU forecast table [H]

Annual gross at three ARPDAU levels (low $0.01, mid $0.025, high $0.05):

| DAU | Low | Mid | High |
|---|---|---|---|
| 100 | $365 | $913 | $1,825 |
| 1,000 | $3,650 | $9,125 | $18,250 |
| 5,000 | $18,250 | $45,625 | $91,250 |
| 10,000 | $36,500 | $91,250 | $182,500 |
| 50,000 | $182,500 | $456,250 | $912,500 |
| 100,000 | $365,000 | $912,500 | $1,825,000 |

Downloads are not players: 100,000 DAU needs on the order of millions of installs. Costs to subtract [V/H]: Google Play developer account $25 once; Apple Developer $99/year (only when iOS starts); a domain and privacy-policy page (small); purchased art or sound if any; your AI subscription; taxes. Paid installs cost $0.60–3.50 each in Western markets for casual games [E], so at these ARPDAUs paid marketing should wait until soft-launch data shows a lifetime value above that.

---

## 8. Task 7 — Recommendation

**Develop Abyss Station first.**

Why:

1. **Evidence of demand that is current:** the ocean is the theme with the most strong recent Steam idle hits (Shelldiver, Chillquarium, Cast n Chill); mobile players already know aquarium idlers (Abyssrium).
2. **A gap on Play:** I found no current, polished deep-sea *exploration* idle game on Google Play.
3. **Long life built into the theme:** each depth zone and each ocean is a new rule set, exactly what long-lived games do (CIFI, Unnamed Space Idle, Farmers Against Potatoes: "each mechanic has a different set of rules").
4. **Both audiences:** cozy collection and a calm look for mainstream players; food-web optimisation, expeditions and challenge oceans for enthusiasts.
5. **Cost:** glowing line art on dark backgrounds can be largely drawn in code; dark mode is the natural style; screenshots stand out in a store full of bright cartoon tycoons.
6. **Portfolio:** its framework parts (zones with rules, collections, expeditions, a placement puzzle) are reusable for Alchemist's Atelier and Dig & Display.

**The strongest arguments against my own recommendation:**

1. The ocean evidence is mostly **Steam (PC)**. Mobile success is not proven by it; Abyssrium shows mobile interest, but it is old and an aquarium, not exploration.
2. **Alchemist's Atelier has the clearer mobile gap** (huge discovery game, tiny idle competitors) and cheaper content (recipes are data). If you value certainty of a gap over trend, choose it.
3. **Content volume:** 120+ species need to look distinct. If code-drawn art doesn't look commercial enough, we'll need illustrations (cost, licensing).
4. **Offline food-web simulation** is a real technical risk; a simpler bonus system may be needed.
5. All scores are my judgement. The difference between #1 (7.55) and #2 (7.20) is within the margin of error. A one-week fake-door test of both themes would give real evidence.

---

## 9. Task 8 — Proposed studio architecture (proportionate)

| Part | Proposal | Why |
|---|---|---|
| **Studio control** | This repository, `MadGames`: research, portfolio registry, decision registry, function registry index, standards, studio status script later | One place to start every session |
| **Shared framework** | Its own repository (proposed `madgames-framework`), a TypeScript package with semantic versions as git tags; games pin an exact version | A framework change never reaches a released game by accident |
| **Games** | One repository per game (`game-001-…`), each its own Capacitor app, own version, own store identity, own monetization config | A bug in one game cannot break another |
| **Until game 1's vertical slice** | Framework code lives inside game 001's repository in a `framework/` folder; it is split into its own repository when the vertical slice is proven | Avoid building a framework before we know what is reusable |
| **Decision registry** | `studio/decision-registry/decisions.md` (one table + one section per decision, never deleted, superseded ones marked) | Required by the brief, simple to search |
| **Function registry** | Generated from code doc comments (like G OPS's `building-blocks.md`), per repository, with an index here | Always true, because it is generated |
| **Tests** | Vitest unit tests + deterministic economy simulations (5 min … 365 days × 8 player profiles) in Node, run in CI on every push | Balance checked automatically |
| **Releases** | GitHub Actions builds a signed AAB from a tag; upload to Play internal testing is manual (or by an explicit command) | Nothing publishes without your approval |
| **Portfolio analytics** | Later: Firebase Analytics (free) or a privacy-friendly alternative per game; a studio dashboard script that reads only connected sources | No invented numbers |

New repositories: I cannot create GitHub repositories from this session. When we start game 001 you'll create an empty repository (I'll tell you exactly how), and I'll set it up.

---

## 10. Task 9 — First roadmap (Abyss Station, if chosen)

Effort is in calendar weeks with AI-assisted development and your part-time review [H].

| Stage | What | Estimate | Exit criterion |
|---|---|---|---|
| A. Validation | detailed concept, personas, fake-door page (optional), store-search check | 1 week | You approve the concept details |
| B. Design & architecture | game design document, economy model, wireframes, tech decision confirmed, test strategy | 1–2 weeks | Economy simulation shows the milestone targets |
| C. Vertical slice | first 2 zones, probes, drones, sonar, first species, saves, offline summary; playable in the browser and as an Android test build | 2–3 weeks | You and 5–10 testers say it's fun; first-hour pacing matches targets |
| D. Minimum viable game | 6 zones, ~120 species, reef, expeditions, 1 prestige + 2nd ocean, tutorial, settings, achievements, analytics, rewarded ads (test ads), consent, ad-removal purchase | 6–10 weeks | All tests and 365-day simulations pass |
| E. Testing | balance sims, device tests, save compatibility, performance on a midrange phone | 1–2 weeks (overlaps D) | No crash/blocker bugs |
| F. Closed test / soft launch | **Google's required closed test: 12 testers for 14 days** (new personal accounts), then a limited release | 3–6 weeks | Go/no-go: D1 ≥ 30%, D7 ≥ 10%, crash-free ≥ 99.5%, rewarded opt-in ≥ 25% of DAU [H targets] |
| G. Public launch | store listing, screenshots, privacy policy, Data safety form, production ads | 1–2 weeks | Your explicit release approval |
| H. Live operations | content every 4–8 weeks (new zone/ocean), bug fixes, balance | ongoing | KPI review monthly |

Rough total to public launch: **4–6 months**. Main uncertainties: whether the vertical slice is fun (we may iterate), art quality, finding 12 testers, your review time, and Google account verification.

A step you can take early regardless of concept: create a Google Play developer account (personal $25, or organisation with a D-U-N-S number which avoids the 12-tester rule), because verification and the 14-day closed test take calendar time.

---

## 11. Task 10 — Your decision

Please choose:

1. **Abyss Station** (recommended), or
2. **Alchemist's Atelier**, or
3. **Dig & Display**, or
4. another concept from the list, or
5. run a one-week fake-door test of the top two before choosing.

Also useful to know (not blocking): whether you'll publish as a person or as a company (affects the 12-tester rule and the developer name on the store), and how much time per week you can give to testing.
