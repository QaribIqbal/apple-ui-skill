# Getting started — HIG digest
Source pages: 9. Digest written 2026-10-22. Live pages are authoritative when in doubt.

## Design principles
URL: https://developer.apple.com/design/human-interface-guidelines/design-principles
Essence: Eight guiding principles (Purpose, Agency, Responsibility, Familiarity, Flexibility, Simplicity, Craft, Delight) used to weigh trade-offs; there is no single correct way to apply them.
Rules:
- Purpose: decide what the product is for and make a few core features excellent; every stage should ask whether the design serves that purpose. Study existing solutions and differentiate rather than copy.
- Agency: get people straight to the task or content; stay unobtrusive. Do not lock users into modes or flows; any guided flow must be easy to skip or exit.
- Build forgiveness in: every action should be reversible or recoverable (undo, back, restore previous state) without costing time or work.
- Responsibility: state clearly what the product does and why; give a rationale when requesting permissions; collect only the data needed and explain its use; anticipate misuse and add safeguards.
- Familiarity: lean on real-world and existing software metaphors; once an element has a look or behavior, repeat it everywhere; give clear feedback (show control availability, content changes, use system patterns for alerts/choices).
- Flexibility: treat accessibility as a day-one priority; support many input methods (touch, keyboard, voice, pointer); keep controls and content in consistent positions across platforms/sizes and use natural animation for transitions; give each platform equal care.
- Simplicity: include only what is necessary (focused, not stripped-down for its own sake); use the fewest words that label a control or explain a concept; build clear hierarchy and recognizable controls so people know where they are and what comes next.
- Craft: be deliberate about visuals, animation, wording and audio; prototype early, iterate, discard what fails, test in real conditions; keep updating after shipping.
- Delight: pick the emotion the product should evoke (calm, energy, thrill) and let it shape the design; add character to key moments (even error messages) but never let decoration obstruct the task.
Avoid:
- Mistaking delight for decoration; forced linear flows; collecting data you do not need; inconsistent behavior of the same element; designing only for your own context or one input method.
Platform notes: Page reintroduced June 2026.
Beyond Apple platforms: Fully portable; a good checklist for any product design review.

## Designing for games
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-games
Essence: How to make a game feel native across Apple devices (onboarding, legibility, input, inclusivity, platform tech).
Rules:
- Let people play right after install: keep initial download to 30 minutes or less and fetch extra content in the background; choose good defaults from device resolution, paired controllers and accessibility settings.
- Teach through play (playable tutorial); written tutorials are optional reference, not a prerequisite. Ask for permissions in context when the feature needs them; ask for ratings only after meaningful play time.
- Default / minimum text size: iOS and iPadOS 17 / 11 pt; macOS 13 / 10 pt; tvOS 29 / 23 pt; visionOS 17 / 12 pt; watchOS 16 / 12 pt. Keep strong contrast with backgrounds.
- Default / minimum button size: iOS and iPadOS 44x44 / 28x28 pt; macOS 28x28 / 20x20 pt; tvOS 66x66 / 56x56 pt; visionOS 60x60 / 28x28 pt; watchOS 44x44 / 28x28 pt.
- Prefer resolution-independent (vector) art; otherwise match device resolution. Respect safe areas for rounded corners and camera housings.
- In-game menus must work at many aspect ratios (for example 16:10, 19.5:9, 4:3) and both orientations; use relative constraints rather than fixed layouts.
- Support each platform's default input: touch (iOS, watchOS), keyboard/mouse/trackpad (macOS), remote (tvOS), eyes and hands (visionOS). Support game controllers but always offer an alternative to them (not on watchOS).
- Do not rely on color alone or on cutscenes without subtitles; allow customizing type size, control mapping, motion intensity and sound balance.
- Offer inclusive avatar/name options and avoid stereotyped characters.
- Adopt platform tech where it fits: Game Center, iCloud game saves across devices, Core Haptics, Spatial Audio.
Avoid:
- Long first-run downloads, permission barrages before play, tiny text/buttons, fixed layouts that break on other aspect ratios, controller-only play.
Platform notes: Letterboxing is discouraged on iPhone Duo; prefer changing aspect ratio.
Beyond Apple platforms: The size table and onboarding rules transfer directly to any cross-platform game; 44 pt is the common touch-target floor.

