# Raw research notes: engine and SDK comparison (2026-11-10)

Versions read from npm / pub.dev / GitHub release pages on 2026-11-10. Performance and "AI-agent fit" ratings are judgement, not measured.

## Rule for every option

Google Play target API: since 31 Aug 2026 new apps and updates must target Android 16 (API 36); existing apps ≥ API 35 to stay visible to new users. https://developer.android.com/google/play/requirements/target-sdk

## Comparison

| | Godot 4.7.x | Unity 6 | Flutter + Flame | TypeScript + Capacitor 8 | React Native / Expo |
|---|---|---|---|---|---|
| Version | 4.7.2-stable (18 Aug 2026) | 6.x, IAP 5.x | Flame 1.38.2 (27 Aug 2026) | @capacitor/core 8.6.0 (28 Oct 2026) | expo 58.0.23, RN 0.88.1 |
| Android | Yes; Gradle build for AAB; target SDK 36 default not verified | Yes; API 36 from 6000.0.46f1 | Yes; default targetSdk 36 not verified | Yes; compile/target 36, minSdk 24 | Yes |
| iOS | Yes (Mac) | Yes (Mac) | Yes | Yes | Yes |
| AdMob | Community only: poingstudios v5.1.0 (13 Sep 2026), 15+ mediation adapters; Godot-version churn | Official AdMob Unity plugin; LevelPlay; direct Unity Ads no longer supported (bidding only from 31 Jan 2026) | Official google_mobile_ads 9.2.0 (21 Oct 2026); gma_mediation_applovin 2.6.5; applovin_max 4.6.4; unity_levelplay_mediation 9.4.0 | @capacitor-community/admob 8.3.0 (29 Oct 2026, MIT), GMA Android 25.4.x / iOS 13.11; community-maintained; mediation through it not verified | react-native-google-mobile-ads 17.4.0; react-native-applovin-max 9.6.0 |
| IAP | godot-google-play-billing 3.3.0 (PBL 9.1.0); iOS StoreKit plugin not verified | Unity IAP 5.4.x | in_app_purchase 3.3.1 (18 Sep 2026, flutter.dev) | @revenuecat/purchases-capacitor 14.1.0 (5 Nov 2026) or cordova-plugin-purchase 13.20.0 (27 Oct 2026) | react-native-purchases 11.0.1, react-native-iap 17.3.5 |
| 2D UI midrange | Good | Good, heavier runtime/size | Good (Skia/Impeller) | Fine for menu/number-heavy idle UI; keep effects modest (judgement) | OK, not a game engine |
| Licence | Free (MIT) | Personal free < $200k; Pro $2,310/yr from 12 Jan 2026; Runtime Fee cancelled 12 Sep 2024 | Free | Free | Free |
| AI agent, text-only | Medium-good (.tscn verbose; C# on Android experimental) | Weak (YAML+GUIDs, editor-centric) | Good (all Dart code) | Best (plain TS/HTML/CSS) | Good, thin game tooling |
| Tests | GUT 9.7.x; gdUnit4 6.2.3 headless; reported Godot 4.7.2 headless failures exiting 0 | Unity Test Runner via GameCI (Editor) | flutter test, flame_test 2.3.1 | Vitest in Node | Jest |
| CI | headless export + templates | GameCI; Personal licence activation in CI restricted | standard | Node + Gradle (JDK 21, AGP 8.13) | Gradle or EAS |
| Sharing | addons / submodule | UPM | Dart packages | pnpm workspaces | npm workspaces |

## Big numbers

- break_eternity.js 2.2.1, published 8 Nov 2026 (MIT), up to 10^^1e308, maintained.
- break_infinity.js 2.2.0, last 26 Feb 2023 (MIT), up to ~1e9e15, faster, dormant but stable.
- C#: NuGet BreakInfinity 1.1.1 (15 Nov 2025), source/licence not verified.
- Godot: BigNumber GDExtension, Idle Number Kit Lite, break-nihility: small community projects.
- Dart: break_eternity port, big_double, infinity 1.0.1: thinly maintained, licences not verified.

## Research pass recommendation

1. TypeScript + Capacitor 8 (DOM/CSS or light canvas). Best for headless agent work; Vitest simulations in Node; break_eternity.js; Node + Gradle CI; pnpm monorepo; owner already runs Capacitor (G OPS). Risks: community AdMob plugin, mediation unverified (start AdMob-only), WebView perf on low-end devices. OTA code updates for a Play game: policy not verified, do not rely on it.
2. Flutter + Flame: official Google ads/IAP packages incl. mediation; weaker big-number ports.
3. Godot 4.7: good game feel; third-party ads plugin churn; C# mobile experimental; headless exit-code issue.
4. Unity 6: not recommended for this setup (editor-centric, CI licence activation).
5. React Native / Expo: no advantage over Capacitor.

All: target/compile SDK 36, Google UMP consent, pure simulation module separate from renderer.

## Sources

https://github.com/godotengine/godot/releases · https://docs.godotengine.org/en/4.7/tutorials/scripting/c_sharp/index.html · https://docs.godotengine.org/en/4.7/tutorials/export/exporting_for_android.html · https://forum.godotengine.org/t/how-to-target-latest-android-sdk/142631 · https://github.com/poingstudios/godot-admob-plugin/releases · https://github.com/godot-sdk-integrations/godot-google-play-billing · https://docs.unity3d.com/Manual/com.unity.purchasing.html · https://docs.unity.com/en-us/engine/6000.0/manual/platform-specific/android/introducing/requirements-and-compatibility · https://docs.unity3d.com/Manual/com.unity.ads.html · https://docs.unity.com/grow/levelplay/sdk/unity/migrate-from-unity-ads-to-levelplay · https://pub.dev/packages/flame · https://pub.dev/packages/google_mobile_ads · https://pub.dev/packages/in_app_purchase · https://capacitorjs.com/docs/updating/plugins/8-0 · https://github.com/capacitor-community/admob/releases · https://game.ci/docs/github/activation · https://unity.com/products/pricing-updates · https://mikeschulze.github.io/gdUnit4/faq/ci · https://github.com/bitwes/Gut/releases · https://forum.godotengine.org/t/things-that-exit-0-in-godot-4-headless-even-though-they-failed-measured-reproducible/145990 · https://github.com/Patashu/break_eternity.js · https://github.com/Patashu/break_infinity.js · https://pub.dev/packages/break_eternity
