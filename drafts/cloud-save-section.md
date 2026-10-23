---
published: false
---

# Draft: sign-in and cloud save (Unity)

**Not published** (`published: false`). Apply this to `index.md`, `ko/index.md`, `support.md` and `delete-account.md` when a release is built with the cloud-save switch on (`tools/unity-build.ps1 -CloudSave` in the game repository). Set a new effective date and publish first.

Source: `docs/store/cloud-save-privacy-draft.md` in the game repository, plus two owner decisions from 2026-10-23:

- in-app deletion queues RevenueCat deletion, completed within 30 days;
- the project stays on the Firebase Spark plan, so no server deletes RevenueCat data automatically.

## index.md

**Intro paragraph.** Replace the second paragraph with:

> Pocket Cat is a game about caring for one cat. You can play as a guest on your device, or sign in to keep a cloud save for recovery after reinstalling or changing phones: with Google on Android, and with Apple or Google on iPhone.

**The short version.** Replace the "earlier version" bullet with:

> - Sign-in is optional: Google on Android, and Sign in with Apple or Google on iPhone. Signed-in game saves are stored in Google's Cloud Firestore in Seoul. Photos and device settings stay on your device.
> - Uninstalling the app does not delete your cloud account. You can delete it in the app, or [request account and data deletion](delete-account/) without the app.

**Replace "Accounts from the earlier version" with:**

> ## Sign-in and cloud saves
>
> Sign-in is optional. It creates a Pocket Cat account in Firebase Authentication with Google (Android and iPhone) or Sign in with Apple (iPhone). Firebase holds a user identifier, your email address (or an Apple private relay address if you choose Hide My Email) and the name your provider shares. The app shows the email in Settings. Pocket Cat never receives your Google or Apple password.
>
> When you sign in, Pocket Cat keeps one cloud save for your account in Google's Cloud Firestore (region asia-northeast3, Seoul). The cloud save contains:
>
> - your cat's name and coat, Bond and progress;
> - your gem balance and gem history;
> - the identifiers of your purchases and ad rewards, used so a purchase is never credited twice;
> - the items you own and the furniture layout of each room;
> - your postcard progress.
>
> It also records when it was saved and a random identifier for this installation. Only your signed-in account can read or write it. Photos and device settings such as language and sound are never uploaded.
>
> If you used the earlier version of Pocket Cat with the same account, a new installation that has no cat yet may read that earlier cloud save once, to offer bringing your cat over. Pocket Cat never changes the earlier save.
>
> While you are signed in, RevenueCat uses your Firebase user identifier as your purchase identity. When you sign out or delete the account, it returns to an anonymous identifier. Gameplay statistics are never linked to your sign-in.
>
> Firebase Authentication is processed in the United States, and the cloud save is stored in Seoul. See [Firebase's privacy and security information](https://firebase.google.com/support/privacy), the [Google Privacy Policy](https://policies.google.com/privacy) and, for Sign in with Apple, the [Apple Privacy Policy](https://www.apple.com/legal/privacy/).
>
> ### Sign in with Apple (iPhone)
>
> Pocket Cat checks at launch whether you still allow Sign in with Apple, and signs out on the device if you have stopped using it with Pocket Cat. When you delete your cloud account in the app, Pocket Cat also revokes its Sign in with Apple authorization. You can stop using Sign in with Apple with Pocket Cat at any time in your Apple Account settings.

**Retention and deletion.** Add first:

> In the app, open **Settings → Account & cloud save → Delete cloud account** and confirm your Apple or Google account. This happens immediately:
>
> - Pocket Cat deletes your cloud save, including any save from the earlier version of the app.
> - It deletes your Firebase Authentication account.
> - For an Apple account, it revokes its Sign in with Apple authorization.
>
> It also queues your purchase records at RevenueCat for deletion, and we complete that within 30 days. Your cat stays on this device as guest data. Payment records kept by Google Play and the App Store follow their own policies.

**Retention list.** Replace the "Earlier accounts" and "RevenueCat" items with:

> - **Accounts and cloud saves:** kept while the account exists and deleted when you delete it in the app or ask us. Firebase removes Authentication information from its live and backup systems within 180 days.
> - **RevenueCat purchase records:** deleted within 30 days of an in-app account deletion or a request.

## ko/index.md

**Section 2, items collected.** Add this row:

| 구분 | 항목 | 수집 방법 |
|---|---|---|
| 선택 로그인과 클라우드 저장 | Firebase 사용자 식별자, 이메일(또는 Apple 비공개 릴레이 주소), 로그인 제공자가 공유한 이름, 클라우드 저장 데이터(고양이 이름과 털 색, 유대감과 진행도, 보석 잔액과 내역, 구매·광고 보상 식별자, 보유 아이템, 방별 가구 배치, 엽서 진행 상황, 저장 시각, 설치 식별자) | 이용자가 로그인할 때 |

**Section 3, retention.** Add:

> 계정과 클라우드 저장 데이터: 앱에서 계정을 삭제하거나 삭제를 요청할 때까지. 앱에서 삭제하면 즉시 지우고, Firebase 인증 정보는 Google 백업에서 180일 이내에 지워집니다. RevenueCat 구매 기록은 계정 삭제 후 30일 이내에 지웁니다.

**Overseas transfer table.** Add:
- Google LLC (Firebase Authentication): 미국.
- Cloud Firestore: 대한민국 서울 리전(asia-northeast3), operated by Google.

## delete-account.md

Replace the last paragraph of "Data on your device" with:

> ## Delete the cloud account in the app
>
> In Pocket Cat, open **Settings → Account & cloud save → Delete cloud account**, then confirm the same Apple or Google account you linked to your cat. Internet access is required. This happens immediately:
>
> - Pocket Cat removes both cloud saves (the current one and any from the earlier version).
> - It removes the Firebase account.
> - For an Apple account, it revokes its Sign in with Apple authorization.
>
> Your purchase records at RevenueCat are queued for deletion and removed within 30 days. Your cat remains on the device as a guest.

## support.md

Replace "Your cat" with:

> - Your cat is saved on your device. To keep a copy in the cloud, open **Settings → Account & cloud save** and sign in: with Google on Android, and with Apple or Google on iPhone.
> - After reinstalling or changing phones, sign in with the same account to restore your last cloud save. Progress played only as a guest cannot be recovered from another device.

## data-safety.md

**Data types.** No new types. The State C rows already cover sign-in and cloud saves.

**Deletion answer.** Change "in-app deletion returns with sign-in" to "in-app deletion (Settings → Account & cloud save → Delete cloud account) and the external request page".