## Designing for iOS
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-ios
Essence: Characteristics of iPhone (handheld, close viewing, touch, short and long sessions) that shape design.
Rules:
- Limit on-screen controls to focus on the primary task; reveal secondary actions with minimal interaction.
- Adapt to orientation, Dark Mode and Dynamic Type so people can pick their configuration.
- Favor reachability: controls in the middle or bottom of the screen are easier to hit; support swipe to go back and swipe actions on list rows.
- With permission, use device data (location, biometrics, payments) instead of making users type.
- Expect multitasking and frequent app switching; sessions range from seconds to hours.
Avoid:
- Piling controls on screen; making top-of-screen controls the only route to key actions.
Platform notes: Viewing distance is roughly a foot or two.
Beyond Apple platforms: Same thumb-zone and progressive-disclosure rules apply to any mobile UI.

## Designing for iPadOS
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-ipados
Essence: iPad is large, flexible and multi-input; design to use the space and many ways of holding it.
Rules:
- Use the large display to elevate content; minimize modals and full-screen transitions; place controls within reach but out of the way.
- Choose content size and density from viewing distance (about 3 feet) and input mode.
- Support touch, keyboard, trackpad and Apple Pencil, and combinations of them.
- Adapt to orientation, multitasking window sizes, Dark Mode and Dynamic Type; support drag and drop and side-by-side apps.
- Be ready to run on macOS as well.
Avoid:
- Stretched phone layouts; modal-heavy flows on a large canvas.
Platform notes: Multiple apps on screen at once is normal.
Beyond Apple platforms: Responsive tablet layouts should use extra width for more content or panes, not larger elements.

## Designing for iPhone Duo
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-iphone-duo
Essence: A dual-display foldable iPhone (page dated Sept 2026); design adaptive layouts for outer display, inner display, hinge and many poses.
Rules:
- Build to resize: use size classes (compact width for outer display, regular width for inner), layout margins and safe-area insets; no fixed widths or display-specific assumptions.
- Keep the same functionality, state and information hierarchy on both displays; the larger display may show an extra hierarchy level (for example list plus detail side by side).
- Reserved regions to avoid covering: the outer camera (always present, grows into the Dynamic Island), the inner camera (only when active), and the fold (conditional, splits the inner display when partly open).
- When folding, prefer adaptive containers like split views; in grids use an even number of columns; favor small adjustments over big rearrangements.
- Toolbars, tab bars and navigation controls move to the side on the outer display and inner landscape; the inner display in portrait keeps standard horizontal bars. Side controls stay on the same side in right-to-left languages.
- Toolbar order on the vertical axis: primary navigation (Back/Close) first at the top, then prominent actions like Done. Do not override default bar placement.
- Set visibility priorities so frequently used actions and badged items overflow last; group related items with system toolbar groups instead of manual spacing.
- Give each toolbar item both a title and a symbol (title is used in overflow menus); minimize text-only buttons; use the system overflow menu and reserve the ellipsis symbol for overflow.
- Keep controls near the content they affect; when space is tight choose compression by experience (navigation apps keep the tab bar, task apps minimize the tab bar).
- Arrangement views hold a primary and secondary view as split (horizontal if wider than tall, else vertical) or overlay; keep navigation containers outside them.
- Games: fill the screen in every pose, keep text and control sizes consistent, prefer aspect-ratio changes over letterboxing.
Avoid:
- Fixed widths, extreme layout changes on fold, custom per-pose layouts, custom overflow menus.
Platform notes: Mostly iPhone patterns still apply.
Beyond Apple platforms: Foldable-Android and responsive web guidance is similar: size-class style breakpoints, avoid hinge areas, keep state across panes.

