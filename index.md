# Pocket Cat privacy policy

**Effective date:** 2026-10-04 (Android from version 0.5.14; iPhone from version 0.5.25)

**Apps:** Pocket Cat for Android (package `com.pocketcat.galchi`) and Pocket Cat for iPhone (bundle ID `com.pocketcat.galchi`)

**Developer:** the Pocket Cat developer, GitHub account `jhyang12345`

**Contact:** [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com)

Pocket Cat is a game about caring for one cat. You can play as a guest on your device, or sign in to keep a cloud save for recovery after reinstalling or changing devices: with Google on Android, and with Apple or Google on iPhone.

## The short version

- Core gameplay works offline. Guest progress stays on your device.
- Optional sign-in uses Firebase Authentication: Google on Android, Sign in with Apple or Google on iPhone. Signed-in game saves are stored in Google's Cloud Firestore.
- Cloud saves include your cat, progress, gem balance, purchase-credit records and saved gameplay preferences. Photo Mode pictures stay on your device.
- Optional gem purchases use Google Play on Android and the App Store on iPhone, with RevenueCat. Their account and purchase records are described below.
- The only ad is an **optional rewarded video in the shop**, served by Google AdMob. You choose to watch it in exchange for gems; nothing in the game requires it, and there are no banners or ads that interrupt play.
- Pocket Cat does not sell your data and does not include a separate gameplay analytics or crash-reporting SDK. Purchase and ad providers also use information for their operational reporting.
- Uninstalling the app does not delete your cloud account or cloud save. You can [request account and data deletion](delete-account/), including without reinstalling the app.

## Data on your device

The game save is kept in the app's private storage. It contains the cat's name and coat, Bond progress, gems earned and spent, purchase credits, treats and cosmetics owned or equipped, saved camera preferences and postcard metadata. Device preferences such as language and reduced motion are stored separately in the app's local WebView storage.

Photo Mode keeps a local album in app-private storage. Pictures are not uploaded to Firebase or RevenueCat. On Android, exporting a picture writes it to the public **Pictures/Pocket Cat** folder and makes it available in the device's gallery. Exported copies remain there until you remove them yourself.

On Android, the app uses internet access, network-state access and Google Play Billing for sign-in, cloud saving, purchases and the optional ad, and the advertising ID permission that the Google Mobile Ads SDK adds. Android 8 and 9 require storage-write permission to export pictures to the public Pictures folder; newer Android versions use MediaStore. The app does not request access to your location, contacts, camera or microphone.

On iPhone, the game save is kept in the app's private Application Support folder and the Photo Mode album in the app's local web storage. Saving a picture adds it to your Photos library. Pocket Cat asks only for add-only access, so it cannot see or read anything else in your library. If you turn postcards on, iOS asks whether Pocket Cat may send notifications; postcards are scheduled on your device and no notification server is involved. The iPhone app does not request access to your location, contacts, camera or microphone. It never asks to track you, so iOS does not give the app or its ads SDK your device's advertising identifier.

## Google sign-in and cloud saves

Google sign-in is optional for core gameplay. It creates a Pocket Cat account in Firebase Authentication using your Google account. Firebase receives account identifiers and your email address, and can receive the display name and profile-picture URL provided by Google. Pocket Cat does not receive your Google password or access to your email inbox.

Cloud Firestore stores your current native game save under your Firebase user ID. It includes the cat and economy record, saved camera preferences and postcard metadata, together with a save revision, integrity hash, update time and a randomly generated installation identifier used to coordinate saves. It does not contain the Photo Mode album or device preferences held separately in WebView storage, such as language and reduced motion. Email and Google profile details are handled by Authentication rather than copied into the game-save document.

This information provides account management, cloud recovery and coordination between devices. Firebase also processes IP addresses and app/device information for authentication, service operation and abuse prevention. Firebase Authentication is processed in the United States; other Google services may process information internationally. See [Firebase's privacy and security information](https://firebase.google.com/support/privacy) and the [Google Privacy Policy](https://policies.google.com/privacy).

Sign in with the same account on another device to recover the last successfully uploaded save. Sign in with Apple is currently available only in the iPhone app, so a cloud save linked to an Apple account can be recovered on iPhone. Offline changes, failed uploads and guest progress may not be recoverable. Signing out or uninstalling does not remove an existing cloud save. Pocket Cat keeps the current cloud save while the account exists; there is no automatic inactivity-expiry period.

## Sign in with Apple (iPhone)

On iPhone you can also sign in with Apple. Firebase Authentication receives a stable user identifier from Apple, an email address, and your name if you choose to share it the first time you sign in. If you choose Hide My Email, Apple provides a private relay address that forwards to your real address. Pocket Cat does not receive your Apple Account password. The cloud save works the same way as with Google sign-in, as described above.

Pocket Cat checks at launch whether you still allow Sign in with Apple and signs out on the device if you have stopped using it with Pocket Cat. When you delete your cloud account in the app, Pocket Cat also revokes its Sign in with Apple authorization. You can stop using Sign in with Apple with Pocket Cat at any time in your Apple Account settings. See the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).

## Device backups

If Android backup is enabled, Android may back up the local game save and eligible app settings or transfer them between devices under Google's backup terms. The Photo Mode album and caches are excluded. You can manage Android backup in your device settings.

