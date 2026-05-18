# Google Play — Full Launch Checklist

Pull from this file ONLY when a Google Play phase is active.

## Account (one-time, do first)
- [ ] Google account ready
- [ ] Go to https://play.google.com/console → pay **one-time US $25**
- [ ] Complete identity verification (gov ID; can take 1–2 days)
- [ ] For an **organization** account: D-U-N-S number may be required (lead time)
- [ ] Set up a payments profile if the app is paid / has IAP

## The bundle
- [ ] Format = **AAB** (`.aab`), NOT apk, for new apps
- [ ] App is signed with an **upload key** (keystore)
- [ ] **Backed up**: `.keystore` file + key alias + both passwords stored
      somewhere safe (password manager). Losing this blocks all future updates
      unless enrolled in Play App Signing (recommended — Google holds the app
      signing key, you only manage the upload key).

## Create app
- [ ] Play Console → Create app
- [ ] App name, default language, App or Game, Free or Paid
- [ ] Accept declarations

## Store listing (Grow → Store presence → Main store listing)
- [ ] App name (max 30 chars)
- [ ] Short description (max 80 chars) ← Phase 0 "problem in one sentence"
- [ ] Full description (max 4000 chars)
- [ ] App icon — 512×512 PNG, 32-bit
- [ ] Feature graphic — 1024×500
- [ ] Phone screenshots — min 2, 16:9 or 9:16, 320–3840 px
- [ ] (Optional) 7-inch + 10-inch tablet screenshots
- [ ] App category + tags
- [ ] Contact email (required), website/phone optional

## App content (the stall point — Policy → App content)
- [ ] **Privacy policy URL** — must be a real hosted page
- [ ] **Data safety** — declare data collected/shared, per type, with purpose
      and whether encrypted in transit / user can request deletion
- [ ] **Content rating** — fill questionnaire honestly; rating auto-assigned
- [ ] **Target audience and content** — age groups; Families policy if kids
- [ ] **Ads** — does the app contain ads? yes/no
- [ ] **News app / COVID / Government** declarations if applicable
- [ ] **Data deletion** — provide in-app + URL path to delete account/data if
      the app has accounts

## Release
- [ ] Choose track: **Internal testing** first (recommended), then Production
- [ ] Internal testing: add tester emails, share opt-in link
- [ ] Create release → upload `.aab` → release notes
- [ ] Set countries/regions
- [ ] Production release → set **staged rollout %** (e.g. 20%)
- [ ] Submit → status goes "In review"

## Timelines
- First app review: can take up to ~7 days, usually faster
- Subsequent updates: hours to ~3 days
