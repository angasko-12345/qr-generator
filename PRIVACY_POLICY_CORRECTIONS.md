# Privacy Policy Document Corrections - Implementation Summary

**Date:** October 11, 2026  
**Repository:** https://github.com/angasko-12345/qr-generator  
**Status:** Ready for review (not committed)

## Files Modified

1. `PRIVACY_POLICY.md` - Complete update of privacy policy
2. `docs/privacy.html` - Synced with PRIVACY_POLICY.md  
3. `README.md` - Updated Privacy section and Google Play data safety section

---

## Corrected Claims with Citations

### 1. Separation of Beta vs Billing-Enabled Builds

**Previous claim:** "The short version: No accounts, no analytics, no ads. Your QR content never leaves your device."

**Correction:** Now explicitly distinguishes between:
- Beta build (BETA_BUILD=1): no network calls, RevenueCat SDK not initialized
- Billing-enabled production build: RevenueCat SDK initialized, processes purchase/entitlement data

**Citation:** 
- PRIVACY_POLICY.md lines 8-16 (intro paragraph)
- README.md lines 61-72 (Beta vs billing-enabled builds section)

**Code reference:** 
- `src/premium/beta.ts` - `isBetaBuildEnabled()` function
- `src/billing/index.ts` - `createBillingProvider()` factory

---

### 2. RevenueCat Data Collection Description

**Previous claim:** "No collection of personal data (billing exposes only an anonymous app identifier and purchase/entitlement state, described below)"

**Correction:** Now accurately describes:
- RevenueCat generates pseudonymous app-user identifier (not anonymous for legal purposes)
- SDK reports purchase history, transaction status, subscription/entitlement state, related metadata
- App does not set custom customer attributes, advertising identifiers, or enable integrations/webhooks (based on current code)
- RevenueCat states it encrypts in transit, collects purchase history, may process locale/currency, does not collect location
- RevenueCat acts as data processor under DPA

**Citation:**
- PRIVACY_POLICY.md lines 24-52 (Data collection in a billing-enabled build section)
- docs/privacy.html lines 79-117 (billing-data section)

**Documentation references:**
- RevenueCat Google Play Data Safety page: https://www.revenuecat.com/docs/platform-resources/google-platform-resources/google-plays-data-safety
- RevenueCat Customers/User-IDs: https://www.revenuecat.com/docs/customers/user-ids
- RevenueCat Customer Attributes: https://www.revenuecat.com/docs/customers/customer-attributes
- RevenueCat Security & Compliance: https://www.revenuecat.com/security-and-compliance

---

### 3. Export, Clipboard, and Sharing Behavior

**Previous claim:** "The Android share sheet, clipboard copy, and the 'save as PNG' folder picker are triggered only by your own taps and operate on-device or through Android system components."

**Correction:** Now explains that these actions can place QR images outside app's private storage:
- **Save as PNG:** Uses Storage Access Framework, file stored in user-chosen folder (may persist after uninstall, may be cloud-synced)
- **Clipboard copy:** Image placed on system clipboard, may persist beyond app session
- **Share sheet:** Image sent to destination app, which may store/forward/upload it

**Citation:**
- PRIVACY_POLICY.md lines 100-144 (Export, clipboard, and sharing section)
- docs/privacy.html lines 157-193 (export-sharing section)
- README.md lines 97-115 (Export, clipboard, and sharing section)

**Code reference:**
- `src/util/qrExport.ts` - `saveQrPng()`, `shareQrPng()`, `copyQrPng()` functions
- `expo-file-system` StorageAccessFramework API
- `expo-clipboard` Clipboard API
- `expo-sharing` Sharing API

---

### 4. PNG Files and Post-Uninstall Behavior

**Previous claim:** "Nothing in this list leaves your device."

**Correction:** Now clarifies that PNG files saved via Storage Access Framework:
- Are stored in user-chosen location, not app-private storage
- May remain after clearing app data or uninstalling
- May be accessible to other apps or cloud services depending on folder chosen and device backup settings

**Citation:**
- PRIVACY_POLICY.md lines 107-114 (Save as PNG bullet)
- docs/privacy.html lines 163-170
- README.md lines 102-106

---

### 5. Logo Images and Photo References

**Previous claim:** "Any image you choose from your photos to place inside a QR code" (listed as removed on uninstall)

**Correction:** Now clarifies:
- App stores a reference (content URI) to the photo, not the photo itself
- App does not make the original photo app-owned
- App does not upload the photo to any server
- Clearing app data or uninstalling removes the app's reference, not the original photo from device's photo library

**Citation:**
- PRIVACY_POLICY.md lines 146-159 (Logo images section)
- docs/privacy.html lines 195-207 (logo-images section)
- README.md lines 117-123

**Code reference:**
- `src/sheets/CustomizeSheet.tsx` - `pickLogo()` function using `expo-image-picker`
- `src/data/storage.ts` - SavedCode stores `appearance.logoUri`

---

### 6. Wi-Fi Credentials Storage

**Previous claim:** Implied Wi-Fi credentials are removed on uninstall (listed under "Data that stays on your device")

