# Abyss Station: concept (Stage A)

Game ID: game-001 · Working title: Abyss Station (no game with that exact name found on 2026-11-10; the final store name is checked again before launch) · Stage: A (validation) · Approved by the owner: 2026-11-10 (D-0008)

These documents live in the studio repository until the game's own repository exists; they move there at Stage B (D-0004).

## 1. The pitch

You run a small research station on a lonely ocean. You send probes down, they come back with samples, and samples fund deeper dives. Every depth zone plays by **its own rule**: light in the twilight, pressure in the midnight zone, heat at the vents, scarcity on the abyssal plain, crewed expeditions in the trench. You catalogue every species you find and keep them in a **living reef** whose food web makes your station stronger. When an ocean is mapped, you found a station in **a new ocean that changes the rules again**.

One-line store hook [H]: *"Dive deeper. Discover what lives in the dark."*

## 2. Who it's for (personas)

| Persona | Who | What they want | What would make them quit | How we serve them |
|---|---|---|---|---|
| **Kari, the commuter** (mainstream) | 30s, plays 3–6 short sessions a day on the bus or in breaks | progress every visit, clear next goal, no stress | forced ads, confusing menus, "nothing changes" | big "while you were away" summary, one obvious next goal, recommended choices |
| **Ola, the optimiser** (hardcore) | 20s, r/incremental_games, spreadsheets, Discord | real decisions, systems that interlock, months of depth | being balanced around ads, shallow prestige, a dev who disappears | reef food web, pressure trade-offs, challenge oceans, transparent formulas in a "Station log", a public roadmap |
| **Mia, the collector** (cozy) | any age, loves nature documentaries and calm games | discovering, completing a collection, beautiful screens | grind without discoveries, ugly UI | the species codex, glowing art, sound design, completion percentages |
| **Lars, the returner** | played for weeks, left for 3 months | to come back without feeling lost or punished | wiped streaks, a wall of new systems | full offline progress (capped generously), "what changed while you were away", no punishing daily streaks |

## 3. The core loop

1. **Probes** dive and return with **Samples** (the main currency). Tap the sonar to speed things up (active play).
2. Spend Samples on more and better probes (deeper, faster, larger hauls).
3. The **Lab** turns Samples into **Data** (research currency) → the **research tree** (permanent upgrades within this ocean).
4. Deeper dives **discover species** → codex entries → place them in the **Reef** for bonuses.
5. **Drones** automate probes; **crew** run shifts; the station works while you're away.
6. Reach the bottom of the ocean's chart → **found a new station** in a new ocean (prestige).

## 4. Depth zones (each one a new rule)

| Zone | Depth | New rule | Decision it creates |
|---|---|---|---|
| Sunlight | 0–200 m | none: learn the basics | which probe to upgrade |
| Twilight | 200–1,000 m | **Light**: lures and lamps raise discovery chance but cost energy | light vs production |
| Midnight | 1,000–4,000 m | **Pressure**: each probe has a hull rating; dives below it fail | a few strong probes or many light ones |
| Vents | 2,000–3,500 m (side branch) | **Heat**: vents power drones; vents cycle between active and dormant on a known schedule | where to place collectors, when to move them |
| Abyssal plain | 4,000–6,000 m | **Scarcity**: food falls as "marine snow"; the reef's food web matters most here | reef layout for this zone |
| Hadal trench | 6,000–11,000 m | **Expeditions only**: crewed dives with gear and crew picks, rare one-off finds | who and what to send, and when |

Vent cycles and marine snow are **deterministic functions of time**, so offline progress can be calculated exactly, without simulating every second (this removes the main technical risk named in Phase 1).

## 5. Systems and when they unlock (pacing targets [H])

