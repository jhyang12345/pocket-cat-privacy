# Google Play Data Safety — draft answers for Pocket Cat

Prepared 2026-09-22 for package `com.pocketcat.galchi`. Two states are recorded because the answers change when in-app purchases are switched on.

## State A — current build (no purchases wired)

| Question | Answer |
|---|---|
| Does your app collect or share any of the required user data types? | **No** |
| Is all user data encrypted in transit? | Not applicable (no data leaves the device) |
| Do you provide a way for users to request that their data is deleted? | Yes — uninstall or clear app data removes everything |
| Committed to the Play Families Policy? | No (not directed at children) |
| Independent security review? | No |

Rationale: the WebView blocks network loads, the manifest declares no permissions, there are no SDKs. The game save and photo album stay in app-private storage. Android Auto Backup is Google's system feature and does not count as developer collection.

## State B — with Google Play Billing through RevenueCat

Collection and sharing to declare:

| Data type | Collected | Shared | Ephemeral | Required | Purposes |
|---|---|---|---|---|---|
| Financial info → **Purchase history** | Yes | Yes (RevenueCat, service provider) | No | Required for purchase features | App functionality, fraud prevention |
| Device or other IDs | Yes (anonymous app user ID generated per install; device/app metadata RevenueCat records) | Yes (RevenueCat) | No | Required for purchase features | App functionality, fraud prevention |

Not collected: name, email, address, phone, location, contacts, messages, photos (album is on-device only, never uploaded), files, audio, health, browsing, app activity, crash logs, diagnostics, advertising ID.

| Question | Answer |
|---|---|
| Is all user data encrypted in transit? | Yes (RevenueCat SDK uses HTTPS) |
| Do you provide a way for users to request deletion? | Yes — email jhyang123494@gmail.com; RevenueCat customer deletion on request |
| Data handling practices | Data is not sold; not used for advertising or marketing; not used for personalization beyond crediting the user's own purchases |
| Account creation | None; purchases are tied to the Google Play account and an anonymous ID |

Before switching to State B: add the INTERNET permission, update the privacy policy's purchases section from "when enabled" to present tense, and re-submit the Data Safety form in the same release.

## Store listing fields that reference these documents

- Privacy policy URL: the GitHub Pages URL of this repository (`index.md`).
- Ads: No. Contains in-app purchases: No in State A, Yes in State B.
- Target audience: 13 and over. Not a Families app.
