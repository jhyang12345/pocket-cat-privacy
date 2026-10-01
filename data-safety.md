# Google Play Data Safety draft for Pocket Cat

Prepared **2026-10-01** for `com.pocketcat.galchi`, for the upcoming Google sign-in and Firebase cloud-save release. **These new answers have not been submitted to Play Console.** The previous purchase-only answers were submitted on 2026-09-25; that historical version remains in Git history.

The app offers guest gameplay, optional Google account linking and cloud saving, and Google Play gem purchases verified by RevenueCat. New purchases require a protected cloud account. Photo Mode pictures remain local. The release owner must review this draft against the final SDK versions, provider configuration and release build before submission.

## Overall form answers

| Question | Draft answer |
|---|---|
| Does the app collect or share required user data types? | **Yes** |
| Is collected user data encrypted in transit? | **Yes**, for app/SDK network traffic using HTTPS. Review support-email handling separately; email is an external request channel. |
| Account creation methods | **Other: Google sign-in / federated sign-in**. No Pocket Cat password is created. |
| Can users request deletion of an account and its associated data? | **Yes**, in-app cloud-account deletion and the external email request page. Complete the processor-deletion release review below. |
| Can users request data deletion without deleting an account? | **Yes**, via the support email request; do not describe this as an automatic in-app feature. |
| Account/data deletion URL | `https://jhyang12345.github.io/pocket-cat-privacy/delete-account/` — publish and verify before submitting. |
| Ads / independent security review | No ads; no independent security-review claim. |
| Target audience / Families Policy | 13 and over; not a Families app. |

“Not shared” below relies on Play's service-provider exception: Firebase and RevenueCat process information for Pocket Cat. Recheck any RevenueCat integrations, exports or independently operating third parties before using this answer.

## Data types and purposes

| Play data type | Collection in this implementation | Required or optional | Ephemeral | Draft purposes |
|---|---|---|---|---|
| Personal info: **Email address** | Google sign-in email in Firebase Authentication; support email when a user contacts us | Optional account/support features | No | App functionality, account management, fraud prevention/security |
| Personal info: **User IDs** | Firebase UID and Google provider identifier; UID used as RevenueCat app-user ID after linking | Optional account features; SDK anonymous identifiers require review below | No | App functionality, account management, fraud prevention/security |
| Personal info: **Name** | Google display name may be populated in Firebase Authentication, even though game UI uses email | Optional account feature | No | App functionality, account management |
| Financial info: **Purchase history** | Google Play transaction/product/purchase-token information in RevenueCat; purchase-credit ledger in cloud save | RevenueCat recommends **required** for an integrated purchase SDK; cloud ledger is optional cloud saving | No | App functionality, Analytics (provider purchase reporting), fraud prevention/security |
| App activity: **Other user-generated content** | Player-entered cat name in cloud save | Optional cloud saving | No | App functionality |
| App activity: **Other actions** | Bond/progress, earned/spent gems, treats, cosmetics and game settings in cloud save | Optional cloud saving | No | App functionality |
| Device or other IDs | Random installation writer ID in Firestore; review SDK identifiers generated at startup | Cloud writer ID optional; mark required if any declared SDK identifier is collected without a user choice | No | App functionality, fraud prevention/security |

Draft **Collected: Yes, Shared: No** for these rows, subject to the service-provider exception above. Data stored only on the device is not developer collection under Play's definition.

The Google account profile-picture URL may be populated by Firebase Authentication. Inspect a real test account and its provider data before submission and include the applicable profile-image disclosure if it is received/stored. “Photo Mode album is local” does not cover a Google profile image supplied during sign-in.

**Approximate location requires provider review:** RevenueCat's Data Safety guide says it does not collect location, while its Customer Profile documentation says it derives country from the last-seen IP if transaction country is unavailable. Country derived from an IP is different from simply handling an IP for security. Resolve this against the actual SDK/provider behavior before submission; if inferred country is stored for Pocket Cat users, conservatively disclose approximate location, its collection choice and its reporting/security purposes. The privacy policy includes country-level provider information.

