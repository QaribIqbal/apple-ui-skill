---
name: apple-hig-bible
description: The user's binding authority for Apple-style and minimal design, built from every page of Apple's Human Interface Guidelines (developer.apple.com/design/human-interface-guidelines). Use in ANY project and on ANY platform (iOS, macOS, web, Flutter, Android, React, slides) whenever the user wants something Apple-like, Apple-inspired, "like Apple", Apple-quality, clean/minimal/minimalist design, HIG compliance, or asks to design, build, restyle or review a UI, component, screen, layout, icon set, color palette, typography or interaction in that spirit. Load it before making any such design decision.
metadata:
  source: https://developer.apple.com/design/human-interface-guidelines
  pages: 158 (all pages, read in full on 2026-10-22, condensed into references/)
  version: 1.1.0 (adds motion-and-glass recipes)
---

# Apple HIG — the design bible

The user has made Apple's Human Interface Guidelines the **authority** for Apple-style and minimal design in every project. When this skill is active, the HIG decides. Your own taste, generic "best practices" and framework defaults only fill gaps the HIG leaves open.

`references/` holds a condensed rulebook of all 158 HIG pages in our own words, with each page's live URL. The live page is the final word. If a decision depends on exact wording, or the rulebook seems thin or out of date, fetch the page at its URL.

## Order of authority

1. Explicit requirements from the user or the project spec win. Examples: bilingual labels, or one step per screen for low-literacy users. The HIG supports them; it doesn't override them.
2. The HIG, through this rulebook and the live pages.
3. The platform's own conventions, where the HIG says to follow the host platform (for example web, Android or Flutter).
4. Your own judgement, for anything none of the above covers. Say when you're relying on it.

## How to use it

1. **Work out what the request touches.** Use the topic map below to find which reference files cover it, for example a form screen means Entering data, Text fields, Buttons, Layout, Typography, Color and Accessibility.
2. **Read those sections before designing or coding.** Use `grep -n "^## <Page title>"` on the reference file to jump straight to a page.
3. **Apply the rules.** Keep the numbers exact. When the target isn't an Apple platform, use the page's "Beyond Apple platforms" line, plus the translation table below.
4. **Cite the rule** when you make a design call, briefly ("HIG Buttons: one primary action per view"), so the user can see what decided it.
5. **For a review or audit**, check the work against the relevant pages and report each violation with the rule it breaks. If your environment has an `apple-hig-expert` or `swiftui-pro` skill, use it as well for native Apple audits and SwiftUI code quality.
6. **For animation, press feedback, transitions and translucent bars**, follow the recipes in `references/motion-and-glass.md`. They set how things move and how glass is built, not colours, fonts or layout. Those stay the app's own.

## Topic map

| File | Pages |
|---|---|
| `references/motion-and-glass.md` | How-to recipes (no colours, fonts or layouts): spring press feedback with haptics, motion values, staggered entrance, shared-element card-to-details flight, Wallet-style card stack, glass surface recipe, floating tab bar, collapsing large titles, sheets, undo toasts, skeleton loading, Reduce Motion / Reduce Transparency fallbacks. Flutter, SwiftUI and CSS notes. |
| `references/getting-started.md` | Design principles (Purpose, Agency, Responsibility, Familiarity, Flexibility, Simplicity, Craft, Delight); Designing for iOS, iPadOS, macOS, tvOS, visionOS, watchOS, games, iPhone Duo |
| `references/foundations.md` | Accessibility, App icons, Branding, Color, Dark Mode, Icons, Images, Immersive experiences, Inclusion, Layout, Materials (incl. Liquid Glass), Motion, Privacy, Right to left, SF Symbols, Spatial layout, Typography, Writing |
| `references/patterns.md` | Charting data, Collaboration and sharing, Drag and drop, Entering data, Feedback, File management, Going full screen, Launching, Live-viewing apps, Loading, Managing accounts, Managing notifications, Modality, Multitasking, Offering help, Onboarding, Playing audio/haptics/video, Printing, Ratings and reviews, Searching, Settings, Undo and redo, Workouts |
| `references/components-core.md` | Content (Charts, Image/Text/Web views); Layout and organization (Boxes, Collections, Column views, Disclosure controls, Labels, Lists and tables, Lockups, Outline views, Split views, Tab views); Navigation and search (Path controls, Search fields, Sidebars, Tab bars, Token fields); Presentation (Action sheets, Alerts, Page controls, Panels, Popovers, Scroll views, Sheets, Windows); Selection and input (Color wells, Combo boxes, Digit entry, Image wells, Pickers, Segmented controls, Sliders, Steppers, Text fields, Toggles, Virtual keyboards); Status (Activity rings, Gauges, Progress indicators, Rating indicators) |
| `references/components-actions-system.md` | Menus and actions (Activity views, Buttons, Context menus, Dock menus, Edit menus, Home Screen quick actions, Menus, Ornaments, Pop-up/Pull-down buttons, Menu bar, Toolbars); System experiences (App Shortcuts, Complications, Controls, Live Activities, Notifications, Snippets, Status bars, Top Shelf, Watch faces, Widgets) |
| `references/inputs.md` | Action button, Apple Pencil and Scribble, Camera Control, Digital Crown, Eyes, Focus and selection, Game controls, Gestures, Gyroscope and accelerometer, Keyboards, Nearby interactions, Pointing devices, Remotes |
| `references/technologies.md` | AirPlay, Always On, App Clips, In-App Purchase, Apple Pay, AR, CareKit, CarPlay, Game Center, Generative AI, HealthKit, HomeKit, iCloud, ID Verifier, iMessage apps, Live Photos, Mac Catalyst, Machine learning, Maps, NFC, Photo editing, ResearchKit, SharePlay, ShazamKit, Sign in with Apple, Siri, Tap to Pay, VoiceOver, Wallet |

