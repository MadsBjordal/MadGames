# Raw research notes: ad monetization benchmarks (2026-11-10)

Collected by a research pass on 2026-11-10. Tags: [V] vendor/marketing claim, [O] official platform documentation, [I] independent/secondary blog. Treat every figure as directional; replace with our own soft-launch data.

Not accessible from the research session: reddit.com, comic.gamedev.net, the image-only Appodeal Q4 2024 and TopOn H1 2025 PDFs, interactive Appodeal / Business of Apps country charts. No Norway-specific rewarded eCPM found.

## 1. Rewarded video eCPM

Appodeal Q4 2024 (published 2025, read from charts, cited by Mistplay Mar 2026 and Playio) [V]:

| Region | Android | iOS |
|---|---|---|
| North America | ~$9.0–9.2 | ~$13.6–13.9 |
| Europe | ~$5.1 | ~$8.8–8.9 |
| APAC | ~$8.2 | ~$7.5 |
| Middle East | ~$2.3–2.4 | ~$8.4 |
| LatAm | ~$1.8–1.9 | ~$3.4–3.75 |

- Country averages, all platforms (Appodeal via Mistplay) [V]: US $15.15, UAE $14.55, Australia $13.80, Switzerland $12.20, Ireland $12.10, UK $10.65, Iceland $9.25 (only Nordic listed). Mistplay's table has internal inconsistencies.
- Older baseline, Appodeal H2 2021–H1 2022 via Udonis 2024 [V]: Western Europe Android $3.62 / iOS $6.51; US Android $12.91 / iOS $13.81; LatAm $2.00 / $2.31; Asia $2.00 / $5.86; Eastern Europe $1.49 / $2.55.
- Tenjin × CAS, game apps, top countries [V]: Q2 2024 Android US $30.25, Canada $23.13, South Korea $22.01; iOS US $24.39, South Korea $20.94, Australia $19.91. Q1 2024 Android US $27.88, Canada $22.01, UK $20.45. Much higher than Appodeal (different method and data set).
- Tenjin Q3 2026 share of game ad revenue [V]: Android US 28%, Russia 8%, Brazil 5%, UK 3%, Germany 3%, 34% outside the top 10; iOS US 52%. No Nordic country in the top 10.
- TopOn H1 2025 [V]: Android rewarded eCPM −7% YoY, "near three-year lows"; iOS rewarded +18% YoY.
- Other ranges [V/I]: AppLovin 2025 (via Coinis) tier-1 $15–40, tier-2/3 $3–10; Playwire (Sep 2025) global $8–18; Applixir average $12–15, SE Asia $1–4; mwm.ai (2026) US iOS $10–25, India Android $0.30–1.00; blog via Playio India $0.70–3.96, US $14–22.

