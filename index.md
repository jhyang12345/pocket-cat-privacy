# Pocket Cat privacy policy

**Effective date:** 2026-10-01

**App:** Pocket Cat for Android (package `com.pocketcat.galchi`)

**Developer:** the Pocket Cat developer, GitHub account `jhyang12345`

**Contact:** [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com)

Pocket Cat is a game about caring for one cat. You can play as a guest on your device, or sign in with Google to keep a cloud save for recovery after reinstalling or changing devices.

## The short version

- Core gameplay works offline. Guest progress stays on your device.
- Optional Google sign-in uses Firebase Authentication. Signed-in game saves are stored in Google's Cloud Firestore.
- Cloud saves include your cat, progress, gem balance, purchase-credit records and saved gameplay preferences. Photo Mode pictures stay on your device.
- Optional gem purchases use Google Play and RevenueCat. Their account and purchase records are described below.
- Pocket Cat has no advertising, does not sell your data, and does not include a separate gameplay analytics or crash-reporting SDK. Purchase providers also use purchase information for their operational reporting.
- Uninstalling the app does not delete your cloud account or cloud save. You can [request account and data deletion](delete-account/), including without reinstalling the app.

## Data on your device

The game save is kept in the app's private storage. It contains the cat's name and coat, Bond progress, gems earned and spent, purchase credits, treats and cosmetics owned or equipped, saved camera preferences and postcard metadata. Device preferences such as language and reduced motion are stored separately in the app's local WebView storage.

Photo Mode keeps a local album in app-private storage. Pictures are not uploaded to Firebase or RevenueCat. Exporting a picture writes it to the public **Pictures/Pocket Cat** folder and makes it available in the device's gallery. Exported copies remain there until you remove them yourself.

The app uses internet access, network-state access and Google Play Billing for sign-in, cloud saving and purchases. Android 8 and 9 require storage-write permission to export pictures to the public Pictures folder; newer Android versions use MediaStore. The app does not request access to your location, contacts, camera or microphone.

## Google sign-in and cloud saves

Google sign-in is optional for core gameplay. It creates a Pocket Cat account in Firebase Authentication using your Google account. Firebase receives account identifiers and your email address, and can receive the display name and profile-picture URL provided by Google. Pocket Cat does not receive your Google password or access to your email inbox.

Cloud Firestore stores your current native game save under your Firebase user ID. It includes the cat and economy record, saved camera preferences and postcard metadata, together with a save revision, integrity hash, update time and a randomly generated installation identifier used to coordinate saves. It does not contain the Photo Mode album or device preferences held separately in WebView storage, such as language and reduced motion. Email and Google profile details are handled by Authentication rather than copied into the game-save document.

This information provides account management, cloud recovery and coordination between devices. Firebase also processes IP addresses and app/device information for authentication, service operation and abuse prevention. Firebase Authentication is processed in the United States; other Google services may process information internationally. See [Firebase's privacy and security information](https://firebase.google.com/support/privacy) and the [Google Privacy Policy](https://policies.google.com/privacy).

Sign in with the same Google account on another device to recover the last successfully uploaded save. Offline changes, failed uploads and guest progress may not be recoverable. Signing out or uninstalling does not remove an existing cloud save. Pocket Cat keeps the current cloud save while the account exists; there is no automatic inactivity-expiry period.

## Android backup

If Android backup is enabled, Android may back up the local game save and eligible app settings or transfer them between devices under Google's backup terms. The Photo Mode album and caches are excluded. This system backup is separate from the Pocket Cat cloud save and is not a guarantee that your latest progress will be restored. You can manage Android backup in your device settings.

## In-app purchases

Pocket Cat sells optional one-time gem packs. Core care, play and the room are free. Guest players can purchase gems; linking a Google account is optional. Only successfully uploaded cloud saves provide Pocket Cat account recovery of the saved balance and purchase-credit ledger.

- **Google Play** handles payment. Pocket Cat does not receive card or bank details. Google's handling of payment records is covered by the [Google Play Terms of Service](https://play.google.com/about/play-terms/) and [Google Privacy Policy](https://policies.google.com/privacy).
- **RevenueCat** verifies purchases and processes purchase history and refunds. It receives purchase tokens, products and transaction information, an app-user identifier, and service-related app/device information. Its customer records can include country information from a transaction or the connection's IP address. The identifier is anonymous before account linking and uses your Firebase user ID after linking. Pocket Cat does not set your Google email or display name as RevenueCat customer attributes. See the [RevenueCat Privacy Policy](https://www.revenuecat.com/privacy/).
- **The cloud save** contains your remaining gem balance and purchase-credit ledger. Recovering this save restores its recorded state. Consumed gem packs are not a promise of a fresh balance after reinstalling, and restoring purchase history must not grant gems that were already spent. Gems have no cash value and cannot be transferred.

Firebase and RevenueCat process information as service providers for these features. Purchase information is used for purchase handling, provider reporting and fraud prevention; it is not used for advertising or sold by Pocket Cat.

## Retention and deletion

In the app, open **Settings → Account & cloud save → Delete cloud account** and confirm the linked Google account. This removes the current Firestore cloud save and requests deletion of the Firebase Authentication account. Your cat and Photo Mode album remain on this device as guest data. Clear the app's data or uninstall it to remove those local copies. Previously exported photos need to be removed separately.

For an account or data deletion request without the app, use the [Pocket Cat deletion page](delete-account/) or email [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com). We may ask for information needed to verify ownership. You can also request deletion of RevenueCat purchase records associated with your account or installation; those records are not automatically removed by the app's cloud-account deletion button. Purchase details can help locate an old anonymous installation record.

Firebase documents that logged Authentication IP addresses are kept for a few weeks and that other Authentication information is removed from its live and backup systems within 180 days after account deletion is initiated. Google Play payment records and Android backups follow Google's own retention and account controls. Removing a Pocket Cat account does not delete your Google account, cancel a payment or issue a refund.

Support emails contain the information you choose to send and are used to verify and handle your request. We will explain any verification needed or records that cannot be removed, and why, when responding. Do not send passwords, payment-card details or purchase tokens.

## Children

Pocket Cat is not directed at children under 13 and does not knowingly collect personal information from them. It has no chat, public user-content sharing or advertising.

## Changes to this policy

Updates are published at this address with a new effective date. Material changes will be reflected here before the corresponding app version is released.