## Quick card (check these on every design)

These are taken from the rulebook. Read the full pages for detail.

- **Principles:** purpose first; include only what's necessary; use the fewest words; make every action reversible; keep the same element looking and behaving the same everywhere; treat accessibility as a day-one requirement; never let decoration get in the way of the task.
- **Hit targets:** at least 44×44 pt on iOS, iPadOS and watchOS (28×28 pt absolute minimum), 60×60 pt on visionOS, 28×28 pt on macOS. Leave enough space between controls to tell them apart.
- **Text size:** default/minimum is 17/11 pt on iOS and iPadOS, 13/10 pt on macOS. Text must scale to at least 200% (Dynamic Type or an equivalent). Use system fonts for body and captions; custom fonts only for headlines, and they must stay legible at every size.
- **Contrast:** at least 4.5:1 for text up to 17 pt, 3:1 for 18 pt and larger and for bold text. Check both light and dark appearance.
- **Color:** never use color alone to carry meaning. Use semantic and system colors, test in Dark Mode, and use one accent color consistently.
- **Buttons:** one primary (prominent) action per view, and never put the primary style on a destructive action. Roles are normal, primary, cancel and destructive (system red). Labels are verbs; add "…" when the button leads to more input.
- **Alerts:** only for rare, important, usually irreversible situations. Don't use them for routine destructive actions that can be undone; offer undo instead. Put Cancel where the platform expects it.
- **Undo:** support undo and redo rather than asking for confirmation, and name the action being undone ("Undo Typing").
- **Layout:** use standard margins (16 pt typical, 11 pt for tighter groups), respect safe areas, align with corners that share a centre (concentric), and put the most important content first.
- **Motion:** purposeful and brief. Respect Reduce Motion by replacing zoom and depth with fades and avoiding automatic repeating animation.
- **Writing:** short, direct, consistent terms; describe actions and outcomes; avoid jargon and blaming the user.
- **Navigation:** tab bars for top-level sections (not for actions), sidebars on larger screens, clear back paths; modal sheets only for self-contained tasks, always with an obvious way out.
- **Loading and feedback:** show content as fast as possible, use progress indicators that match how long it takes, and give immediate, quiet feedback for every action.

## Translating to non-Apple platforms

- 1 pt ≈ 1 dp (Android/Flutter logical pixel) ≈ 1 CSS px at 1×. So 44 pt ≈ 44 dp ≈ 44 px. Material's 48 dp target also satisfies this.
- The SF Pro / system font becomes the platform's system UI font. Keep the HIG's type scale proportions and minimum sizes.
- SF Symbols become a single consistent icon set with matching stroke weight, such as Material Symbols or Lucide. Keep the HIG's icon rules: simple, recognizable, labelled when the meaning is ambiguous.
- Liquid Glass and materials become translucency or blur only where the platform renders it well. Otherwise use solid layers with clear separation.
- Where a page says "Apple-only", don't imitate the Apple-specific UI on other platforms. Apply its underlying principle instead.
