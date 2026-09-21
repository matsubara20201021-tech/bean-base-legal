# BeanBase Privacy Policy

Last updated: September 21, 2026
Effective date: September 21, 2026

## 1. Scope

This Privacy Policy (the "Policy") applies to the Android app "BeanBase" (the "App") distributed on Google Play by yuzumaruca (the "Developer").

The App lets you log coffee brews, keep master data about your equipment, record how each cup tasted, and analyse those records. This Policy explains what information is handled when you use the App, where it is stored, what is sent outside your device, and what choices you have.

## 2. Core principles

- The brew records, equipment master data and analysis results you enter, and the photos you add, are **stored only on your device**. They are not automatically sent to the Developer's servers, a Google Sheets spreadsheet or anywhere else.
- App settings such as theme and language, and the brewing articles you write yourself, are also stored on your device.
- Information leaves your device only when you **use the AI feature, sign in, purchase a subscription, use cloud backup (Pro plan), are shown an ad, or when usage and error reports are sent (you can turn this off in the settings; Sections 3 and 15)**.
- **Cloud backup sends and stores the photos you added (images of beans, equipment and shops) as well as your brew records and master data** (Section 8).
- The free manual export and import (Section 15) write your data, including photos, to a file on your device. This export does not go through any server.
- The Developer does not use your records or photos for ad targeting and does not sell them to third parties.

## 3. Information the App handles and where it is stored

The categories of information the App handles, and where each is stored, are as follows.

| Category | Examples | Where it is stored |
|---|---|---|
| Brew records | Brew date and time; the bean, grinder, dripper, filter and brewing method used; dose; grind setting; water temperature; water volume; bloom water; bloom time; total brew time; taste and strength notes; scores for aroma, acidity, bitterness, sweetness, complexity, flavour and overall; free-text comments | A database (SQLite) on your device |
| Master data | Beans, grinders, drippers, filters, brewing methods (including pour steps), origins, shops, and bean purchase history | A database (SQLite) on your device |
| Photos | Photos of beans, equipment and shops. The image data is stored in the App's private area on the device, and the database records a string pointing to where it is stored | Your device (also stored in the cloud if you use cloud backup, as described in Section 8) |
| Analysis results | Snapshots of analyses computed on the device, and the history of recipe suggestions | A database (SQLite) on your device |
| Brewing articles | Articles you write or edit yourself | A database (SQLite) on your device |
| App settings | Theme, accent colour, language, onboarding status, the reference-data setting, the automatic backup setting, and state such as the time of the last successful backup | A settings area on your device |
| Usage statistics | Screen IDs, types of actions, counts and durations in seconds (text you enter is not included; Section 12) | Firebase Analytics (Google) |
| Error and crash records | Exception type, where it occurred, device model and OS version (text you enter is not included; Section 12; in regions where consent is required, nothing is sent until consent has been obtained) | Firebase Crashlytics (Google) |

- Usage statistics and error and crash records are sent to the Developer to improve the App (analysing usage and fixing defects). Sending them is optional, and you can turn it off at any time under "Privacy" on the settings screen (Section 15).
- Apart from usage statistics and error and crash records, the information above is not kept anywhere outside your device unless you run the cloud backup described in Section 8. No information identifying you, such as a name or an email address, is attached to a record.
- You are not asked to sign in with a Google account to store records, master data, analysis results or photos (the cases where signing in is required are described in Section 6).
- Uninstalling the App deletes the information stored on your device (records, master data, analysis results, photos, articles and settings). If you use cloud backup, described in Section 8, the copy in the cloud remains (if you want it deleted, please contact us using the details in Section 19). Files you exported as described in Section 15 also remain under your own control.
- Information stored on your device (records, master data, analysis results, photos, articles and settings) may be backed up automatically to your own Google account by the operating system's standard backup feature (Android), depending on your device settings. How that backup is handled is governed by Google's policies, and the operator of the App does not access the contents of that backup.

## 4. Overview of information sent outside the device

