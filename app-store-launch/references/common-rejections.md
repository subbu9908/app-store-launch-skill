# Common Store Rejections — Cause & Fix

Match a rejection email / screenshot against this list. Explain the cause in
plain words, then give the exact fix.

## Both stores
| Symptom | Cause | Fix |
|---|---|---|
| "App crashes on launch" | Reviewer's device hit a crash | Test release build on a clean device; check crash logs; never submit a debug build |
| Broken / placeholder content | Lorem ipsum, dead links, "coming soon" screens | Remove all placeholders before submit |
| Privacy policy missing/invalid | URL 404s or doesn't cover the app | Host a real policy page that names the data you collect |
| Login required, no test account | Reviewer can't get past sign-in | Provide working demo credentials in review notes/App Review Information |
| Data declaration mismatch | Declared data ≠ what app actually collects | Make Data Safety / App Privacy match reality exactly |

## Google Play specific
| Symptom | Cause | Fix |
|---|---|---|
| "Upload an AAB" / apk rejected | Sent APK for a new app | Build `.aab` (`./gradlew bundleRelease` / `eas build`) |
| "Version code already used" | Reused versionCode | Increment `versionCode` in `android/app/build.gradle` |
| Data safety section incomplete | Required form not finished | Complete every Data safety question; save & submit the section |
| Target API level too low | Play enforces a minimum target SDK | Bump `targetSdkVersion` to the currently required level and rebuild |
| Permissions policy violation | Requesting sensitive perms (SMS, location bg) without justification | Remove unused permissions or submit the permissions declaration form |

## Apple specific
| Symptom | Cause | Fix |
|---|---|---|
| Guideline 2.1 "more information needed" | Reviewer couldn't fully test | Add detailed review notes + demo account + steps |
| Guideline 4.0 design / 4.2 minimum functionality | App feels like a thin wrapper / web page | Add native value, not just a website in a shell |
| Guideline 5.1.1 data collection | Asks for data not needed for core function | Make data optional or remove the prompt |
| "Account deletion required" | App has account creation but no in-app delete | Add an in-app delete-account path |
| Build doesn't appear in App Store Connect | Processing/export-compliance not answered | Wait for processing; answer encryption question; re-select build |
| Duplicate build number | Reused Build number | Increment Build in Xcode and re-archive |
| Email ITMS-91053 / 91056 | Missing/incomplete **Privacy Manifest** (PrivacyInfo.xcprivacy) for required-reason APIs or an SDK | Add/fix `PrivacyInfo.xcprivacy`; update SDKs that ship their own manifest; re-upload |
| ITMS-90683 "Missing purpose string" | Used a sensitive API with no Info.plist usage description | Add the matching `NS...UsageDescription` string and re-archive |
| Guideline 4.8 sign-in | Social/3rd-party login without Sign in with Apple | Add Sign in with Apple as an equivalent option |
| Guideline 5.1.1(v) | Account creation but no in-app account deletion | Add an in-app delete-account flow |
| ITMS-90809 / invalid binary | Deprecated API, missing icon size, non-public API, bad architecture | Read the exact ITMS message; fix the named item; re-archive |
| ATT / IDFA rejection | Tracks users but no ATT prompt or `NSUserTrackingUsageDescription` | Implement the ATT prompt + add the usage string, or stop tracking |
| Agreement not active | Paid Apps Agreement / Tax / Banking incomplete | Complete App Store Connect → Business; wait for status = Active |

## Pre-submission self-check (run before every submit)
- [ ] Release (not debug) build, tested on a real device
- [ ] No placeholder text/images/links anywhere
- [ ] Hosted privacy policy that matches declared data
- [ ] Demo account provided if login exists
- [ ] Version/build number incremented
- [ ] Data Safety / App Privacy matches actual behavior
- [ ] Account deletion path if accounts exist
- [ ] (Apple) Privacy Manifest present + matches App Privacy answers
- [ ] (Apple) Every sensitive API has its Info.plist usage string
- [ ] (Apple) Sign in with Apple offered if social login is used
- [ ] (Apple) Agreements/Tax/Banking = Active (esp. paid / IAP apps)