Planning range, Android rewarded eCPM: US ~$9–30; Western Europe/Nordics ~$4–10 (Europe average ≈ $5; Nordics probably higher, unverified); LatAm ~$1.5–2; South/SE Asia ~$0.3–4. Blended global for an Android-heavy audience: single digits (Playwire's $8–18 is too high).

## 2. Idle/casual benchmarks

Retention:
- GameAnalytics 2026 report (2025 data, all genres, 16,262 games) [I/V]: D7 median just under 4%, top 25% 6–7%, top 10% 11–12%, top 1% >25%. D30 median 0.69–0.79%, top 25% 1.6–1.8%, top 1% 13–15%. D1 median not stated; top 25% just above 30%, top 10% ~40%. D1 fell in 2025 vs 2024.
- GameAnalytics idle study (Dec 2020) [V]: top 25% idle D1 39.4%, top 10% D1 45.6%; DAU/MAU 18% (hyper-casual 10.5%); 5.3 sessions/day, ~8 min each; ARPDAU ~9× hyper-casual.
- East Side Games (2024), internal idle targets: D1 ~40%, D7 20%.
- Playio genre table [I]: idle D1 35–50%, D7 20–30%, D30 10–15% (aspirational, far above GA medians).

ARPDAU (no audited idle benchmark): idle $0.05–0.25; optimized sim/idle $0.05–0.10; most indies $0.02–0.05 [I]. Playio 2026 illustrative rewarded-only example ≈ $0.029 ad ARPDAU.

Rewarded impressions per DAU: no published benchmark (Playio); "3–5/day" is a design rule. 2024 Department of Fun roundtable: targets 4–5 per DAU, 45% viewer rate, $15–30 eCPM [I, second-hand].

Engagement: Unity Mobile Growth & Monetisation Report 2024 (2023 data) [V], share of DAU watching rewarded ads: casual 36%, word 38.4%, RPG 37.6%, sports/trivia 27.3%; placements where players run out of resources 38.1% vs between levels 23.8%; >15 placements up to 46%. AppLovin ad-viewer rate: <15% poor, >30% strong [V]. Opt-in per offer shown: 30–80% [V].

Fill rate: 95%+ with mediation (vendor targets) [V]. Kongregate × AdMob case study: 90% fill, 95% completion, $30 eCPM (one title) [V].

Ads vs IAP split (sources disagree): idle/sim ads 80–90% (igvend) [I]; idle ads 60–70%, IAP 30–40% (adjoe) [V]; ad-reliant casual ads 60–70% (Gamesforum 2025) [I]; at scale IAP can dominate: Idle Outpost (≈360K DAU estimated) ads ≈35% of revenue (Felix Braberg newsletter, estimate).

Formula: ad ARPDAU = impressions/DAU × fill × eCPM / 1000.

## 3. CPI and organic discovery

- Liftoff/Singular 2025 casual report (Feb 2024–Feb 2025) [V]: no regional CPI in the summary; top Android genre CPI RPG $4.29.
- Liftoff 2022 casual [V]: casual Android $0.75, iOS $2.27; North America $3.32, LatAm ~$0.66; simulation $0.91. Casual D30 ROAS 17.8–29.6%.
- Admiral Media 2026 [V/agency], tier-1 Android: casual/puzzle $1.20–3.00; idle RPG $2.00–5.00 (iOS $4–9); hypercasual $0.30–1.20.
- Game Growth Advisor 2026 [I], casual/puzzle Android: US $1.50–3.50; UK/CA/AU $1.00–2.50; Western Europe $0.60–1.50; SE Asia $0.20–0.60; LatAm $0.15–0.60; India $0.08–0.30.
- Idle RPG blended global $3.19 [I]; AppTweak 2025 US games median $4.63 [V].
- Implication: with ad ARPDAU in cents, tier-1 paid UA rarely pays back for an ad-only game.

Organic: search ≈ 58–60% of Google Play installs (2026 blogs citing Sensor Tower/Apple; no primary source) [I]; ASO surfaces 27–41% of organic installs by category (data.ai, second-hand) [I]; ~41–44K new apps/month on Google Play (Statista Dec 2024, 42matters); games ≈ 12% of ~2.2M apps (42matters 2026) [I]; catalogue shrank 3.4M → 1.8M between early 2024 and Apr 2025 (Appfigures via TechCrunch, second-hand).

## 4. Platform rules [O]

- Target API: since 31 Aug 2026 new apps and updates must target Android 16 (API 36); existing apps need ≥ API 35 to stay visible to new users on newer Android. API 37 date not yet published; pattern = yearly around 31 Aug.
- 12 testers / 14 days: personal developer accounts created after 13 Nov 2023 must run a closed test with ≥ 12 testers continuously opted in for ≥ 14 days before applying for production. Organisation accounts are exempt but need a D-U-N-S number (up to ~30 days per third-party guides).
- Android developer verification: announced Aug 2025, open to all from Mar 2026; enforced from 30 Sep 2026 in Brazil, Indonesia, Singapore, Thailand; global from 2027. Not yet enforced in Norway; verify anyway.
- Play Billing Library: PBL 7 deadline 31 Aug 2026 (extension 1 Nov 2026, both passed); PBL 8 31 Aug / 1 Nov 2027; PBL 9 31 Aug 2028. Use PBL 8 or 9.
- Service fees: from 30 Jun 2026 in EEA (incl. Norway), UK, US: service fee + separate 5% billing fee when Play Billing is used; first $1M/yr 10% + 5% = 15% (PocketGamer.biz 25 Jun 2026); above $1M 20% + 5% new installs, 25% + 5% existing (lower for Play Games Level Up, from 30 Sep 2026); subscriptions 10% + 5%. Elsewhere 15% first $1M, 30% above. Confirm in Play Console.
- AdMob consent: since 16 Jan 2024 personalised ads in EEA/UK need a Google-certified CMP on IAB TCF v2.2 (Switzerland since 31 Jul 2024). Google UMP SDK qualifies. Otherwise non-personalised ads only.
- Families policy: only if children are a target audience → Families self-certified ad SDKs only. Target 13+/general without children in audience to avoid.
- Apple ATT: required before tracking (iOS 14.5+); relevant only for iOS.

## 5. Small-developer case studies (little verified data)

- Mirkowanie – Idle Money Clicker (gamedev.net, Feb 2018): 3,451 Play + Amazon downloads, ~26K web plays, $84 total ($54 Unity Ads + Chartboost, $29.62 Kongregate), no IAP.
- r/gamedev via mirror (unverified): rewarded-only game $2–10/day from 100–500 impressions (~$0.001–0.03/view).
- AppGoblin estimates: most small Android idle games < $10K/month; one with 1.2M installs, 95.5K MAU estimated $10K+/month.
- Not idle, unverified: Holger Sindbaek (solitaire) ~$32 day one → ~$10K/month ads; Max Artemov 30-app portfolio $22K+/month.
- Idle Miner Tycoon × Pangle: +12.5% ARPDAU with rewarded video [V].

Back-of-envelope (assumption, not data): 1,000 Android DAU mostly Europe × 4 rewarded imps × 95% fill × $5 eCPM ≈ $19/day (≈ $0.019 ARPDAU).

## Sources

- https://business.mistplay.com/resources/mobile-ecpm/ , https://business.mistplay.com/resources/mobile-ads-ecpm/
- https://blog.playio.co/mobile-game-ecpm-benchmarks-2026
- https://appodeal.com/wp-content/uploads/2025/03/Quarterly_Mobile_eCPM_Report_-_Q4_2024.pdf , https://appodeal.com/benchmarks/
- https://www.blog.udonis.co/mobile-marketing/mobile-apps/ecpms
- https://tenjin.com/tr/blog/ad-mon-gaming-2026/
- https://gamedevreports.substack.com/p/tenjin-ad-monetization-in-mobile , https://gamedevreports.substack.com/p/tenjin-ad-monetization-in-mobile-00b
- https://mores.toponad.com/reports/TopOn%20Global%20Mobile%20Games%20Monetization%20Report%20_%202025%20H1.pdf
- https://coinis.com/glossary/rewarded-video
- https://www.playwire.com/blog/admob-ecpm-benchmarks-what-publishers-should-expect
- https://gamedevreports.substack.com/p/gameanalytics-mobile-and-pc-game
- https://wnhub.io/news/marketing/item-3203
- https://www.pocketgamer.biz/unity-global-rewarded-ad-engagement-rose-by-32-in-2023/
- https://applovin.com/?p=7802
- https://gamerdigesthq.substack.com/p/ads-in-gaming-dof-roundtable
- https://blog.playio.co/mobile-game-ad-revenue-calculator
- https://igvend.com/en/blog/mobile-game-monetization-how-mobile-games-make-money
- https://adjoe.io/?p=68287
- https://investgame.net/wp-content/uploads/2025/07/Gamesforum-Intelligence-Casual-Gaming-Report.pdf
- https://felixbraberg.substack.com/p/idle-outpost-zombie-apocalypse-review-7cb
- https://www.casestudies.com/company/google-admob/case-study/kongregate-uses-admob-to-boost-revenue-with-average-30-cpm
- https://pangleglobal.com/resource/27816
- https://gamedevreports.substack.com/p/liftoff-and-singular-casual-games , https://liftoff.ai/?p=34267
- https://www.pocketgamer.biz/cpi-for-casual-games-has-fallen-while-roas-has-increased/
- https://blog.playio.co/mobile-game-cpi-benchmarks-2026
- https://segwise.ai/blog/cpi-ipm-roas-benchmarks-optimizing-ad-spend/
- https://www.webtonic.io/blog/app-store-optimization-statistics , https://www.appalize.com/blog/mobile-trends/aso-trends-and-benchmarks-2026-what-the-data-shows
- https://data.42matters.com/google-play-statistics-and-trends
- https://developer.android.com/google/play/requirements/target-sdk , https://support.google.com/googleplay/android-developer/answer/11926878
- https://support.google.com/googleplay/android-developer/answer/14151465?hl=en
- https://developer.android.com/developer-verification/guides , https://support.google.com/android-developer-console/answer/16650243
- https://developer.android.com/google/play/billing/deprecation-faq
- https://support.google.com/googleplay/android-developer/answer/112622?hl=en , https://www.pocketgamer.biz/google-play-expands-billing-options-and-lowers-fees-for-developers/
- https://support.google.com/admob/answer/13554116?hl=en
- https://support.google.com/googleplay/android-developer/answer/12918983
- https://developer.apple.com/documentation/apptrackingtransparency
- https://www.gamedev.net/blogs/entry/2264438-earnings-and-statistics-from-my-4th-android-game/
- https://appgoblin.info/apps/com.CryptoGrounds.IdleResearch