| What triggers the transfer | What is sent | Where it goes |
|---|---|---|
| Creating, updating or deleting a brew record, master entry, analysis result or photo, and opening list, detail or analysis screens | (Nothing is sent. Everything is processed on the device.) | (Not applicable) |
| Running the AI feature (reading bean details from a photo) | The photo you selected and the instruction text for the AI | Google's Gemini API, through the Developer's relay server (Google Cloud, Tokyo region) |
| Using the AI feature for the first time, and watching an ad to earn free uses | The anonymous account identifier, the app version, the originating IP address, and Google Play's verdict on the integrity of the app and device | The Developer's relay server; Google Play (Play Integrity) |
| Signing in with Google (only for purchase and purchase restore) | Google account credentials (ID token) | Firebase Authentication (Google) |
| Purchasing, renewing or cancelling the Pro plan | The purchase token and product ID | Google Play, through the Developer's relay server |
| Running a cloud backup (Pro plan) | The data exported from the on-device database (brew records, master data and so on) and the photos you added (resized before sending; see Section 8) | The Developer's Google Cloud Storage (Tokyo region, through the Developer's relay server) |
| Running the free manual export (Section 15) | (Nothing is sent. The data is written as a file to a location on your device that you choose.) | (Not applicable) |
| Displaying an ad | Information the ad SDK collects about the device (subject to your consent) | Google (AdMob) |
| From time to time while the App is open and in use (can be turned off in the settings) | Usage statistics (screen IDs, types of actions, counts, durations in seconds) and error and crash records (exception type, where it occurred, device model, OS version) | Google (Firebase Analytics and Firebase Crashlytics) |

## 5. Information sent when you use the AI feature

The App's AI feature runs only when you tap "Read bean details from a photo" on the bean entry screen.

- **What is sent**: one photo you choose (resized so its longer edge is at most 1024 pixels before sending) and the instruction text used to read the bean details.
- **How it is sent**: the App does not call Google's Gemini API directly. The call goes through a relay server operated by the Developer (Google Cloud Run, Tokyo region `asia-northeast1`), which then calls the Gemini API.
- **How the photo is handled**: a photo sent for the AI feature is not stored on the relay server (this is a separate path from the photos included in cloud backup; see Section 8). The text the AI returns is **kept on the relay server for up to 24 hours** so that a retry after a dropped connection does not consume a second use, and is deleted automatically after that. Neither the instruction text nor the photo is written to server logs.
- **Google's handling**: information sent to the Gemini API is handled according to Google's policies and terms.
- Your brew records, scores, comments and master data are not included in the input to the AI feature.

If you never use the AI feature, nothing is sent through this path.

## 6. Accounts and sign-in

- The App **works without signing in** from the moment you install it. Logging, master data and analysis require no account.
- **The first time you use the AI feature**, an anonymous Firebase Authentication account is created so that your remaining uses can be counted. What is created is a random identifier (uid) that does not by itself identify you. You are not asked for a name or an email address.
- **Signing in with Google is required only to purchase the Pro plan or restore a purchase.** You are never asked to sign in with Google for free use. When you sign in, Firebase Authentication records identifying information for that Google account (such as the email address). The relay server stores only the identifier (uid) and the sign-in method; the App does not display your email address or link it to your records.
- If you sign in with Google while an anonymous account already holds your usage counters, the same identifier is kept wherever possible. If the Google account is already associated with a different identifier, you are signed in with that identifier instead and any remaining uses on the anonymous account are not carried over.

## 7. Information stored on the server to manage usage limits and prevent abuse

To count free uses (granted by watching an ad) and Pro plan uses correctly, and to prevent automated abuse, the following is stored in Firestore on the relay server's project (Google Cloud, Osaka region `asia-northeast2`).

| Stored information | Contents |
|---|---|
| Account information | Identifier (uid), sign-in method, creation time, last access time, Pro plan status |
| Usage counters | Period type (free daily / Pro monthly), period ID, limit, number granted, number used |
| Records of grants from watching ads | The single-use identifier issued by the server, the times of issue and grant, its state, a hash of the originating IP address at issue, and the transaction ID, ad unit and reward information reported by the ad network |
| Records of AI runs | Request ID, feature name, period, state, model used, and the text of the AI response |
| Purchase records | Purchase token, product ID, purchase state, expiry time, order ID |
| Per-IP aggregates | Date, hash of the originating IP address, and the number of issues, grants and identifiers seen that day |

