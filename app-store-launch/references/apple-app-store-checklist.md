# Apple App Store — Full Launch Checklist

Pull from this file ONLY when an Apple phase is active. Apple is stricter and
has MORE forms than Google Play — work top to bottom, do not skip a section.

## 1. Account (one-time / yearly — do first, has lead time)
- [ ] Apple ID with **two-factor auth** enabled
- [ ] Enroll in **Apple Developer Program** — **US $99/year**
      https://developer.apple.com/programs/
- [ ] **Individual vs Organization**: Organization needs a **D-U-N-S number**
      (free, but request EARLY — can take days to weeks to get/verify)
- [ ] Mac with **Xcode** installed (Apple builds require macOS + Xcode; no
      Windows path. Alternatives: Expo EAS cloud build, or a Mac in the cloud)

## 2. Agreements, Tax, and Banking (App Store Connect → Business)
This blocks submission/sale if incomplete — beginners miss it constantly.
- [ ] **Free apps**: accept the free **Apple Developer Program License Agreement**
- [ ] **Paid / in-app purchase apps** ALSO need:
  - [ ] **Paid Applications Agreement** accepted (Agreements tab)
  - [ ] **Bank account** added (Banking)
  - [ ] **Tax forms** completed (US W-9/W-8BEN, plus regional tax info)
- [ ] Agreement status must show **Active** before the app can go on sale

## 3. Identifiers & Signing (developer.apple.com → Certificates, IDs & Profiles)
- [ ] **Bundle ID** registered (e.g. com.yourcompany.yourapp) — must match the
      app's bundle identifier exactly
- [ ] Enable required **Capabilities** on the Bundle ID (Push, Sign in with
      Apple, etc.) if the app uses them
- [ ] **Distribution certificate** + **App Store provisioning profile**
      (Xcode → Signing → "Automatically manage signing" handles this for most)

## 4. App-side requirements BEFORE you build (Apple-specific, 2026)
- [ ] **Privacy Manifest** `PrivacyInfo.xcprivacy` included in the app AND any
      SDKs that require one. Declares collected data + **Required Reason API**
      usage. Missing/incorrect → email **ITMS-91053 / 91056** and rejection.
- [ ] **Info.plist usage strings** for every sensitive API used:
      `NSCameraUsageDescription`, `NSPhotoLibraryUsageDescription`,
      `NSLocationWhenInUseUsageDescription`, `NSMicrophoneUsageDescription`,
      `NSContactsUsageDescription`, `NSUserTrackingUsageDescription` (ATT).
      Missing string = crash on access OR rejection (ITMS-90683).
- [ ] **App Tracking Transparency**: if the app tracks users across other
      companies' apps/sites, you MUST show the ATT prompt + set
      `NSUserTrackingUsageDescription`.
- [ ] **Sign in with Apple**: if the app offers third-party/social login
      (Google, Facebook, etc.) as the only/primary option, you must ALSO offer
      Sign in with Apple (Guideline 4.8) — limited exceptions.
- [ ] **Account deletion**: if the app supports account creation, it must
      provide an **in-app way to delete the account** (Guideline 5.1.1(v)).
- [ ] **Export compliance**: set `ITSAppUsesNonExemptEncryption` in Info.plist
      (usually `false` for standard HTTPS) to skip the question every upload.
- [ ] App icon in asset catalog (all sizes), launch screen, no private APIs,
      supports current iOS, 64-bit, IPv6-compatible networking.

## 5. The bundle
- [ ] Format = **IPA** archived from Xcode (or `eas build --platform ios`)
- [ ] Set **Version** (e.g. 1.0.0) and **Build** number — Build MUST increase
      on every upload (duplicates rejected)
- [ ] Xcode → Product → **Archive** → Distribute App → App Store Connect →
      Upload (or export `.ipa` and upload via the **Transporter** app)
- [ ] Wait for the build to finish **Processing** in App Store Connect
      (TestFlight tab) before it can be selected for a version

## 6. Create the app record (App Store Connect → Apps → +)
- [ ] Platform(s), App Name, Primary language, **Bundle ID**, **SKU**
      (internal id, any unique string), user access

## 7. App Information (APP-LEVEL — shared across all versions)
- [ ] Name, Subtitle (max 30) ← Phase 0 "problem in one sentence"
- [ ] **Privacy Policy URL** (required — hosted page)
- [ ] **Category** (Primary + optional Secondary)
- [ ] **Content Rights** — does it contain third-party content? declare
- [ ] **Age Rating** questionnaire (be honest — drives age gate)
- [ ] **License Agreement** — default Apple EULA or your custom one
- [ ] Localizations if shipping multiple languages

## 8. Pricing and Availability (APP-LEVEL)
- [ ] **Price** — Free, or pick a price tier
- [ ] **Availability** — all countries/regions or a subset
- [ ] Pre-orders (optional), distribution method (Public App Store / Unlisted /
      Custom for Apple Business/Education)

## 9. Version page (PER-VERSION — the big form)
- [ ] **Promotional Text** (changeable without review)
- [ ] **Description** (full marketing copy)
- [ ] **Keywords** (100 chars, comma-separated, no spaces best)
- [ ] **Support URL** + **Marketing URL**
- [ ] **Version** number + **Copyright**
- [ ] **App icon** 1024×1024 (no alpha, no rounded corners)
- [ ] **Screenshots / App Previews** per required device size — at minimum
      **6.7" iPhone**; **13" iPad** if the app supports iPad. Verify exact
      current pixel sizes in App Store Connect's upload panel (Apple changes).
- [ ] **"What's New in This Version"** (for updates)
- [ ] **Build** — select the processed build from step 5
- [ ] **App Review Information**:
  - [ ] Sign-in required? Provide working **demo account** (user + pass)
  - [ ] Contact first/last name, phone, email
  - [ ] **Notes** — explain anything non-obvious + how to reach hidden features
  - [ ] Optional attachment (e.g. a doc/video for complex flows)
- [ ] **Version Release** — Manually / Automatically / **Phased (7-day)**
- [ ] **Routing App Coverage File** only if it's a maps app (rare)

## 10. App Privacy (APP-LEVEL — the nutrition label, separate from #7)
- [ ] **App Privacy** questionnaire — every data type collected, whether it is
      **linked to the user**, and whether **used to track**. Must match what
      the app + its SDKs actually do (must also match the Privacy Manifest).

## 11. TestFlight (recommended before App Store submit)
- [ ] **Internal testers** (your team, up to 100, no review) — fastest sanity
- [ ] **External testers**: requires **Beta App Review** + Beta App
      Description + feedback email + export compliance answer
- [ ] Verify on real devices via TestFlight before submitting for App Review

## 12. Submit for App Review
- [ ] Add the build to the version → click **Add for Review** → **Submit**
- [ ] Status: Waiting for Review → In Review → Pending Developer Release /
      Ready for Distribution (or Rejected)
- [ ] Pre-check against `common-rejections.md` BEFORE submitting

## Timelines
- App Review: typically **24–48 hours**; first submission, sign-in apps,
  account-deletion apps, or kids apps can take longer.
- Beta App Review (external TestFlight): usually faster, still required.
