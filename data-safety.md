# Google Play Data Safety answers for Pocket Cat

**Live answers (State C):** prepared 2026-10-02 for `com.pocketcat.galchi` 0.5.14 (versionCode 22) and entered in Play Console with that release. They declare optional Google sign-in with Firebase cloud saves, Google Play purchases verified by RevenueCat, and the opt-in rewarded ad served by Google AdMob. Earlier answer sets remain in Git history.

**Since then (2026-10 review):**

- **Since versionCode 109, the Android app has been the Unity build.** Builds up to 0.5.103 (119) have no sign-in. The owner decided on 2026-10-23 to **keep the account answers**:
  - accounts from the earlier version still exist and still need the deletion route;
  - players who signed in earlier still reach RevenueCat under their Firebase user ID.
- **Sign-in returns (owner, 2026-10-26).** Unity release builds after 0.5.103 (119) include optional Google sign-in and the Unity cloud save by default (`tools/unity-build.ps1`; `-NoCloudSave` leaves it out). The State C rows already cover it: the Unity save adds room layouts and postcard progress to the same gameplay data. The Play form needs no change; the deletion URL stays the account-deletion answer, and the app adds Settings → Account & cloud save → Delete cloud account.
- **Rewarded ads now also appear in the minigames** (paws back, next levels early), besides the shop. The data types and the AdMob sharing rows do not change.
- **The next release adds gameplay statistics and crash reports** (Google Analytics for Firebase, Firebase Crashlytics). Apply the "Analytics release" changes below with it.
- **Target audience:** 13 and over; not a Families app (owner decision, 2026-10-23).

## Overall form answers

| Question | Answer |
|---|---|
| Does the app collect or share required user data types? | **Yes** |
| Is collected user data encrypted in transit? | **Yes**, for app/SDK network traffic using HTTPS. Email support is an external request channel. |
| Account creation methods | **Other: Google sign-in / federated sign-in** (kept; see above). No Pocket Cat password is created. |
| Can users request deletion of an account and its associated data? | **Yes**: in-app deletion (Settings → Account & cloud save → Delete cloud account) in builds with sign-in, and the external request page. RevenueCat records are deleted within 30 days of an in-app deletion or a request. |
| Can users request data deletion without deleting an account? | **Yes**, via the support email request. |
| Account/data deletion URL | `https://jhyang12345.github.io/pocket-cat-privacy/delete-account/` |
| Ads | **Yes**: opt-in rewarded videos in the shop and the minigames (Google AdMob, with Meta Audience Network bidding through AdMob mediation on Android). Advertising ID declaration: Yes (analytics, advertising, fraud prevention). |
| Independent security review | No |
| Target audience / Families Policy | 13 and over; not a Families app. |

"Not shared" below relies on Play's service-provider exception: Firebase and RevenueCat process information for Pocket Cat. Google AdMob and Meta Audience Network are not service providers for this purpose, so everything the Mobile Ads and Audience Network SDKs receive is declared **shared**. Play's form does not name recipients, so Meta adds no new answer.

## Data types and purposes

### Current release (State C, unchanged)

