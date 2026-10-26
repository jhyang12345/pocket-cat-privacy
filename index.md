# Pocket Cat privacy policy

**Effective date:** 2026-10-26 (Android from the first update with gameplay statistics, with Meta Audience Network, with sign-in and with the questions after adoption from the first updates that include them; iPhone from the first version built on the shared game)

**Apps:** Pocket Cat for Android (package `com.pocketcat.galchi`) and Pocket Cat for iPhone (bundle ID `com.pocketcat.galchi`)

**Developer:** the Pocket Cat developer, GitHub account `jhyang12345`

**Contact:** [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com)

**한국어:** [개인정보 처리방침 (한국어)](ko/). For players in Korea, the Korean policy is the authoritative version and includes the items required by Korea's Personal Information Protection Act.

Pocket Cat is a game about caring for one cat. You can play as a guest on your device, or sign in to keep a cloud save for recovery after reinstalling or changing phones: with Google on Android, and with Apple or Google on iPhone. No account is needed to play.

## The short version

- Core gameplay works offline. Your cat and your progress are saved on your device.
- Pocket Cat sends gameplay statistics and crash reports to Google's Firebase so we can see where the game is confusing and fix crashes. They are tied to a random app ID, not to your name or any account, and never include your cat's name or anything you type. The app asks about this right after you adopt your cat, and you can change your answer at any time in **Settings → Share usage and crash data**. If your App Store or Google Play account is in the European Economic Area or Switzerland, nothing is sent unless you turn it on.
- Optional gem purchases use Google Play on Android and the App Store on iPhone, with RevenueCat.
- Ads are **optional rewarded videos** requested through Google AdMob; on Android they may also come from Meta Audience Network. They appear in the shop for a few gems, and in the minigames to get paws back or open the next levels early. You choose to watch them; nothing in the game requires it, and there are no banners or ads that interrupt play.
- Pocket Cat does not sell your data.
- Sign-in is optional: Google on Android, and Sign in with Apple or Google on iPhone. Signed-in game saves are stored in Google's Cloud Firestore in Seoul. Photos and device settings stay on your device. See [Sign-in and cloud saves](#sign-in-and-cloud-saves).
- Uninstalling the app does not delete your cloud account. You can delete it in the app, or [request account and data deletion](delete-account/) without the app.

## Data on your device

The game save is kept in the app's private storage. It contains your cat's name and coat, Bond and progress, gems earned and spent and the identifiers of purchases and ad rewards (so nothing is credited twice), treats, accessories, rooms, wallpapers and floors you own, the furniture layout of each room, and your postcard progress. Device preferences such as language, sound, haptics, camera, room lighting and your choice about gameplay statistics are kept in the app's local preferences.

Photos you take in the cat studio or Photo Mode stay in the app's private storage. Saving or sharing a photo hands that picture to your device's gallery or share sheet only when you choose to.

Postcards, if you turn them on, are scheduled on your device and shown as local notifications. No notification server is involved and nothing about them is sent to us.

On Android, the app uses internet access, network-state access and Google Play Billing for statistics, purchases and the optional ads; the advertising ID permission added by the Google Mobile Ads SDK; the notification permission if you turn postcards on; and the install-referrer service that Google Analytics for Firebase reads to learn which store listing or link led to the install. The app does not request access to your location, contacts, camera or microphone.

On iPhone, saving a picture adds it to your Photos library with add-only access, so Pocket Cat cannot see or read anything else in your library. If you turn postcards on, iOS asks whether Pocket Cat may send notifications. Pocket Cat does not request access to your location, contacts, camera or microphone, and it never asks to track you, so iOS does not give the app or its ads SDK your device's advertising identifier.

## Gameplay statistics and crash reports