- Originating IP addresses are not stored as-is. Only part of a hashed value is stored.
- Retention periods are set out in Section 14.
- When you watch an ad to earn free uses, Google Play's Play Integrity API checks that the app was installed from the official Google Play and that the device has not been tampered with. Google performs this check and the relay server receives the verdict.
- Completion of ad viewing is reported by Google (AdMob) directly to the relay server. Your identifier (uid) is not included in that report; only the single-use identifier issued by the server is used.

## 8. Cloud backup (Pro plan)

Pro plan subscribers can keep a copy of their records in the cloud.

- **What is stored**: the data exported from the on-device database (the tables for brew records, master data, purchase history, analysis results, recipe suggestions and brewing articles) and, in addition, **the photos you added themselves** (images of beans, equipment and shops). The scope is the same as the export feature described in Section 15.
- **Resizing of photos**: photos are resized before they are sent. A photo whose longer edge exceeds 1024 pixels, or whose file size exceeds about 1.5 MB, is reduced to a longer edge of at most 1024 pixels and converted to JPEG before sending. Photos that are already small are sent as they are. A large photo is never sent at its original size. The original photo on your device is not modified.
- **What is stored alongside it**: information describing the state of the backup (the number of records, the file size, the data format version and the time it was stored) and a list of which photos are referenced by your records are kept as metadata on the stored files. There is a mechanism for attaching a device name, but the current version does not send one.
- **Where it is stored**: a Google Cloud Storage bucket controlled by the Developer (Tokyo region `asia-northeast1`). The record data is stored, compressed, as a single file per user, and each photo is stored as a separate file. The bucket is configured so that it is not publicly accessible, and only the Developer's relay server has permission to reach it.
- **How stored data is used**: only your own records and photos are stored, and they are used only for backup and restore. They are not provided to third parties and are not used for advertising.
- **When it runs**: if automatic backup is on, it runs when you open the App if at least six hours have passed since the last successful backup (that is, while you are using the App, data may be sent automatically every six hours). You can also run it at any time from the screen. Automatic backup can be turned off in the settings.
- **Photos and Wi-Fi**: by default, automatic backup **sends photos only while you are connected to Wi-Fi (or Ethernet)**. On mobile data, only the record data is sent, and the photos are sent the next time you are on Wi-Fi. You can change this at any time with the "Upload photos on Wi-Fi only" switch. A manual backup or restore that you start from the screen runs regardless of the type of connection.
- **Versions kept and automatic deletion of photos**: only the latest version of the record data is kept, and a version that has been overwritten is retained for 30 days and then deleted. A photo that is no longer referenced by any record is **deleted automatically after about 30 days** (after deletion it may be kept in Cloud Storage for a further 30 days in case it needs to be recovered).
- **Restoring**: a restore happens only when you ask for it. Nothing is imported automatically. Photos are also downloaded from the cloud to your device when you restore.
- **After cancellation**: you can still download (restore) the data you stored, including photos, after cancelling the Pro plan. Uploading a new backup is limited to Pro plan subscribers.
- **Deletion**: the current version has no in-app way to delete the backup held in the cloud (photos included). If you want it deleted, please contact us using the details in Section 19.

## 9. Advertising

- In free use, a banner ad is shown on list screens, and rewarded ads (watch to earn AI uses) are offered to obtain free AI uses. Banner ads are not shown on the Pro plan.
- Ads are delivered by Google AdMob. The ad SDK may collect information about your device and about ads (which may include the advertising ID) in order to deliver ads, measure impressions and prevent fraud. What is collected and how Google handles it is governed by Google's privacy policy and AdMob's policies.
- In regions where consent is required, such as the European Economic Area and the United Kingdom, a consent form provided by Google's UMP (User Messaging Platform) is shown at startup. If consent has not been obtained, the ad SDK is not initialised. Your consent choice is also applied to usage measurement (Google Analytics) and to the collection of error and crash information (Firebase Crashlytics).
- Usage measurement (Firebase Analytics) does not collect the advertising ID and does not use it to personalise ads. The party that may obtain the advertising ID is the ad SDK (AdMob), which is handled as described above.
- The Developer does not use the brew records, scores or photos you enter for ad targeting, and does not pass them to the ad SDK.