The game does not collect payment-card/bank details, precise location, contacts, messages, audio, health data or browsing history. It does not upload Photo Mode pictures or exported files. No advertising ID, gameplay analytics, Crashlytics or Performance Monitoring integration is added by this feature. Firebase SDK app/device user-agent information and IPs used for security must still be reviewed using Firebase's current disclosure guide; absence of a crash-reporting SDK is not a blanket claim that SDKs process no diagnostics or metadata. Do not declare approximate location merely because a service sees an IP address unless it is used to derive location.

## Retention and deletion review before release

- Publish the revised privacy policy and `/delete-account/` page, then check both public URLs without being signed into GitHub. The page identifies Pocket Cat and gives an outside-app request path through the existing support address.
- Verify the exact in-app path: **Settings → Account & cloud save → Delete cloud account**. Test with the final signed release configuration: fresh Google confirmation, Firestore save removed, Authentication account deleted, and a clear failure state when either step cannot finish. Local guest data remains, as the UI and policy disclose.
- The current native button does **not** delete a RevenueCat customer. Before release, document and test how associated RevenueCat customer records and aliases are deleted when an account deletion is requested. Do not claim that logging out of RevenueCat deletes data. Play requires deletion of associated processor-held data, subject to properly disclosed legitimate retention; an email route alone does not prove that the in-app operation satisfies this requirement.
- For a support request, verify ownership before deletion. Locate the Firebase UID from the linked email while it still exists, identify the RevenueCat customer/aliases and any older anonymous purchase identity, remove the matching Firestore save and Authentication user, and delete/request deletion of associated RevenueCat records. Confirm what was removed and explain any records that remain. Do not put service credentials in the app or use an unauthenticated public delete endpoint.
- A Firebase account delete does not delete Firestore documents automatically; the implementation explicitly removes `/players/{uid}/saves/current`. Confirm that no other account-linked collections or storage objects have been added.
- Firebase Authentication's documented provider retention includes a few weeks for logged IPs and up to 180 days after deletion for other authentication information. Do not promise immediate provider-backup erasure. Android system backups, exported photos and Google Play payment records have separate controls.
- RevenueCat is configured at process startup, including guest gameplay. Inspect actual automatically collected SDK identifiers and metadata before marking those types optional. Cloud-save opt-in does not make unrelated SDK collection optional.
- Match the public privacy policy, Play form answers and actual release behavior. Keep the previous form answers until the corresponding new behavior and public documents are ready, then submit the updated answers with the release.

## Official reference material

- [Google Play account deletion requirements](https://support.google.com/googleplay/android-developer/answer/13327111?hl=en): apps with account creation need both an in-app deletion path and an accessible outside-app resource. An email support route is allowed. Account deletion includes associated user data and processor-held data, with disclosed exceptions for legitimate retention.
- [Google Play Data Safety definitions](https://support.google.com/googleplay/android-developer/answer/10787469?hl=en): collection includes SDK transfers off the device, and service-provider processing has a sharing exception. Optional collection requires a real user choice.
- [Firebase Android SDK disclosure guide](https://firebase.google.com/docs/android/play-data-disclosure): check Authentication and Firestore sections plus the actual app payload; the developer is responsible for the final answers.
- [Firebase privacy, retention and processing locations](https://firebase.google.com/support/privacy).
- [Firebase Authentication user profiles](https://firebase.google.com/docs/auth/users): basic profile information can include UID, email, display name and photo URL.
- [RevenueCat Google Play Data Safety guidance](https://www.revenuecat.com/docs/platform-resources/google-platform-resources/google-plays-data-safety): purchase history is required, not ephemeral, with App functionality and Analytics purposes; identifiers depend on integrations/configuration.
- [RevenueCat Customer Profile](https://www.revenuecat.com/docs/dashboard-and-metrics/customer-profile): customer information, IP-derived country and dashboard deletion. Restrict deletion access to operators.

## Store listing document URLs

- Privacy policy: `https://jhyang12345.github.io/pocket-cat-privacy/`
- Account and data deletion: `https://jhyang12345.github.io/pocket-cat-privacy/delete-account/`