On iPhone, iCloud Backup or a backup to a computer may include Pocket Cat's local game save under Apple's terms. The identifier Pocket Cat uses to coordinate cloud saves for this installation is excluded from backups.

These system backups are separate from the Pocket Cat cloud save and are not a guarantee that your latest progress will be restored.

## In-app purchases

Pocket Cat sells optional one-time gem packs. Core care, play and the room are free. Guest players can purchase gems; signing in is optional. Only successfully uploaded cloud saves provide Pocket Cat account recovery of the saved balance and purchase-credit ledger.

- **Google Play** handles payment on Android. Pocket Cat does not receive card or bank details. Google's handling of payment records is covered by the [Google Play Terms of Service](https://play.google.com/about/play-terms/) and [Google Privacy Policy](https://policies.google.com/privacy).
- **The App Store** handles payment on iPhone. Pocket Cat does not receive card or bank details. Apple's handling of payment records is covered by the [Apple Media Services Terms](https://www.apple.com/legal/internet-services/itunes/) and the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).
- **RevenueCat** verifies purchases and processes purchase history and refunds. It receives Google Play purchase tokens or App Store transaction information, products and transaction details, an app-user identifier, and service-related app/device information. Its customer records can include country information from a transaction or the connection's IP address. The identifier is anonymous before account linking and uses your Firebase user ID after linking. Pocket Cat does not set your email or name as RevenueCat customer attributes. See the [RevenueCat Privacy Policy](https://www.revenuecat.com/privacy/).
- **The cloud save** contains your remaining gem balance and purchase-credit ledger. Recovering this save restores its recorded state. Consumed gem packs are not a promise of a fresh balance after reinstalling, and restoring purchase history must not grant gems that were already spent. Gems have no cash value and cannot be transferred.

Firebase and RevenueCat process information as service providers for these features. Purchase information is used for purchase handling, provider reporting and fraud prevention; it is not used for advertising or sold by Pocket Cat.

## Optional rewarded ad

The shop offers a short video ad you can choose to watch for a few gems, a limited number of times a day. Ads are served by **Google AdMob**. Nothing else in the app shows ads.

- **Consent first.** In the EEA, the UK and Switzerland, the app asks for your consent with Google's consent form before any ad is requested. You can change your choice at any time from **Settings → Privacy options**.
- **What Google AdMob receives** when an ad is requested or shown: a device identifier (on Android, the advertising ID and app set ID; on iPhone, an identifier limited to the app or its developer, because Pocket Cat never asks to track you), approximate location derived from your IP address, information about the ad and your interaction with it, and app and SDK performance (diagnostic) information. Google uses this to serve, measure and personalise ads (where you have allowed personalisation) and to prevent fraud. See [How Google uses information from sites or apps that use its services](https://policies.google.com/technologies/partner-sites) and the [Google Privacy Policy](https://policies.google.com/privacy).
- **What RevenueCat receives:** the same app-user identifier used for purchases (anonymous, or your Firebase user ID after sign-in), ad events (loaded, shown, revenue) and the reward verification result. RevenueCat confirms with Google that the ad was completed so that gems are only credited for a finished ad.
- **Advertising ID.** You can reset or delete your advertising ID in Android settings (Settings → Privacy → Ads, or Settings → Google → Ads, depending on the device). Deleting it stops personalised ads. On iPhone, Pocket Cat never shows Apple's tracking prompt, so the advertising identifier is not available to it.

Nothing ad-related starts until you open the shop: the consent form, the ads SDK and the first ad request all wait for that. An ad then loads in the background so it is ready if you choose to watch it, but it is only ever shown when you tap it.

## Retention and deletion

In the app, open **Settings → Account & cloud save → Delete cloud account** and confirm the linked Apple or Google account. This removes the current Firestore cloud save and requests deletion of the Firebase Authentication account; for an Apple account, Pocket Cat also revokes its Sign in with Apple authorization. Your cat and Photo Mode album remain on this device as guest data. On Android, clear the app's data or uninstall it to remove those local copies; on iPhone, delete the app. Previously exported photos need to be removed separately from your gallery or the Photos app.

For an account or data deletion request without the app, use the [Pocket Cat deletion page](delete-account/) or email [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com). We may ask for information needed to verify ownership. You can also request deletion of RevenueCat purchase records associated with your account or installation; those records are not automatically removed by the app's cloud-account deletion button. Purchase details can help locate an old anonymous installation record.

Firebase documents that logged Authentication IP addresses are kept for a few weeks and that other Authentication information is removed from its live and backup systems within 180 days after account deletion is initiated. Google Play and App Store payment records follow Google's and Apple's own retention policies, and device backups follow your Google or Apple backup settings. Removing a Pocket Cat account does not delete your Google or Apple account, cancel a payment or issue a refund. Ad data held by Google is governed by Google's own retention and controls; you can reset or delete your advertising ID at any time in Android settings.

Support emails contain the information you choose to send and are used to verify and handle your request. We will explain any verification needed or records that cannot be removed, and why, when responding. Do not send passwords, payment-card details or purchase tokens.

## Children

Pocket Cat is not directed at children under 13 and does not knowingly collect personal information from them. It has no chat or public user-content sharing. Its only advertising is the optional rewarded ad described above, limited to ad content suitable for general audiences with parental guidance (PG).

## Changes to this policy

Updates are published at this address with a new effective date. Material changes will be reflected here before the corresponding app version is released.
