# Google Play Data Safety — draft answers for Pocket Cat

Prepared 2026-09-22 for package `com.pocketcat.galchi`. Two states are recorded because the answers change when in-app purchases are switched on.

## State A — builds up to 0.5.0 (no purchases wired; superseded)

| Question | Answer |
|---|---|
| Does your app collect or share any of the required user data types? | **No** |
| Is all user data encrypted in transit? | Not applicable (no data leaves the device) |
| Do you provide a way for users to request that their data is deleted? | Yes — uninstall or clear app data removes everything |
| Committed to the Play Families Policy? | No (not directed at children) |
| Independent security review? | No |

Rationale: the WebView blocks network loads, the manifest declares no permissions, there are no SDKs. The game save and photo album stay in app-private storage. Android Auto Backup is Google's system feature and does not count as developer collection.

## State B — current, from 0.5.1 (Google Play Billing through RevenueCat)

Collection and sharing to declare:

| Data type | Collected | Shared | Ephemeral | Required | Purposes |
|---|---|---|---|---|---|
| Financial info → **Purchase history** | Yes | No — RevenueCat is a service provider, which Play does not count as sharing | No | Required for purchase features | App functionality, fraud prevention |
| Device or other IDs | Yes (anonymous app user ID generated per install; device/app metadata RevenueCat records) | No (RevenueCat, service provider) | No | Required for purchase features | App functionality, fraud prevention |

Not collected: name, email, address, phone, location, contacts, messages, photos (album is on-device only, never uploaded), files, audio, health, browsing, app activity, crash logs, diagnostics, advertising ID.

| Question | Answer |
|---|---|
| Is all user data encrypted in transit? | Yes (RevenueCat SDK uses HTTPS) |
| Do you provide a way for users to request deletion? | Yes — email jhyang123494@gmail.com; RevenueCat customer deletion on request |
| Data handling practices | Data is not sold; not used for advertising or marketing; not used for personalization beyond crediting the user's own purchases |
| Account creation | None; purchases are tied to the Google Play account and an anonymous ID |

Submitted in Play Console 2026-09-25 with these answers; deletion link https://jhyang12345.github.io/pocket-cat-privacy/#deleting-your-data. Switched 2026-09-25: the app declares INTERNET, ACCESS_NETWORK_STATE and BILLING from 0.5.1, and the privacy policy describes purchases in the present tense. Submit these answers with the 0.5.1 release.

## State C — from the release that adds the optional rewarded ad (Google AdMob + RevenueCat Ad Monetization)

Adds Google AdMob (rewarded video in the shop only) and RevenueCat ad-event tracking to State B. Everything in State B still applies.

| Data type | Collected | Shared | Ephemeral | Required | Purposes |
|---|---|---|---|---|---|
| Financial info → **Purchase history** | Yes | No (RevenueCat, service provider) | No | Required for purchase features | App functionality, fraud prevention |
| Device or other IDs | Yes — anonymous app user ID (RevenueCat); advertising ID and app set ID (AdMob SDK) | **Yes** — Google AdMob | No | Optional (only when the user chooses the rewarded ad) | Advertising or marketing, analytics, fraud prevention, security and compliance; app functionality for the RevenueCat ID |
| Location → **Approximate location** | Yes (derived from IP by the AdMob SDK) | **Yes** — Google AdMob | No | Optional | Advertising or marketing, analytics, fraud prevention |
| App activity → **App interactions** | Yes (ad impressions, clicks, completions; RevenueCat ad events) | **Yes** — Google AdMob | No | Optional | Advertising or marketing, analytics, app functionality (reward verification) |
| App info and performance → **Diagnostics** | Yes (AdMob SDK: app and SDK performance such as launch time and hang rate) | **Yes** — Google AdMob | No | Optional | Analytics, fraud prevention |

Notes:

- Google's AdMob data disclosure guidance lists these types for the Mobile Ads SDK; check it again at submission time for SDK changes: https://developers.google.com/admob/android/privacy/play-data-disclosure
- AdMob counts as **sharing** (Google acts as an independent party for ads), unlike RevenueCat, which is a service provider.
- "Optional": no ad request is made unless the user taps the shop's rewarded-ad card, and in the EEA/UK/CH not before consent.

| Question | Answer |
|---|---|
| Is all user data encrypted in transit? | Yes |
| Do you provide a way for users to request deletion? | Yes — same as State B; ad data: reset or delete the advertising ID in Android settings |
| Data handling practices | Data is not sold. Device IDs, approximate location and app interactions are used for advertising only through the opt-in rewarded ad |
| Advertising ID declaration | Yes — the app uses the advertising ID (AD_ID permission from the Mobile Ads SDK) for advertising and analytics |
| Ads declaration | **Yes**, the app contains ads (Play shows "Contains ads") |

Submit State C together with the first release that contains the ad. Until then State B stays live.

## Store listing fields that reference these documents

- Privacy policy URL: the GitHub Pages URL of this repository (`index.md`).
- Ads: No in States A and B; **Yes in State C**. Contains in-app purchases: No in State A, Yes in States B and C.
- Target audience: 13 and over. Not a Families app.