| When | What happens | Brief milestone |
|---|---|---|
| 0–30 s | first probe returns, first upgrade bought | immediate reward |
| ~5 min | **first drone**: probes dive by themselves | first automation |
| ~15 min | **Lab and Data**, the research tree opens | new currency |
| ~30 min | **Twilight zone** and the first bioluminescent species (light rule) | first big milestone |
| day 1 | **Reef** (first species placed), **Codex**, **first expedition** | longer goals understood |
| week 1 | **Midnight zone** (pressure), **crew** with specialisations | several systems interacting |
| weeks 2–3 | **Vents** (heat economy) | systems interlock |
| ~week 4 | **first new station** (prestige) in a second ocean | major evolution |
| months 2–3 | **Abyssal plain**, third and fourth oceans, **challenge dives** (dives with constraints) | strategic decisions |
| months 3–6 | **Hadal trench**, the **Ocean Institute** (second prestige layer across oceans: programmes and grants) | new progression layer |
| 6–12 months | remaining oceans, rare species, institute programmes | deeper challenges |
| 12+ months | codex completion, seasonal **currents** (optional events), new oceans in updates | optional long-term goals |

Waits are short early. A long wait always comes with something else to do. Nothing requires daily play.

### Oceans (prestige layer 1)

Each new station keeps **Charts** (prestige currency → a permanent archive of bonuses) and some species, and adds one twist:

1. **Home Ocean**: the standard rules.
2. **Arctic**: sea ice covers the surface by season; light is scarce, cold-adapted species thrive.
3. **Ring of Fire**: vents everywhere, but they erupt and move more often.
4. **Southern Ocean**: strong currents carry probes and samples sideways (route choice).
5. Later oceans arrive in content updates (planned 4–8 weeks apart).

### The reef (the strategic heart)

- A small grid (it grows over time). Each species has a role: producer, grazer, predator, filter feeder, symbiont, cleaner.
- Neighbours give bonuses (a cleaner next to a predator, a symbiont next to its host, producers near grazers).
- **"Arrange for me (recommended)"** gives a good layout for casual players; optimisers can beat it by hand.
- Reef bonuses are calculated once whenever the layout changes, so they cost nothing offline.

### Species

