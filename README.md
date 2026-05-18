# app-store-launch

A [Claude Code](https://claude.com/claude-code) skill that walks **anyone** —
including people with zero prior knowledge — through publishing an app to the
**Google Play Store** and/or the **Apple App Store**, from start to finish.

It is **interactive**: it asks you about your business problem, builds your
store listing for you, and when you paste a **screenshot** of a console screen
it tells you exactly where you are and gives you multiple-choice next steps —
so you never have to guess what to click.

---

## What it does

| Phase | What happens |
|------|---------------|
| 0. Business intake | Asks what your app is, the problem it solves, who it's for, which store, free/paid. Reuses this to write your store listing. |
| 1. Readiness gate | Figures out where you actually are and what's blocking you (developer account, app not tested, etc.). |
| 2. Build the bundle | Explains AAB (Android) / IPA (iOS) and signing in plain words, then gives the exact build commands for your stack. |
| 3. Create the app | Play Console / App Store Connect app creation. |
| 4. Store listing | Auto-drafts your title, description, and tells you exactly which images/sizes to make. |
| 5. Compliance forms | Privacy policy, Data Safety / App Privacy, content rating — the part beginners get stuck on. |
| 6. Testing tracks | Internal testing / TestFlight before going public. |
| 7. Submit for review | What the store checks, timelines, and how to avoid the common rejections. |
| 8. Live + after launch | Going live, then how to ship updates. |

At every step you can paste a screenshot and it will recognize the screen and
guide you from there.

---

## Install

A Claude Code skill is just a folder. Copy the `app-store-launch/` folder into
your skills directory:

**One user (global):**
```bash
git clone https://github.com/<your-username>/app-store-launch-skill.git
cp -r app-store-launch-skill/app-store-launch ~/.claude/skills/
```

**One project only:**
```bash
cp -r app-store-launch-skill/app-store-launch <your-project>/.claude/skills/
```

(On Windows PowerShell, use `Copy-Item -Recurse app-store-launch-skill\app-store-launch $HOME\.claude\skills\`.)

That's it. Restart Claude Code if it was open.

---

## Use

Just tell Claude what you want, in plain language:

> "I want to publish my app to the Play Store but I have no idea how."

or

> "Help me get my app on the App Store."

Claude will load this skill automatically and start at Phase 0. Answer its
questions, and **paste a screenshot any time you're stuck** — it will tell you
which screen you're on and exactly what to do next.

### Example

```
You: i want to publish my app, i don't know anything about this
Claude: (Phase 0) What's the app called? What problem does it solve in one
        sentence? Which store — Google Play, Apple, or both?
You: ...answers...
Claude: Here's your Launch Brief — confirm. Next: do you have a Google Play
        Developer account? (it's a one-time $25 fee) ...
You: (pastes a screenshot of the Play Console "App content" page)
Claude: You're on Play Console → App content. Data safety is red. Pick:
        ① I'll walk you through Data safety
        ② Do Content rating first
        ③ Help me create a privacy policy
```

---

## Repo layout

```
app-store-launch-skill/
├── README.md                 ← you are here
├── LICENSE
└── app-store-launch/         ← the skill (copy THIS into ~/.claude/skills/)
    ├── SKILL.md              ← the workflow Claude follows
    └── references/
        ├── google-play-checklist.md
        ├── apple-app-store-checklist.md
        ├── common-rejections.md
        └── store-listing-template.md
```

---

## Notes

- Store UIs and exact image/SDK requirements change over time. This skill
  teaches the durable process and always tells you to verify size/SDK numbers
  in the live console panel, rather than hardcoding values that go stale.
- It does not need an API key or any paid service to run — it's a guide.

## License

MIT — see [LICENSE](LICENSE). Free to use, modify, and share.