## 10. Purchases (Google Play)

- The Pro plan is purchased as a Google Play subscription. Payment details such as credit card numbers are handled by Google Play; **neither the Developer nor the App receives them**.
- When a purchase completes, the App sends the purchase token and product ID to the relay server. The relay server confirms the purchase through the Google Play Developer API and enables the Pro plan only if the purchase is valid.
- Changes to a purchase (renewal, cancellation, refund and so on) are notified by Google Play to the relay server, which queries Google Play again for the current state before applying it.
- Retention of purchase records is set out in Section 14.

## 11. Reference records from the Developer, bundled with the App

The App ships with reference data built from the Developer's own past brew records, used to help produce recipe suggestions.

- This reference data is a file inside the App; **no network communication takes place** when it is used.
- This feature **never sends any additional records anywhere**. The App only reads the bundled reference data.
- The feature is on by default. You can turn it off at any time in the settings.
- The reference data is used only for recipe suggestions. It is not counted in your record totals or history, and it is not included in cloud backups.

## 12. Information we do not collect

The App does not collect the following.

- Name, address, telephone number or date of birth
- Location, contacts, call history, SMS, or the list of other apps on your device
- Text you enter (bean names, shop names, notes, comments, and the titles and bodies of brewing articles) recorded in the usage statistics or the error and crash records (Section 3). These contain only fixed identifiers defined by the App and numbers, such as screen IDs, types of actions, counts and durations in seconds. The account identifier (uid), email address, display name, photos and location are not included either.
- Device tokens for sending notifications. The App does not send push notifications.

The list above covers information the Developer does not collect as a function of the App. Information the ad SDK collects in order to deliver ads (which may include the advertising ID) is separate from this and is handled as described in Section 9.

Camera and photo access is used only when you take or select a photo. Photos are handled as described in Sections 3, 5 and 8.

## 13. Sharing with third parties and use of service providers

- The Developer does not sell your information to third parties.
- The following services are used to operate the App. They act as providers or processors handling information within the purposes set by the Developer.
  - Google Cloud (Cloud Run, Firestore, Cloud Storage, Cloud Logging): running the relay server, managing usage counters, storing cloud backups (records, master data and photos), recording operational logs
  - Firebase Authentication (Google): identifying accounts
  - Google Gemini API: running the AI feature
  - Google Play (billing, Play Integrity, real-time developer notifications): verifying purchases and checking app integrity
  - Google AdMob and UMP: delivering ads and managing consent
  - Firebase Analytics and Firebase Crashlytics (Google): aggregating usage statistics and collecting error and crash records (to improve the App)
- Information may be disclosed to the extent necessary when disclosure is required by law, or when it is needed to protect someone's life, body or property and obtaining consent is difficult.

## 14. Where information is stored and for how long