- About **120 species at launch** (6 zones × ~20), more with each ocean.
- **Fictional species inspired by real ones** (for example a "lantern-finned angler"). This lets us add as many as we like and avoids presenting wrong facts as science. Each entry has a short note on the real animal family that inspired it (educational, like Cell to Singularity's appeal).
- Codex pages show completion per zone and ocean.

## 6. Active and idle play

- **Idle:** drones, crew and the lab run on their own; full offline progress up to a generous cap (proposal: 24 h at first, raised by research to 72 h+). Returning shows a summary with the next best action.
- **Active:** the sonar ping (taps charge a meter that speeds dives); "contact!" moments where a silhouette passes and a quick tap scans it for a bonus; manual expedition choices.
- Target [H]: an active player progresses about 1.5–2× an idle one, never 10×.

## 7. Money (D-0003)

**Rewarded ads** (opt-in, reward shown before the ad, granted only after completion, no penalty for declining; daily cap proposal: 8):

| Placement | Reward | Limit [H] |
|---|---|---|
| Return bonus | double the offline haul | once per return after ≥ 30 min away |
| Sonar burst | a strong 30-minute speed-up of dives | 3 a day |
| Expedition rush | finish one running expedition now | 2 a day |
| Reef bloom | +50% reef bonuses for 30 min (does not stack) | 2 a day |

**Optional purchases** (no pay-to-win, nothing that can only be bought with money is needed for progress):

| Item | What it does | Price idea [H] |
|---|---|---|
| Ad-free station | every ad reward becomes automatic, same caps | ~$4.99 one-time |
| Supporter pack | cosmetic station + submarine skin, a thank-you codex page | ~$2.99 |
| Cosmetic skins | station, probe and submarine looks | ~$1.99 each |

No subscriptions, no gacha, no premium currency at launch (a source of complaints in the competitor matrix: Shop Titans, AdVenture Ages, Idle Outpost).

## 8. Look and feel (art direction, Stage B details)

- **Glowing line art on deep blue to black**: bioluminescent creatures drawn as vector shapes with glow (largely drawn in code, consistent, light on memory). A few illustrated hero pieces (the station, the store icon) may be commissioned or made with tools whose licences allow commercial use; every asset is logged with its source and licence.
- Portrait, one thumb, large touch targets, dark by nature (a light "surface" theme is optional).
- Readable big numbers (choice of short scale "1.2 M" / scientific "1.2e6").
- Calm ambient sound; satisfying sonar pings.

## 9. Why players keep returning

the next zone · unfinished codex pages · expeditions coming home · vent cycles · the reef getting better · a new ocean · seasonal currents · a developer who visibly keeps adding oceans.

## 10. Competitors

- **Direct (deep-sea exploration idle on Google Play):** none current and polished found (2026-11-10 searches).
- **Near:** Abyssrium / Tap Tap Fish (aquarium tapper, older); Steam ocean idlers (Shelldiver 18,200 reviews, Chillquarium 8,422, Cast n Chill 8,756); Surviving the Abyss (PC deep-sea station management, not idle); browser prototypes ("ABYSS – Deep Sea Expedition Log", "Deep Sea Idle: Infinity Abyss" on Steam).
- **Model to learn from:** Egg, Inc. (optional ads, missed days not punished, 4.7 from 1.41M ratings), Cell to Singularity (educational calm), CIFI and Unnamed Space Idle (long life from new systems), and the mobile UI complaints about deep games (too many tabs early, small buttons).

## 11. Revenue model

See the Phase 1 report §7.4 (conservative ≈ $1.2K, expected ≈ $25K, optimistic ≈ $360K gross in year 1, all [H]). The real numbers come from the closed test and soft launch.

Go/no-go after the soft launch [H targets]: D1 ≥ 30%, D7 ≥ 10%, D30 ≥ 3%, crash-free sessions ≥ 99.5%, rewarded-ad viewers ≥ 25% of daily players, median first session ≥ 8 min.

## 12. Major risks

| Risk | Effect | What we do |
|---|---|---|
| The ocean trend on PC does not carry to phones | few installs | strong store page and screenshots; test the store listing with Play's experiments; cheap itch.io web build first |
| The core loop isn't fun | everything else is wasted | Stage C vertical slice tested by you and testers before more content |
| Code-drawn art doesn't look commercial | low store conversion | art test in Stage B (3 species, station, one zone) before committing |
| 120 species is a lot of content | slow production | species are data + parameterised drawings; content pipeline in Stage B |
| WebView performance on midrange phones | stutter, battery drain | glow effects budgeted; test on a midrange phone from the vertical slice |
| Personal Play account needs 12 testers for 14 days | launch delay | recruit testers during development (see §13) |
| Low ad revenue per player | small income | expected; keep costs low, reuse the framework for game 002 |

## 13. Owner inputs (2026-11-10)

- **Publishing as a person** (personal Google Play developer account). This means the **closed test with at least 12 testers for 14 continuous days** before production access. Plan: start collecting testers now (friends, family, colleagues, the r/incremental_games feedback threads, tester-exchange communities); aim for 15–20 so that 12 stay opted in.
- **About 8 hours a week** for testing and decisions. The roadmap assumes this: one playable build to try each week, with a short list of what to check.

## 14. Next steps (Stage B)

1. Create the game's GitHub repository (owner; instructions in the session).
2. Game design document with the full economy (costs, growth curves, research tree, species list format).
3. Economy simulation in code: the 8 player profiles × 5 minutes … 365 days, checking the pacing targets in §5.
4. UI wireframes for the main screen, reef, codex, expeditions.
5. Art test: one zone, the station, three species.
6. Confirm the technology (D-0005) with a tiny Android test build that shows a test rewarded ad and the consent form.
