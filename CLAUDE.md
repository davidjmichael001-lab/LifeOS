# LifeOS: project rules

Personal iOS app for one user (David, iPhone 13). Not for the App Store.

## Environment (read first)
- I develop on **Windows**. There is no Xcode, no simulator, and no local Swift build for iOS.
- **GitHub Actions is the compiler.** To check that code builds, commit, push, and read the run: `gh run watch` / `gh run view --log-failed`.
- Don't push one change at a time. Group related changes, then push.
- The Xcode project is generated from `project.yml` by XcodeGen in CI. Never create or edit a `.xcodeproj` by hand. Add new files under `LifeOS/` and they get picked up automatically.
- Install path: unsigned .ipa from a tagged GitHub Release, re-signed by SideStore with a free Apple ID.

## Hard constraints (free Apple ID via SideStore)
- No Family Controls / Screen Time API (no app blocking). Use focus reminders and notifications instead.
- No push notifications from a server, no CloudKit, no iCloud sync. Local notifications are fine.
- Keep app extensions to a minimum. Each one uses an App ID (10 per week max). Ask before adding any widget or Live Activity extension.
- Any API keys or cookies go in the Keychain via an in-app Settings screen. Never in code, never committed.

## Stack
- Swift 6, SwiftUI, SwiftData, Swift Testing. iOS 17 minimum.
- Architecture: feature folders (`Features/Study`, `Features/Training`, `Features/Skincare`, `Features/Glow`, `Features/Today`), plus `Core/` for models and shared services.
- All data stays local on the device. Progress photos are stored in the app sandbox, never uploaded.

## How we work
1. New feature: grill-me / brainstorming first, then a written plan in `docs/plans/`, then build.
2. Tests first for logic (timers, streaks, stats, progressive overload maths). Tests must pass in CI before tagging a release.
3. **Visual design: check with me before styling any new screen.** Default direction is Apple native (SF Symbols, system materials, Dynamic Type, dark mode). Show me 2 options in words or ASCII sketches, then wait for my answer.
4. After a screen is built, run the Apple design review and accessibility skills on it.
5. Before saying something is done: CI green, tests passing, and a short "how to check it on my phone" note.
6. Release: bump `CURRENT_PROJECT_VERSION` in project.yml, then `git tag vX.Y && git push --tags`.

## Usage budget (Claude Pro)
- Use Opus for planning and tricky bugs. Use Sonnet for routine building.
- Keep replies short. Don't re-read whole files you've already read. Skip brainstorming when I say "quick fix".

## Writing style for me
- Concise and direct. No em dashes.