| Information | Location | Retention |
|---|---|---|
| Information stored on the device (brew records, master data, analysis results, photo image data, brewing articles, app settings) | Your device | Until you uninstall the App (records and photos you delete are removed from the device at that point) |
| Account information (identifier, sign-in method, Pro status) | Firestore (Osaka region) | Until you ask us to delete it |
| Usage counters (free, daily) | Firestore | 35 days from creation |
| Usage counters (Pro, monthly) | Firestore | 400 days from creation |
| Records of AI runs (including response text) | Firestore | 24 hours |
| Single-use identifiers for ad-based grants | Firestore | 24 hours from issue |
| Records of completed ad views | Firestore | 90 days |
| Purchase records | Firestore | 400 days |
| Notifications received from Google Play | Firestore | 30 days |
| Daily aggregates based on hashed IP addresses | Firestore | 7 days |
| Cloud backup (record data, latest version) | Cloud Storage (Tokyo region) | Until you ask us to delete it |
| Cloud backup (record data, overwritten versions) | Cloud Storage | 30 days |
| Cloud backup (photos referenced by your records) | Cloud Storage (Tokyo region) | Until you ask us to delete it |
| Cloud backup (photos no longer referenced by any record) | Cloud Storage | Deleted automatically about 30 days after they stop being referenced; after deletion they may be kept for a further 30 days in case they need to be recovered |
| Server access logs (identifier, feature name, latency, result) | Cloud Logging | According to the Google Cloud retention settings |
| Usage statistics (Firebase Analytics) | Google data centres (including in the United States; the region cannot be chosen, and it is separate from the Firestore Osaka region above and from Cloud Storage and Cloud Run in the Tokyo region) | Event data is retained for 14 months |
| Error and crash records (Firebase Crashlytics) | Same as above (Google data centres, including in the United States) | According to Google's default retention period |

The relay server runs on Google Cloud Run, and the request logs Cloud Run records automatically contain the originating IP address in addition to the items the Developer logs explicitly above. Those request logs are retained according to the Google Cloud retention settings.

## 15. Your choices and rights

- **Export**: from "Data" in the settings screen you can export your records to a file on your device. "Export data (includes photos)" packs your records and photos into a single ZIP file (photos are resized in the same way as in Section 8). "Export as CSV" writes only the tabular record data and does not include photos. Exporting is completed on the device and does not go through any server. Exported files are then under your own control.
- **Import**: you can bring records back in from a file you exported (a ZIP file, or a JSON file in the earlier format). Photos contained in a ZIP file are also brought onto your device.
- **Deleting data on the device**: the records, master data, analysis results, photo image data, brewing articles and app settings stored on your device are deleted when you uninstall the App. You can also delete individual records and master entries from the screens.
- **Deleting a cloud backup**: as noted in Section 8, the current version has no in-app deletion (this includes photos). Please contact us using the details in Section 19.
- **Deleting your account and server-side information**: please contact us using the details in Section 19. After confirming your identity, we will delete the information linked to your identifier and your cloud backup (including photos).
- **Access, correction and suspension of use**: requests are accepted at the contact point in Section 19.
- **Changing usage and error reporting**: you can turn "Share usage and error reports" off (and back on) at any time under "Privacy" on the settings screen. It is on by default. Turning it off stops the sending of usage statistics and error and crash records. In regions where consent is required, sending also follows your consent status described in Section 9 in addition to this switch, and nothing is sent while consent has not been obtained.
- **Changing advertising consent**: in regions where consent is required, the consent form is shown at startup. You can reopen the form and change your choice at any time from "Ad consent settings" under "Privacy" on the settings screen (shown only in regions where consent is required). You can also limit personalisation through your device's advertising ID settings.

## 16. Children

The App is not designed for children. If you are under 13, please do not use the App. If we learn that we have unintentionally obtained information from someone under 13, we will delete it promptly.

## 17. Security

- All communication between the App and the relay server is encrypted with HTTPS.
- Information stored in Google Cloud Storage and Firestore is encrypted at rest by Google Cloud's standard mechanisms. The cloud backup (photos included) bucket is configured so that it is not publicly accessible, and access is limited to the relay server's service account.
- The API key used for the AI feature is kept as a secret on the relay server and is not included in the App.
- Server logs do not record instruction text, AI response text, photos, or complete authentication or purchase tokens.

## 18. Changes to this Policy

This Policy may be revised in response to changes in law or to new features in the App. When it is revised, the updated text and the last updated date are published on this page. For significant changes, we will give notice in the App or in the store's release notes.

## 19. Contact

For questions about this Policy or about how personal information is handled, please contact:

- Provider: yuzumaruca
- Contact: matsubara20201021@gmail.com

## 20. Governing law

This Policy is governed by the laws of Japan, and any dispute relating to it shall be subject to the exclusive jurisdiction of the district court having jurisdiction over the Developer's place of residence as the court of first instance.