## Designing for macOS
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-macos
Essence: Mac is a stationary, large-display, keyboard-and-pointer platform for long, multi-app sessions.
Rules:
- Use big displays for more content with fewer nested levels and less modality, but keep information density comfortable.
- Let windows resize, move, hide and go full screen.
- Expose all commands through the menu bar; support keyboard shortcuts and keyboard-only workflows.
- Support precise pointer input for pixel-level selection and edits.
- Support personalization: customizable toolbars, saved window configurations, user-chosen colors and fonts.
- Handle smooth active/inactive window transitions.
Avoid:
- Phone-style full-screen modal flows; commands reachable only by mouse.
Platform notes: Viewing distance about 1 to 3 feet.
Beyond Apple platforms: Desktop web apps benefit from the same shortcut, resizable-layout and density guidance.

## Designing for tvOS
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-tvos
Essence: Ten-foot, remote-driven, focus-based, cinematic experience.
Rules:
- Support Siri Remote gestures and the focus system (focused items highlight and expand gently).
- Design for viewing from 8 feet or more: edge-to-edge artwork, legible type, subtle fluid animation, rich audio.
- Make sign-in easy and rare; handle shared sign-in and switch profiles automatically when the viewer changes.
- Integrate with the TV app, SharePlay, Top Shelf, and picture-in-picture.
Avoid:
- Small text, dense layouts, pointer-style interactions.
Platform notes: Input also comes from game controllers, Siri, and phone companion apps.
Beyond Apple platforms: Applies to any 10-foot UI (Android TV, smart TVs): large type and visible focus states.

## Designing for visionOS
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-visionos
Essence: Spatial computing with unlimited canvas, passthrough, eyes-and-hands input and comfort as the top concern.
Rules:
- Apps start in the Shared Space (side-by-side windows) and can go to a Full Space; use the minimum immersion each moment needs, not full immersion everywhere.
- Use standard windows for contained UI tasks; system dynamic scaling keeps them legible near and far.
- Primary interaction: look at a target then make an indirect gesture (tap); direct touch is secondary.
- Comfort: keep content inside the field of view relative to the head; avoid fast, jarring motion or motion with no stationary reference; support indirect gestures with hands at rest; keep direct-touch targets close and not required for long periods; do not push heavy physical movement in full immersion.
- Support accessibility (VoiceOver, Switch Control, Dwell, Head Pointer); system components include it by default.
- Warn on safety: not for use while driving, near stairs, balconies or streets; users must be 13 or older.
- Use SharePlay with spatial Personas for shared activities.
Avoid:
- Placing content that forces head turns, constant motion, always-immersive design.
Platform notes: The Digital Crown adjusts passthrough amount.
Beyond Apple platforms: Applies to VR/AR in general: comfort and minimal immersion.

## Designing for watchOS
URL: https://developer.apple.com/design/human-interface-guidelines/designing-for-watchos
Essence: Glanceable, brief, wrist-based interactions supported by complications and notifications.
Rules:
- Single-screen, glanceable interactions; deliver critical info succinctly with one or two gestures.
- Keep navigation shallow; use the Digital Crown for vertical scrolling and screen switching.
- Anticipate needs using on-device data; show what is relevant now or soon.
- Use complications for live data on the watch face and notifications for timely, actionable info.
- Use background color for supporting info and materials for hierarchy and place.
- The app should work independently, adding detail beyond notifications and complications.
- Plan for the Always On display; interactions often last under a minute.
Avoid:
- Deep hierarchies, long flows, dense screens.
Platform notes: Viewing distance is about a foot or less.
Beyond Apple platforms: Applies to any wearable or glance UI: minimal depth, big type.