Pocket Cat sends gameplay statistics through Google Analytics for Firebase and crash reports through Firebase Crashlytics. When you adopt a cat, the app asks about this right away: where your consent is needed, nothing is sent unless you choose Share; elsewhere the question tells you that sending is on and lets you turn it off. You can change your answer at any time in **Settings → Share usage and crash data**. If your App Store or Google Play account is in the European Economic Area or Switzerland, it is off until you turn it on. Everywhere else, including the United Kingdom and Korea, it is on until you turn it off. To tell which applies, the app uses your store account's country or, when that is not available, your SIM card's country or your phone's region setting. If none is available, it stays off. The country is used on your device only to choose this default and is not sent to us.

**What is sent:** which screens you open and which game features you use (for example adopting, finishing a daily quest, starting or clearing a minigame, buying an item with gems, choosing to watch an optional ad, or moving rooms), how many days since adoption and how long you play, and, when the app crashes, technical details about the crash with your device model and system version. Each record carries a random identifier that Firebase creates for this installation. Google Analytics for Firebase also receives your IP address, from which it derives an approximate region, and on Android the install referrer described above.

**What is not sent:** your cat's name or anything you type, any Google or Apple account, your email, purchase receipts or tokens, your game save, your precise location, photos, or the advertising identifier. Statistics are not used for advertising and are not combined with data from other apps.

**Turning it off** stops statistics and crash reports immediately, resets the random identifier on your device and deletes crash reports that have not been sent yet.

**How long it is kept:**

- Google Analytics keeps event-level data for **2 months**.
- Raw events copied for analysis are kept for up to **90 days**.
- Crash reports are kept for **90 days**.
- Totals that cannot identify an installation, such as how many players finished a chapter on a given day, may be kept for up to **13 months**.

This data is not linked to an account, so it cannot be looked up from your name or email. To ask us to delete it, contact us and include the date you installed the app.