**Correction:** Now explicitly states:
- Wi-Fi QR codes encode network name and password in plaintext (by nature of Wi-Fi QR codes)
- When saved to library or appearing in history, app stores code locally including password in QR payload
- App does not send Wi-Fi credentials to anyone
- Policy does not claim the app separately encrypts local storage (that has not been verified)
- Stored credentials could be exposed if device is compromised

**Citation:**
- PRIVACY_POLICY.md lines 82-98 (Wi-Fi credentials stored locally section)
- docs/privacy.html lines 133-149
- README.md lines 87-94

**Code reference:**
- `src/qr/content.ts` - `buildWifiPayload()` encodes password in plaintext
- `src/data/storage.ts` - SavedCode and HistoryEntry store draft with Wi-Fi fields
- `src/types.ts` - WifiFields interface includes password field

---

### 7. "No Analytics/Advertising/Crash Reporting SDK" Claims

**Previous claim:** "No analytics, crash reporters, tracking SDKs, or advertising SDKs"

**Status:** **PRESERVED** - Verified accurate

**Verification:**
- `package.json` contains no analytics, advertising, attribution, or crash-reporting dependencies
- `package-lock.json` confirms no such transitive dependencies
- Source code review confirms no such SDKs are imported or initialized
- `react-native-purchases` is the only third-party SDK capable of network transmission

**Citation:**
- PRIVACY_POLICY.md line 20 (no analytics claim preserved)
- docs/privacy.html line 72
- README.md lines 59-60

---

### 8. Support Email and Document Synchronization

**Status:** **PRESERVED AND SYNCHRONIZED**

**Verification:**
- Support email `qrgenerator.support@proton.me` present in all three documents
- PRIVACY_POLICY.md and docs/privacy.html contain identical section structure
- README.md Privacy section now matches PRIVACY_POLICY.md terminology and structure
- Google Play data safety section in README.md now consistent with PRIVACY_POLICY.md billing section

**Citation:**
- PRIVACY_POLICY.md line 201 (Contact section)
- docs/privacy.html line 239
- README.md line 248 (Privacy policy link)

---

### 9. Legal Disclaimers Added

**New content:** Added explicit legal disclaimers stating:
- Policy describes app as written and configured in current repository
- Not legal advice
- Does not certify compliance with any specific law
- Exact data handled by billing-enabled build depends on installed SDK version and configured RevenueCat dashboard
- Should be re-checked before any Google Play release

**Citation:**
- PRIVACY_POLICY.md lines 189-198 (Legal disclaimers section)
- docs/privacy.html lines 231-238 (legal-disclaimers section)

---

### 10. Changes Section Updated

**Previous claim:** "If this policy changes, the updated version will be published with the app listing on Google Play."

**Correction:** Now states policy will be published with app listing on Google Play (if ever published there) and on the app's GitHub repository.

**Citation:**
- PRIVACY_POLICY.md lines 200-204 (Changes section)
- docs/privacy.html lines 240-245

---

## Items Requiring Runtime Verification

The following items cannot be verified from code alone and require runtime testing, dashboard access, or qualified legal review:

1. **Exact RevenueCat SDK behavior:** The exact data transmitted by the installed SDK version in a billing-enabled build requires runtime network inspection or SDK documentation verification.

2. **RevenueCat dashboard configuration:** Dashboard-level integrations, webhooks, or attributes could transmit additional data not visible in app code.

3. **Google Play Data safety form accuracy:** The form must be completed based on actual configured build behavior, not code review alone.

4. **PNG file persistence testing:** Actual behavior of PNG files after uninstall depends on device, Android version, folder location, and backup settings.

5. **Clipboard persistence:** Clipboard behavior varies by Android version and device manufacturer.

6. **Legal jurisdiction applicability:** Whether Philippine DPA, GDPR, UK GDPR, or CCPA/CPRA apply requires legal analysis of operator location, target markets, user volume, and revenue.

7. **Classification of pseudonymous identifiers:** Whether the anonymous app-user ID constitutes "personal data" under applicable law requires legal analysis.

8. **Data processor agreement:** Whether RevenueCat DPA is in place and adequacy of cross-border transfer safeguards requires dashboard/account verification.

---

## What Was NOT Changed

- No application code modified
- No dependencies added or removed
- No billing configuration changed
- No SDK versions updated
- No publishing performed
- Beta build behavior unchanged
- All accurate claims preserved (no analytics/ad SDKs, no automatic QR content transmission, etc.)

---

## Validation Performed

1. **Section structure consistency:** All three documents contain compatible section coverage
2. **Key claim consistency:** "no analytics", "RevenueCat", "Storage Access Framework", "support@proton.me" appear consistently
3. **Corrected claim presence:** "pseudonymous", "does not claim encryption", "cloud-backed", "does not make original photo app-owned", "re-check" all present in appropriate documents
4. **Code citation accuracy:** All code references verified against actual source files in repository

---

*Report generated as part of QR Generator Privacy, Data Safety & Legal Compliance Audit implementation.*
