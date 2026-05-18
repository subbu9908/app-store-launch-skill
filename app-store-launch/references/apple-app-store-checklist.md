# Apple App Store — Full Launch Checklist

Pull from this file ONLY when an Apple phase is active.

## Account (one-time/yearly, do first)
- [ ] Apple ID with two-factor auth
- [ ] Enroll in **Apple Developer Program** — **US $99/year**
      https://developer.apple.com/programs/
- [ ] Individual vs Organization (org needs a **D-U-N-S number** — request
      early, can take days/weeks)
- [ ] Accept agreements in App Store Connect; for paid apps complete the
      **Paid Apps agreement** + banking + tax forms (blocks paid release)

## Identifiers & signing (Apple is stricter than Google here)
- [ ] **Bundle ID** registered (developer.apple.com → Identifiers)
- [ ] Distribution certificate + App Store provisioning profile
      (Xcode "Automatically manage signing" handles this for most users)

## The bundle
- [ ] Format = **IPA** archived from Xcode
- [ ] Set **Version** (e.g. 1.0.0) and **Build** number (must increase every
      upload — duplicates are rejected)
- [ ] Xcode → Product → Archive → Distribute App → App Store Connect → Upload
- [ ] (Or use **Transporter** app to upload an exported `.ipa`)

## Create app record (App Store Connect)
- [ ] https://appstoreconnect.apple.com → Apps → +
- [ ] Platform, Name, Primary language, Bundle ID, SKU

## App information & listing
- [ ] Subtitle (max 30) ← Phase 0 "problem in one sentence"
- [ ] Promotional text + Description
- [ ] Keywords (100 chars, comma-separated)
- [ ] Support URL + Marketing URL
- [ ] App icon (1024×1024, no alpha, no rounded corners)
- [ ] Screenshots — required per device size; at minimum 6.7" iPhone +
      (if iPad supported) 12.9" iPad. Exact pixel sizes change — verify in
      App Store Connect's upload panel for the current requirement.
- [ ] Category, age rating questionnaire

## App Privacy (the stall point)
- [ ] **App Privacy** questionnaire — data types collected, linked to user,
      used for tracking; per Apple's nutrition-label model
- [ ] **Privacy Policy URL** (required)
- [ ] **Export compliance** — does the app use encryption? (usually "no" beyond
      standard HTTPS — but answer honestly)
- [ ] **Sign-in required?** Provide a working **demo account** (username +
      password) in App Review Information or the app WILL be rejected
- [ ] App Review notes — explain anything non-obvious to the reviewer

## Submit
- [ ] (Recommended) **TestFlight** internal/external testing first
- [ ] Select build → "Add for Review" → Submit
- [ ] Choose manual or automatic release after approval
- [ ] Phased release (7-day gradual rollout) optional

## Timelines
- App Review: typically 24–48 hours; can be longer for first submission or
  if extra review (e.g. account deletion, sign-in apps) is triggered
