# Privacy Policy — QR Generator

Effective date: October 11, 2026

QR Generator (package name `com.qrgenerator.app`) is an offline-first utility app.

This policy explains what the app does with your data.

The short version: no accounts, no analytics, no ads. Your QR code contents are
generated on the device and are not automatically uploaded. However, when you
export, copy, or share a QR code image, you choose where that image goes, and it
may leave the app's private storage or be sent to another app.

This policy distinguishes between the current free beta build (purchases disabled)
and a future billing-enabled production build. The beta build makes no network
calls. A billing-enabled build contacts RevenueCat for subscription entitlement
state; see "Payments (premium)" below.
## What the app does not do

- No accounts and no user registration.
- No servers or backend services operated by the app.
- No analytics, crash reporters, tracking SDKs, or advertising SDKs. The app does
  not include any analytics, advertising, attribution, or crash-reporting SDK.
- No automatic transmission of your QR code contents, saved codes, history, input
  text, or images. QR content is generated on-device and is not sent anywhere
  unless you choose to export, copy, or share it.
- No collection of personal data such as your name, email address, phone number,
  advertising identifier, or location, in any build.

## Data collection in a billing-enabled build

When billing is enabled in a production build ( RevenueCat public SDK key configured,
BETA_BUILD not set), the app initializes the RevenueCat SDK. In that build only:

- RevenueCat generates and uses an anonymous app-user identifier so the service can
  track purchases and entitlement state. This is a pseudonymous identifier, not
  your name or email. Whether a pseudonymous identifier is "personal data" depends
  on the applicable law and on whether it can be linked back to a person; this
  policy does not treat it as anonymous for legal purposes.
- The app sends RevenueCat the purchase and entitlement information the SDK
  reports: purchase history, transaction status, subscription/entitlement state,
  and related purchase metadata that RevenueCat needs to manage subscriptions.
- Based on the current app code, the app does not set custom customer attributes
  (such as name or email), does not set advertising identifiers, and does not
  enable RevenueCat integrations or webhooks. These statements describe the app as
  written; they should be re-checked against the configured RevenueCat dashboard
  and the exact installed SDK version before any Google Play release, because
  dashboard-level integrations can send additional data.
- RevenueCat states that it encrypts data in transit and that, when used for
  in-app purchases, it collects purchase history and may process locale and
  currency code, but does not collect precise or approximate location. It also
  states that it acts as a data processor under its data processing agreement when
  handling end-user data. These are provider statements about RevenueCat's general
  practice; confirm the exact data handled by this app's configured setup before
  relying on them.

The app never sends your QR code contents, saved codes, Wi-Fi credentials,
app settings, or images to RevenueCat or to any other service in any build.

## Data stored in the app's private storage

The following is stored locally in the app's private storage and is removed if you
clear the app's data or uninstall the app:

- The text you type and the QR codes you generate.
- QR codes you save to your library and your generation history.
- App settings, such as your theme preference.
- A reference to any image you choose from your photos to place inside a QR code
  (see "Logo images" below).

## Wi-Fi credentials stored locally

Some QR codes include sensitive information by their nature. In particular, a Wi-Fi
QR code encodes the network name and password so that a phone scanning it can join
the network. When you save a Wi-Fi QR code to your library, or when a Wi-Fi QR code
appears in your history, the app stores that code locally in the app's private
storage, including the network password in the QR payload.

The app stores this data in local storage only. The app does not send Wi-Fi
credentials to anyone. This policy does not claim that the app separately encrypts
this local storage; that has not been verified. If device access is lost or the
device is compromised, stored Wi-Fi credentials could be exposed to anyone with
access to the device.

## Export, clipboard, and sharing

Your QR code contents are generated on-device and are not sent anywhere
automatically. However, you can take actions that place a QR code image outside the
app's private storage:

- **Save as PNG.** When you save a QR code as a PNG, the app asks you to choose a
  folder through the Android Storage Access Framework and writes the PNG into that
  folder (for example, a Downloads folder or a cloud-backed document provider). That
  PNG file is stored in the location you chose, not in the app's private storage.
  It may remain there after you clear the app's data or uninstall the app, and it
  may be accessible to other apps or to a cloud service that backs up that folder,
  depending on the location you chose and your device's backup settings.
- **Clipboard copy.** When you copy the QR code image, the app places the image on
  the system clipboard. Clipboard contents are handled by the operating system and
  may persist beyond the app session, and may be accessible to other apps with
  clipboard access.
- **Share sheet.** When you share the QR code image, the Android share sheet lets
  you send the image to another app (for example, a messaging app, email, or social
  app). The image then becomes data handled by that app, which may store it,
  forward it, or upload it according to that app's own behavior.

The app does not send QR code images to anyone on its own. Once you save, copy, or
share an image, however, the image is outside the app's direct control and may be
retained or transmitted by the destination app, folder, or cloud service you chose.

## Logo images

When you choose a photo from your library to use as a logo inside a QR code, the app
stores a reference (a content URI) to that image so it can display the logo in the
preview and include it in saved codes. The app does not make the original photo
app-owned, and it does not upload the photo to any server.

Clearing the app's data or uninstalling the app removes the app's reference to the
photo, but it does not remove the original photo from your device's photo library.

## Payments (premium)

Premium plans (auto-renewing monthly and yearly subscriptions and a lifetime
one-time purchase) are sold through Google Play. Google Play handles the
payment; the app never sees or stores your payment card or billing details.
Purchases are tied to your Google Play account and are restored through the
app's "Restore purchases" action.

Entitlement state (whether Premium is active on this device) is managed by
RevenueCat, a third-party subscription infrastructure service.

- In a billing-enabled production build (BETA_BUILD not set and a RevenueCat public
  SDK key configured), the app initializes the RevenueCat SDK. The SDK generates an
  anonymous app-user identifier and reports purchase and entitlement information to
  RevenueCat so the app can determine whether Premium is active. See "Data
  collection in a billing-enabled build" above for what that includes.
- In the current free beta build (BETA_BUILD=1), or in any build without a
  configured RevenueCat key, the app does not initialize the RevenueCat SDK, does
  not contact any store, and does not process any purchases. The app shows an honest
  notice and does not offer prices or purchase buttons.

The app never sends your QR code contents, saved codes, Wi-Fi credentials,
app settings, or images to RevenueCat or to any other service in any build.

## Children

The app is a general-audience utility. It does not request account information and
does not knowingly collect personal data from anyone, including children. In a
billing-enabled build, purchases are handled by Google Play and RevenueCat; those
services have their own terms and privacy practices that may apply to purchase
activity.

## Legal disclaimers

This policy describes the app as written and as configured in the current
repository. It is not legal advice and does not certify compliance with any
specific law. The exact data handled by a billing-enabled build depends on the
installed SDK version and the configured RevenueCat dashboard, which should be
re-checked before any Google Play release.

## Changes

If this policy changes, the updated version will be published with the app listing
on Google Play (if the app is ever published there) and on the app's GitHub
repository.

## Contact

Questions about this policy: qrgenerator.support@proton.me