Google processes this data for us as a service provider. See [Firebase's privacy and security information](https://firebase.google.com/support/privacy) and the [Google Privacy Policy](https://policies.google.com/privacy).

## Sign-in and cloud saves

Sign-in is optional. It creates a Pocket Cat account in Firebase Authentication with Google (Android and iPhone) or Sign in with Apple (iPhone). Firebase holds a user identifier, your email address (or an Apple private relay address if you choose Hide My Email) and the name your provider shares. The app shows the email in Settings. Pocket Cat never receives your Google or Apple password.

When you sign in, Pocket Cat keeps one cloud save for your account in Google's Cloud Firestore (region asia-northeast3, Seoul). The cloud save contains:

- your cat's name and coat, Bond and progress;
- your gem balance and gem history;
- the identifiers of your purchases and ad rewards, used so a purchase is never credited twice;
- the items you own and the furniture layout of each room;
- your postcard progress.

It also records when it was saved and a random identifier for this installation. Only your signed-in account can read or write it. Photos and device settings such as language and sound are never uploaded. On your device, the app also remembers which account protects your cat.

If you used the earlier version of Pocket Cat with the same account, a new installation that has no cat yet may read that earlier cloud save once, to offer bringing your cat over. Pocket Cat never changes the earlier save. Accounts from the earlier version, with the name and profile-picture URL their provider shared, still exist until you delete them.

While you are signed in, RevenueCat uses your Firebase user identifier as your purchase identity. When you sign out or delete the account, it returns to an anonymous identifier. Gameplay statistics are never linked to your sign-in.

On Android, sign-in returns with the first update that includes it. Until your app has it, use the [deletion page](delete-account/) or email us to delete an earlier account and its cloud save.

Firebase Authentication is processed in the United States, and the cloud save is stored in Seoul. See [Firebase's privacy and security information](https://firebase.google.com/support/privacy), the [Google Privacy Policy](https://policies.google.com/privacy) and, for Sign in with Apple, the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).

### Sign in with Apple (iPhone)

Pocket Cat checks at launch whether you still allow Sign in with Apple, and signs out on the device if you have stopped using it with Pocket Cat. When you delete your cloud account in the app, Pocket Cat also revokes its Sign in with Apple authorization. You can stop using Sign in with Apple with Pocket Cat at any time in your Apple Account settings.

## Device backups

If Android backup is enabled, Android may back up the game save, the app's local preferences and which account protects your cat, or transfer them between devices, under Google's backup terms. The preferences include the anonymous purchase identity, so a restored save keeps its purchases. Photos, caches and the earlier version's web storage are excluded. You can manage Android backup in your device settings.

On iPhone, iCloud Backup or a backup to a computer may include Pocket Cat's local game save under Apple's terms.

These system backups are not a guarantee that your latest progress will be restored.

## In-app purchases

Pocket Cat sells optional one-time gem packs. Care and play are always free, and gems can also be earned by playing. No account is needed to buy gems.

- **Google Play** handles payment on Android. Pocket Cat does not receive card or bank details. Google's handling of payment records is covered by the [Google Play Terms of Service](https://play.google.com/about/play-terms/) and [Google Privacy Policy](https://policies.google.com/privacy).
- **The App Store** handles payment on iPhone. Pocket Cat does not receive card or bank details. Apple's handling of payment records is covered by the [Apple Media Services Terms](https://www.apple.com/legal/internet-services/itunes/) and the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).
- **RevenueCat** verifies purchases and processes purchase history and refunds. It receives Google Play purchase tokens or App Store transaction information, products and transaction details, an app-user identifier, and service-related app/device information. Its customer records can include country information from a transaction or the connection's IP address. The identifier is anonymous, or your Firebase user identifier while you are signed in (or from an earlier version's sign-in). Pocket Cat does not send your email or name to RevenueCat. See the [RevenueCat Privacy Policy](https://www.revenuecat.com/privacy/).
- **Your gem balance** and purchase-credit ledger live in the game save on your device and in device backups, and in your cloud save if you sign in. Gems have no cash value and cannot be transferred.

RevenueCat processes information as a service provider. Purchase information is used for purchase handling, provider reporting and fraud prevention; it is not used for advertising or sold by Pocket Cat.

## Optional rewarded ads

You can choose to watch a short video ad, each a limited number of times a day:

- in the shop, for a few gems;
- in the minigames, to get paws back when they run out;
- in the minigames, to open the next levels before tomorrow.

Ads are requested through **Google AdMob**. On Android, AdMob holds an auction for each ad in which **Meta Audience Network** can also bid, so the video may come from Google or from Meta. On iPhone, ads come from Google AdMob only. There are no banners and nothing interrupts play.

- **Consent first.** In the EEA, the UK and Switzerland, the app asks for your consent with Google's consent form before any ad is requested. The form lists Meta among the ad partners, and your choice applies to it too. You can change your choice at any time from **Settings → Privacy options**.
- **When ads start.** When you adopt a cat, right after our own question about usage data, the app checks with Google whether the law needs your ad consent and, where it does, shows Google's consent form. If you adopted your cat before this check was added, the form waits until an ad offer is first on screen. The ads SDK and the first ad request always wait until an ad offer is first on screen, in the shop or in the minigames. An ad then loads in the background so it is ready if you choose to watch it, but it is only ever shown when you tap it. On Android, Meta's SDK may start when the app opens and contact Meta's servers; it bids for and shows an ad only when AdMob asks it to, for an ad you have chosen to watch.
- **What Google AdMob receives** when an ad is requested or shown:
  - a device identifier: on Android, the advertising ID and app set ID; on iPhone, an identifier limited to the app or its developer, because Pocket Cat never asks to track you;
  - approximate location derived from your IP address;
  - information about the ad and your interaction with it;
  - app and SDK performance (diagnostic) information.

  Google uses this to serve, measure and personalise ads (where you have allowed personalisation) and to prevent fraud. See [How Google uses information from sites or apps that use its services](https://policies.google.com/technologies/partner-sites) and the [Google Privacy Policy](https://policies.google.com/privacy).
- **What Meta Audience Network receives** (Android only) when it bids for or shows an ad:
  - the advertising ID;
  - information about your device and the app;
  - approximate location derived from your IP address;
  - information about the ad and your interaction with it;
  - diagnostic information.

  Meta uses this to serve and measure ads and to prevent fraud. See the [Meta Privacy Policy](https://www.facebook.com/privacy/policy/).
- **What RevenueCat receives:** the same app-user identifier used for purchases, ad events (loaded, shown, revenue) and the reward verification result. RevenueCat confirms with Google that the ad was completed, so a reward is only credited for a finished ad.
- **Advertising ID.** You can reset or delete your advertising ID in Android settings (Settings → Privacy → Ads, or Settings → Google → Ads, depending on the device). Deleting it stops personalised ads.

## Where data is processed

Google (Firebase, AdMob, Google Play), Meta (Audience Network, on Android) and RevenueCat are based in the United States and may process data there and in other countries where they operate. Apple processes App Store payments under its own terms. Signed-in cloud saves are stored in Google's Cloud Firestore in Seoul (asia-northeast3). Pocket Cat itself does not run servers that store your data. Players in Korea can find the overseas-transfer details required by Korean law in the [Korean policy](ko/#overseas-transfer).

## Your choices and rights

- Turn gameplay statistics and crash reports off in **Settings → Share usage and crash data**.
- Change ad consent in **Settings → Privacy options** where it applies, and reset or delete your advertising ID in Android settings.
- See your account and its last cloud save in **Settings → Account & cloud save**, sign out there, or delete the cloud account.
- Ask us to access, correct or delete data we hold or can request from our providers: your account and cloud save, RevenueCat purchase records, or gameplay statistics (include your install date). Email [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com) or use the [deletion page](delete-account/). We may ask for information needed to verify ownership and will reply with the result, including anything that cannot be removed and why.
- To remove the data on your device, clear Pocket Cat's app data or uninstall it on Android, or delete the app on iPhone. Photos you saved to your gallery or Photos library stay there until you remove them.

## Retention and deletion

In the app, open **Settings → Account & cloud save → Delete cloud account** and confirm your Apple or Google account. This happens immediately:

- Pocket Cat deletes your cloud save, including any save from the earlier version of the app.
- It deletes your Firebase Authentication account.
- For an Apple account, it revokes its Sign in with Apple authorization.

It also queues your purchase records at RevenueCat for deletion, and we complete that within 30 days. Your cat stays on this device as guest data. Payment records kept by Google Play and the App Store follow their own policies.

- **On your device:** kept until you delete the app's data or the app.
- **Gameplay statistics and crash reports:** as described above (2 months, up to 90 days of raw events, 90 days of crash reports, and up to 13 months of totals that identify no one).
- **Accounts and cloud saves:** kept while the account exists, and deleted when you delete it in the app or ask us. Firebase documents that logged Authentication IP addresses are kept for a few weeks, and that other Authentication information is removed from its live and backup systems within 180 days after deletion is initiated.
- **RevenueCat purchase records:** deleted within 30 days of an in-app account deletion or a request.
- **Store payment records:** Google Play and App Store records follow Google's and Apple's own retention policies.
- **Ad data:** data held by Google or Meta is governed by their own retention and controls.
- **Support emails:** used to verify and handle your request.

Deleting Pocket Cat data does not delete your Google or Apple account, cancel a payment or issue a refund. Do not send passwords, payment-card details or purchase tokens.

## Children

Pocket Cat is intended for players aged 13 and over. It is not directed at children under 13 and does not knowingly collect personal information from them. In Korea, the service is not directed at children under 14. It has no chat or public user-content sharing. Google ads are limited to content suitable for general audiences with parental guidance (PG). Meta ads exclude sensitive categories such as gambling, alcohol, dating, and sexually suggestive or adult content.

## Privacy officer

Privacy questions and requests are handled by the Pocket Cat privacy contact (Pocket Cat 개인정보 담당), reachable at [jhyang123494@gmail.com](mailto:jhyang123494@gmail.com).

## Changes to this policy

Updates are published at this address with a new effective date. Material changes will be reflected here before the corresponding app version is released.