| Play data type | Source | Required or optional | Purposes |
|---|---|---|---|
| Personal info: **Email address** | Firebase Authentication (Google sign-in, including the earlier version's); support email | Optional | App functionality, account management, fraud prevention/security |
| Personal info: **User IDs** | Firebase UID; UID as RevenueCat app-user ID while signed in | Optional | App functionality, account management, fraud prevention/security |
| Personal info: **Name** | Provider display name in Firebase Authentication | Optional | App functionality, account management |
| Financial info: **Purchase history** | Google Play purchase information in RevenueCat; purchase-credit ledger in cloud saves | Required (integrated purchase SDK) | App functionality, Analytics (provider purchase reporting), fraud prevention/security |
| App activity: **Other user-generated content** | Cat name and room layouts in cloud saves | Optional | App functionality |
| App activity: **Other actions** | Progress, gems, items, postcard progress and preferences in cloud saves | Optional | App functionality |
| **Device or other IDs** | RevenueCat anonymous app-user ID; random installation writer ID (cloud saves); **advertising ID and app set ID (AdMob SDK); advertising ID (Meta Audience Network SDK, Android)** | **Required** | App functionality, analytics, advertising or marketing, fraud prevention/security. **Shared** with Google AdMob and Meta |
| Location: **Approximate location** | IP-derived, Google Mobile Ads SDK and Meta Audience Network SDK; RevenueCat may infer country | **Required** | Analytics, advertising or marketing, fraud prevention/security. **Shared** with Google AdMob and Meta |
| App activity: **App interactions** | Ad impressions, clicks and completions (AdMob and Meta Audience Network SDKs); ad events and reward verification (RevenueCat) | **Required** | App functionality, analytics, advertising or marketing, fraud prevention/security. **Shared** with Google AdMob and Meta |
| App info and performance: **Diagnostics** | AdMob and Meta Audience Network SDK performance information | **Required** | Analytics, advertising or marketing, fraud prevention/security. **Shared** with Google AdMob and Meta |

### Analytics release (add with the first build that sends statistics)

| Play data type | Change | Required or optional | Purposes |
|---|---|---|---|
| App info and performance: **Crash logs** | **New**: Firebase Crashlytics | Optional (Settings → Share usage and crash data) | App functionality, Analytics |
| App info and performance: **Diagnostics** | Add Firebase Analytics and Crashlytics as sources | **Stays Required**: the AdMob SDK still collects diagnostics whatever the analytics setting | Add App functionality to the existing purposes |
| App activity: **App interactions** | Add Firebase Analytics as a source (screens and game features used) | **Stays Required** for the same reason | Existing purposes (Analytics already listed) |
| **Device or other IDs** | Add the Firebase app-instance ID and the Crashlytics installation UUID | **Stays Required** for the same reason | Existing purposes |
| Location: **Approximate location** | Add Firebase Analytics (IP-derived region) as a source | **Stays Required** | Existing purposes |

Play's form takes one Required/Optional answer per data type. Only Crash logs come from analytics alone, so only that row is Optional.

The setting counts as a real choice everywhere: off by default in the EEA and Switzerland, and on with an opt-out elsewhere. Recheck Play's current definition of "optional" before submitting.

**Retention to disclose:**
- Google Analytics data retention is set to 2 months.
- Raw events are kept up to 90 days. The BigQuery sandbox expires tables after 60 days.
- Crashlytics keeps crash reports for 90 days.
- Totals that cannot identify an installation are kept up to 13 months.

## Retention and deletion review before each release

- Publish the revised privacy policy (`/`, `/ko/`) and the `/delete-account/` page, then check every public URL without being signed in to GitHub.
- **Outside-app requests:**
  - Verify ownership.
  - Find the Firebase UID from the email, delete `/players/{uid}/saves/current` and `/players/{uid}/saves/unity`, and the Authentication user.
  - Delete the matching RevenueCat customer and aliases within 30 days.
  - Delete matching analytics data where an install date allows it.
  - Confirm what was removed.
- **In-app deletion (builds with sign-in):**
  - It removes the cloud saves and the Firebase user immediately.
  - It queues the RevenueCat customer in Firestore `deletionRequests`, which the owner completes within 30 days (owner decision, 2026-10-23; the project stays on the Spark plan, so there is no server-side automatic deletion). The game repository's `tools/cloud-save/deletion-queue.mjs` lists the queue and completes it.
  - Passed on a signed device build on 2026-10-24, including an interrupted deletion finished from the app.
- Firebase Authentication's documented retention is a few weeks for logged IPs and up to 180 days after deletion for other authentication information. Do not promise immediate provider-backup erasure.
- Match the public privacy policy, the Play form answers and the actual release behavior. Submit new answers together with the release that needs them.

## Official reference material

- [Google Play account deletion requirements](https://support.google.com/googleplay/android-developer/answer/13327111?hl=en)
- [Google Play Data Safety definitions](https://support.google.com/googleplay/android-developer/answer/10787469?hl=en)
- [Firebase Android SDK disclosure guide](https://firebase.google.com/docs/android/play-data-disclosure)
- [Firebase privacy, retention and processing locations](https://firebase.google.com/support/privacy)
- [Google Analytics data retention](https://support.google.com/analytics/answer/7667196)
- [RevenueCat Google Play Data Safety guidance](https://www.revenuecat.com/docs/platform-resources/google-platform-resources/google-plays-data-safety)
- [Google Mobile Ads SDK data disclosure](https://developers.google.com/admob/android/privacy/play-data-disclosure)

## Store listing document URLs

- Privacy policy: `https://jhyang12345.github.io/pocket-cat-privacy/` (Korean: `https://jhyang12345.github.io/pocket-cat-privacy/ko/`)
- Account and data deletion: `https://jhyang12345.github.io/pocket-cat-privacy/delete-account/`
