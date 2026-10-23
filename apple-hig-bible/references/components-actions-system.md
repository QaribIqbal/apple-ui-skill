# Components — menus & actions, system experiences — HIG digest
Source pages: 22. Digest written 2026-10-22. Live pages are authoritative when in doubt.

# Part A — Menus and actions

## Activity views
URL: https://developer.apple.com/design/human-interface-guidelines/activity-views
Essence: The share sheet, a system panel of sharing activities and actions for the current item or context.
Rules:
- Open it from the standard Share button; do not invent a second way to reach the same list.
- Do not rebuild system actions (Copy, Print, Add to Files). If your version differs, give it a specific title such as "Print Transaction".
- Custom action titles: one verb or a short verb phrase, no company or product name. Long titles wrap and may truncate.
- Custom action icons: prefer an SF Symbol; a custom icon should be centered in roughly a 70x70 px area.
- You cannot reorder system activities, but you can exclude irrelevant ones and choose which custom ones show.
- Share extensions: use the system compose view; keep interaction to a few steps (a one-tap post is ideal).
- Action extensions: include your app name, use a symbol or interface icon, and echo your app's look if you present UI.
- Never stack another modal over an extension (an alert is the only acceptable exception).
- Long tasks continue in the background; show progress in the main app. Notify on a problem, not on mere completion.
Avoid:
- Duplicate or look-alike system actions; extra modals above extensions; notifications that only say "done".
Platform notes: Exists on iOS, iPadOS, visionOS; not macOS (use Share toolbar button or context menu), tvOS, watchOS.
Beyond Apple platforms: Use the platform share intent (Android share sheet, Web Share API) rather than a custom share list.

## Buttons
URL: https://developer.apple.com/design/human-interface-guidelines/buttons
Essence: A button triggers an instantaneous action; defined by style, content and role.
Rules:
- Minimum hit region 44x44 pt (60x60 pt in visionOS); leave enough space around buttons to tell them apart.
- Every custom button needs a pressed state, otherwise it feels dead.
- Use a prominent (filled, accent-colored) style for the single most likely action; at most one or two prominent buttons per view.
- Distinguish the preferred choice by style, not size; buttons offering parallel choices should be the same size.
- Do not tint button labels with a color similar to colorful content behind them; prefer the default monochrome label then.
- Content: symbol, text or both. Pair familiar actions with familiar icons (square.and.arrow.up = share). Use text when a short label is clearer; start with a verb ("Add to Cart").
- Roles: Normal, Primary (default, answers Return, accent color), Cancel, Destructive (system red).
- Give the primary role to the most likely non-destructive choice; never to a destructive button, since people tap prominent buttons without reading.
- iOS/iPadOS: a button can swap to an activity indicator plus an alternate label ("Checkout" becomes "Checking out...") during delays.
- macOS push button: standard type; trailing ellipsis in the title when it opens further input; flexible-height variant only for two-line or tall content.
- macOS square (gradient) button: symbol only, no label, placed in or under the view it affects, never in toolbars or window frames.
- macOS help button: circular question mark, max one per window, lower corner (opposite the dismiss buttons in dialogs), no explanatory text, opens the context-relevant help topic.
- macOS image button: about 10 px padding around the image; label below it; not in the toolbar (use a toolbar item).
- visionOS: sizes Mini 28, Small 32, Regular 44, Large 52, Extra large 64 pt; shapes circle (icon), capsule or rounded rectangle (text). Keep button centers at least 60 pt apart; prefer capsule/circle; use glass material floating in space, thin material on glass windows.
- watchOS: inline buttons are capsules; use full-width buttons for primary actions; equal heights in stacks; corner actions go in the toolbar.
Avoid:
- White-fill/black-content custom buttons in visionOS (reserved for the toggled state); many prominent buttons; size differences to signal importance; text introducing help/square buttons.
Platform notes: Tooltips on hover in macOS/visionOS; visionOS has no custom hover effects and relies on audible feedback.
Beyond Apple platforms: Map directly: one filled primary per screen, 44-48 px targets, pressed/disabled states, verb labels, red destructive style, ellipsis when more input follows.

## Context menus
URL: https://developer.apple.com/design/human-interface-guidelines/context-menus
Essence: A hidden menu of the few commands most relevant to a specific item.
Rules:
- Include only high-relevance commands (e.g. Reply and Move for a mail message, not mailbox management).
- Keep it short; limit separators to about three groups.
- Be consistent: if some items have context menus, similar items everywhere should.
- Every command must also be reachable in the visible UI (toolbar, menu bar).
- At most one level of submenu, with a predictive title.
- Hide inapplicable items instead of dimming them (macOS Cut/Copy/Paste may dim).
- Put the most likely items nearest where the menu opens; reverse order if the menu opens upward.
- Do not show keyboard shortcuts in context menus; show them in the main menus.
- iOS/iPadOS/visionOS: list destructive items last, flagged destructive (red).
- Title only when it clarifies scope (e.g. "3 messages selected"). Use standard icons for Copy, Share, Delete.
- iOS/iPadOS: a context menu may show a preview; clip it to the content's shape so corners do not jump during the animation. Do not give the same item both a context menu and an edit menu.
- iPadOS: a context menu on empty space is a good way to offer New object.
- visionOS: prefer a context menu over a separate panel or inspector; keep its height within the window.
Avoid:
- Advanced or rare commands; long lists; context menu as the only access path.
Platform notes: Triggered by long-press (touch), pinch-and-hold (visionOS), Control-click or secondary click (Mac/iPad). Not on watchOS.
Beyond Apple platforms: Right-click/long-press menus on web and Android follow the same rules: short, relevant, never the sole path.

## Dock menus
URL: https://developer.apple.com/design/human-interface-guidelines/dock-menus
Essence: The menu shown when secondary-clicking an app's Dock icon on Mac.
Rules:
- Label succinctly and group logically like any menu.
- Duplicate every custom Dock command elsewhere (menu bar or UI).
- Prefer high-value items: open windows or recent documents, plus a few actions useful when the app is not frontmost (e.g. Get Mail, New Message).
Avoid:
- Using the Dock menu as the only access to a command.
Platform notes: macOS only; iOS equivalent is Home Screen quick actions.
Beyond Apple platforms: Comparable to desktop taskbar jump lists and Android app shortcuts.

## Edit menus
URL: https://developer.apple.com/design/human-interface-guidelines/edit-menus
Essence: The system menu for acting on selected content (Cut, Copy, Paste, Select, Translate, Look Up).
Rules:
- Use the system edit menu and its system reveal gestures (touch-and-hold or double-tap, pinch-and-hold in visionOS, secondary click on pointer devices).
- Show only relevant commands: no Copy/Cut without a selection, no Paste with nothing to paste.
- Place custom commands next to related system ones (formatting commands after the system format group); do not add many.
- Custom labels: verbs or short verb phrases.
- Let people copy non-editable content text (captions, statuses), but not control labels.
- Support undo and redo instead of confirming.
- Do not add redundant controls duplicating edit commands.
- Distinguish Delete (just removes) from Cut (copies first).
- iOS/iPadOS: the compact horizontal bar (touch) expands via chevron to a vertical menu (keyboard/pointer); design for both; you may nudge the position so it does not cover key content.
Avoid:
- Custom replacement edit menus; providing both an edit menu and a context menu on the same item.
Platform notes: Not on tvOS/watchOS. On macOS editing commands live in the Edit menu and the context menu.
Beyond Apple platforms: Use the native text selection toolbar on Android/web rather than custom ones.

## Home Screen quick actions
URL: https://developer.apple.com/design/human-interface-guidelines/home-screen-quick-actions
Essence: Shortcuts shown on long-press of the app icon.
Rules:
- Offer at least one useful action; maximum four.
- Choose high-value tasks (search nearby, directions home, new message).
- Titles are short, outcome-clear, without the app name; optional subtitle for state (e.g. unread counts). Keep short for truncation and localization.
- Dynamic quick actions are fine if changes are predictable (location, recent activity, time of day).
- Use SF Symbols or the Quick Action Icon Template; icons are monochrome.
Avoid:
- Emoji in place of an icon (full color breaks Dark Mode contrast); unpredictable changes.
Platform notes: iOS/iPadOS only.
Beyond Apple platforms: Equivalent to Android static/dynamic app shortcuts and PWA manifest shortcuts.

## Menus
URL: https://developer.apple.com/design/human-interface-guidelines/menus
Essence: General rules for labeling, organizing and structuring all menus.
Rules:
- Labels: verb or verb phrase for actions; title-style capitalization; drop articles (a, an, the).
- Show unavailable items dimmed and non-interactive; if every item is unavailable, keep the menu itself openable.
- Add an ellipsis (...) when the action needs more input before completing.
- Icons: use standard system icons; use sparingly and only when a clear one exists; give all items in a group icons, or none.
- Order: most important or frequent first; group related commands with separators, even if the group mixes importance (Paste and Match Style stays with Paste).
- Watch length; split long menus or use a submenu. Exceptions: dynamic user content (History, Bookmarks) may be long and scroll.
- Submenus: use sparingly, one level deep, about five items max; use a submenu when a term repeats in over two items ("Sort by..." becomes one submenu); keep the parent enabled even if children are not; never indent to fake hierarchy.
- Toggled items: either one changeable label (Show Map / Hide Map; add a verb if ambiguous, e.g. Turn HDR On), both actions shown, or a checkmark for active attributes; consider a "Plain" item that clears many toggles.
- In-game menus: use the platform's default interaction and re-check tap sizes when scaling to small screens.
- iOS/iPadOS layouts: Small (row of four icon-only items on top, for tight groups like Bold/Italic/Underline/Strikethrough), Medium (row of three with labels), Large (default list).
- visionOS: show menus near the content they control; breakthrough effect subtle by default, prominent only if essential, none if occluding is intended.
Avoid:
- Deep submenus, indentation, mixed icon/no-icon groups, very long menus.
Platform notes: Menu bar menus on macOS/iPadOS hold all commands.
Beyond Apple platforms: Applies to web dropdowns, Android overflow menus and Flutter PopupMenu: verb labels, ellipsis, grouping, one submenu level.

## Ornaments
URL: https://developer.apple.com/design/human-interface-guidelines/ornaments
Essence: visionOS controls that float just in front of a window edge without covering content.
Rules:
- Use for frequently needed controls or info that should stay in a stable place (e.g. Now Playing).
- Keep visible in most cases; hide only during immersive content like video or photo viewing.
- Limit the number of ornaments to preserve the window's visual balance; relocate elements into the window if you remove one.
- Keep an ornament no wider than its window.
- Borderless buttons work well on the glass background; they get the hover effect automatically.
- Toolbars and tab bars already render as ornaments; use the system ones.
Platform notes: visionOS only.
Beyond Apple platforms: Analogue is a detached floating control bar or bottom app bar that does not overlay content.

## Pop-up buttons
URL: https://developer.apple.com/design/human-interface-guidelines/pop-up-buttons
Essence: A button whose menu holds mutually exclusive options and shows the current choice.
Rules:
- Use for a flat list of exclusive states/choices; switch to a pull-down button for actions, multi-select or submenus.
- Provide a sensible default selection.
- Make options predictable without opening (introductory label or descriptive button label).
- Good for saving space when not all options need constant display.
- Add a "Custom" option for rare cases and optional explanatory text beneath the list.
- iPadOS: inside a popover or modal, prefer a pop-up button to a disclosure indicator for a small, well-defined option set.
Avoid:
- Using it for commands or multiple selection.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: This is the dropdown/select/spinner; use it for single choice, not for actions.

## Pull-down buttons
URL: https://developer.apple.com/design/human-interface-guidelines/pull-down-buttons
Essence: A button revealing a menu of actions or items tied to the button's purpose.
Rules:
- Use for commands related to the button (Add > type, Sort > attribute, Back > history).
- Use a pop-up button instead for exclusive non-command choices.
- Do not hide all a view's primary actions inside one pull-down.
- List at least three items; for one or two, use buttons or toggles. Too many slows people down.
- Add a menu title only if it adds meaning.
- Mark destructive items (red); the system then confirms with an action sheet (iOS) or popover (iPadOS).
- Add icons after labels only when they add value, preferably SF Symbols.
- iOS/iPadOS: a "More" (ellipsis) pull-down can hold low-priority items but hurts discoverability; weigh that.
Avoid:
- Putting everything in More; one- or two-item pull-downs.
Platform notes: Not on tvOS/watchOS; Safari-style long-press on a button can also reveal one.
Beyond Apple platforms: Equivalent to overflow/action menus on toolbars (Material menu button, web dropdown button).

## The menu bar
URL: https://developer.apple.com/design/human-interface-guidelines/the-menu-bar
Essence: Top-of-screen menus listing every command of a Mac or iPad app, in a standard order.
Rules:
- Standard order: AppName, File, Edit, Format, View, app-specific menus, Window, Help (macOS also has Apple menu leading and extras trailing).
- Keep the same menu items always visible; disable rather than hide.
- Prefer one-word menu titles (title case if more); menu bar height 24 pt on Mac.
- Use standard shortcuts for standard items (Copy, Cut, Paste, Save, Print) and define custom ones only if needed.
- App menu: About (first, alone in its group, short app name, 16 characters or fewer, no version number), Settings..., optional items, Services, Hide, Hide Others, Show All, Quit. Settings is for app-level settings; document settings go in File.
- File menu: New, Open, Open Recent (names not paths, newest first, Clear Menu), Close (Option for Close All), Save (autosave regularly), Duplicate (prefer to Save As/Export/Copy To), Rename..., Move To..., Export As... (only for formats the app does not normally handle), Revert To, Page Setup..., Print....
- Edit menu: Undo/Redo (name the target, e.g. Undo Typing), Cut, Copy, Paste, Paste and Match Style, Delete (not Erase/Clear), Select All, Find, Spelling and Grammar, Substitutions, Transformations, Speech; system adds Start Dictation and Emoji & Symbols at the bottom.
- Format menu: Font and Text submenus; omit if no rich text.
- View menu: Show/Hide Tab Bar, Show All Tabs, Show/Hide Toolbar, Customize Toolbar, Show/Hide Sidebar, Enter/Exit Full Screen. Keep the show/hide wording in sync with state. Provide View even for a subset (e.g. just Full Screen). No window navigation here.
- App-specific menus go between View and Window, ordered general to specific, mirroring the app's hierarchy; list all custom commands here even if available elsewhere (gives shortcuts and Full Keyboard Access).
- Window menu (provide even with one window): Minimize, Zoom (not for full screen), tab items, Merge All Windows, Bring All to Front, list of open windows alphabetically (no panels).
- Help menu: AppName Help, Send Feedback to Apple, few extras after a separator.
- Dynamic items (changed by one modifier key, e.g. Option) are shortcuts only, never the sole path, and best in menu bar menus.
- iPadOS: menu bar hidden until pointer at top or swipe down; centered; no Apple menu or extras; Settings item opens the app's page in iPadOS Settings; offer non-menu paths to everything; group items into submenus more readily (taller rows); add tabs to View with key bindings.
- macOS menu bar extras: use a symbol, show a menu not a popover, let the user choose to add it, do not rely on its presence, and offer a Dock menu as a reliable alternative.
Avoid:
- Hiding unavailable items; using the menu bar as a catch-all; Zoom for full screen.
Platform notes: Not on iOS, tvOS, visionOS, watchOS.
Beyond Apple platforms: For desktop web/Flutter apps, mirror this order and shortcut conventions so users find commands where they expect.

## Toolbars
URL: https://developer.apple.com/design/human-interface-guidelines/toolbars
Essence: Top or bottom bar of title, navigation, search and frequently used actions.
Rules:
- Avoid overcrowding; decide what moves to overflow as width shrinks. Do not hand-build an overflow menu on macOS/iPadOS (system adds it); avoid layouts that overflow by default.
- Use a More menu for lower-priority actions only when needed.
- iPadOS/macOS: let users customize the toolbar for feature-rich or long-session apps.
- Minimize custom backgrounds and tints; let content color shape the bar; use a scroll-edge effect to separate bar and content.
- Do not use item label colors similar to colorful content behind the bar.
- Prefer standard components (corner radii concentric with the bar).
- Titles: give each window one; skip if redundant; not the app name; concise, under 15 characters.
- Use standard Back and Close symbols, not "Back"/"Close" text.
- Actions: prioritize likely tasks; prefer simple recognizable symbols over text (except e.g. Edit); use system symbols without borders.
- Key action such as Done/Submit: prominent style, only one, trailing side.
- Three zones: leading (back, sidebar toggle, title, document menu; not customizable), center (common items, customizable, collapse to overflow), trailing (important items, inspectors, search, More, primary action; always visible).
- Group by function and frequency; at most about three groups; keep navigation and critical actions (Done, Close, Save) in distinct sections; keep groupings consistent across platforms.
- Separate text-labeled buttons from symbol buttons with fixed space so they do not read as one control.
- iOS: few main items plus More; large title that collapses when scrolling.
- iPadOS: can combine toolbar and tab bar.
- macOS: every toolbar item must also be a menu-bar command.
- visionOS: system toolbar at bottom edge; no vertical toolbars; keep the window at least as wide as its toolbar; avoid pull-down menus in it.
- watchOS: toolbar buttons in top corners or bottom; scrolling toolbar button for an important non-primary action.
Avoid:
- Too many items or groups; custom backgrounds; text labels reading "Back".
Platform notes: A toolbar is for actions and navigation; a tab bar is for switching top-level areas.
Beyond Apple platforms: Same as an app bar: title, up to ~3 groups, one primary action on the trailing side, overflow menu, symbols over text.

# Part B — System experiences

## App Shortcuts
URL: https://developer.apple.com/design/human-interface-guidelines/app-shortcuts
Essence: App actions exposed to Siri, Spotlight, Shortcuts, the Action button and Apple Pencil squeeze, available as soon as the app is installed.
Rules:
- Maximum 10 App Shortcuts per app; each is one or more App Intents actions.
- Offer the most common and important tasks, ideally completable without leaving the current context.
- Allow at most one optional parameter with familiar, predictable values ("Start [morning/daily/sleep] meditation").
- If information is missing, ask for it, suggesting a likely default plus a short list of alternatives.
- Keep spoken phrases simple; phrase must include the app name; offer natural variants.
- Respond with snippets (static info, confirmation) or Live Activities (ongoing, timer-like).
- Put all critical info in the spoken dialogue for audio-only devices (AirPods, HomePod).
- Make shortcuts discoverable with in-app tips.
- Prefer app schemas for common domains so Apple Intelligence can surface features without individual shortcuts.
- iOS/iPadOS: order by importance (it sets initial order in Spotlight and Shortcuts); choose an SF Symbol or preview image.
- Writing: "App Shortcuts" and "Shortcuts" in title case, plural; individual shortcuts lowercase.
Avoid:
- Long multi-parameter phrases.
Platform notes: Not on macOS (App Intents actions still work in Shortcuts) or tvOS.
Beyond Apple platforms: Parallels Android App Actions/shortcuts and voice assistants; keep invocations short.

## Complications
URL: https://developer.apple.com/design/human-interface-guidelines/complications
Essence: Glanceable app data on the Apple Watch face.
Rules:
- Show essential, dynamic data; static complications get dropped.
- Support all families if possible; otherwise offer an app icon image as a launcher.
- Offer multiple complications per family and a distinct deep link for each.
- Mind privacy: Always-On display can be seen by others.
- Data is a timeline of dated entries; update count is limited, so time entries to when they matter.
- Families: Circular (regular and extra large), Corner, Inline (utilitarian small/large), Rectangular (may appear in Smart Stack); legacy templates for older watchOS (Circular small, Modular small/large, Extra large).
- Gauge styles: closed for percent-of-whole, open for arbitrary ranges, segmented for ranged, fast-changing values.
- Tinted mode desaturates to one color: do not rely on color alone; supply tinted image variants if needed.
- Line widths 2 pt or more.
- Provide static placeholder images per complication.
- Sample sizes (45/49 mm): circular image 50x50 pt, closed gauge 32 pt, open gauge 13 pt; extra large circular image 143x143 pt; corner circular 38 pt; rectangular large image 178.5x56 pt with title, 193x82 pt without. Default text is rounded, medium weight (corner: semibold); circular 14.5 pt, extra large 41 pt, corner 12 pt, rectangular 19.5 pt at 45/49 mm. Per-size tables are in the live page.
Avoid:
- Static or low-information complications; sensitive data on the face.
Platform notes: watchOS only; build with WidgetKit.
Beyond Apple platforms: Comparable to Wear OS tiles/complications.

## Controls
URL: https://developer.apple.com/design/human-interface-guidelines/controls
Essence: Buttons and toggles that surface app features in Control Center, the Lock Screen and the Action button.
Rules:
- Anatomy: symbol, title, optional value; Control Center shows symbol (plus title/value at larger sizes), Lock Screen shows only the symbol.
- Offer actions valuable without launching the app (e.g. start a Live Activity).
- Update state on interaction, completion, or remote push.
- Pick a descriptive symbol; toggles need both on and off symbols (door.garage.open / closed).
- Animate state changes; animate indefinitely during long-running actions.
- Choose a brand tint (applied to the on-state symbol and Dynamic Island).
- Prompt for configuration when added, and allow reconfiguration.
- Provide verb-based hint text for the Action button; provide placeholder title/value for the gallery.
- Redact sensitive title/value when locked; require authentication for security-relevant actions (locks, car start).
- Camera control on locked device: reuse the app's own camera UI, explain how to add it; anything beyond capture requires unlock.
Platform notes: iOS, iPadOS, macOS; not watchOS, tvOS, visionOS.
Beyond Apple platforms: Like Android Quick Settings tiles.

## Live Activities
URL: https://developer.apple.com/design/human-interface-guidelines/live-activities
Essence: Glanceable real-time status for a task or event with a defined start and end.
Rules:
- Use for tasks that begin and end, up to about eight hours; show only the crucial information.
- No ads or promotions; avoid sensitive data (show a neutral summary, or redact).
- Must support four presentations: compact (leading + trailing around the TrueDepth camera, one activity), minimal (up to three; attached plus detached circle/oval), expanded (touch and hold), Lock Screen banner. StandBy uses minimal, scaling the Lock Screen layout 2x.
- Match the app's look in light and dark; logo without container (not the whole app icon); text medium weight or heavier; small text sparingly.
- Limited-width mode (e.g. landscape): fit compact and minimal in a 28 pt circle; leading-only is acceptable.
- Compact: leading and trailing read as one piece of information, narrow, snug to the camera, balanced widths, both link to the same screen.
- Minimal: show live data rather than just a logo if possible.
- Expanded: keep placement consistent with compact; wrap tightly around the camera.
- Lock Screen: standard margin 14 pt; do not copy notification layout; use custom background/tint sparingly with enough contrast, check Always-On reduced luminance and Dark Mode; verify the generated dismiss button color.
- Dynamic island background is black and cannot be customized; color the text and key line; tint the key line to match content.
- Use concentric margins and ContainerRelativeShape; inset container or thick line for separated blocks.
- Vary height dynamically (84-160 pt on Lock Screen) with content.
- Animations max two seconds, none on Always-On reduced; animate layout changes by moving existing elements; avoid overlaps.
- Tapping opens the app at the exact related screen.
- Interactivity: only one simple, essential button or toggle (e.g. pause, contact driver).
- Start at expected moments; give in-app way to turn off; offer an App Shortcut to start.
- Update only when content changes; alert only for essential updates; do not duplicate with push notifications; prefer one Live Activity cycling through events.
- End immediately when the task ends; remains on Lock Screen, Mac menu bar and Smart Stack up to four hours; set a custom dismissal time (15 to 30 minutes is typical).
- StandBy: default background, standard margins, verify Night Mode (red tint).
- CarPlay: system merges compact elements; interactive elements are disabled, so prefer information over buttons. Sizes 240x78, 240x100, 170x78 pt.
- watchOS: appears at the top of the Smart Stack combining compact elements; consider a custom layout; if shared with CarPlay, avoid buttons. Smart Stack sizes: 152x69.5 (40 mm) to 198x81.5 pt (49 mm Ultra 3/4).
- macOS: appears in the menu bar; click launches iPhone Mirroring.
- iOS sizes (393x852 screen): compact 52.33x36.67, expanded 371x84-160, minimal 36.67-45x36.67 pt; 430x932 screen: compact 62.33x36.67, 408 wide.
Avoid:
- Unexpected starts, too many alerts, dense text, edge-to-edge graphics in StandBy.
Platform notes: Not tvOS, visionOS.
Beyond Apple platforms: Android ongoing/foreground-service notifications and live notifications; keep to one glanceable state.

## Notifications
URL: https://developer.apple.com/design/human-interface-guidelines/notifications
Essence: Timely, high-value, glanceable messages that require permission.
Rules:
- Be concise and valuable; do not repeat a notification for the same thing.
- Do not tell users to perform in-app tasks; provide notification actions instead.
- Use alerts, not notifications, for errors.
- In the foreground, update quietly (badge, insert in list) rather than interrupt.
- Keep sensitive info out; write generic fallback body text for hidden previews ("New comment", "Reminder"; sentence case).
- Title: short, title-style, no ending punctuation; skip a generic title and let the system show the app name. Body: complete sentences, sentence case, proper punctuation, no manual truncation.
- Do not include your app name or icon (system adds them).
- Sounds: short, distinctive, professional, never the only carrier of important info.
- Actions: up to four buttons, short title-case labels without app name; no "Open app" action; prefer non-destructive (destructive gets distinct styling); add simple icons (trailing side).
- Badges: only for unread notification count; keep current (zero count clears Notification Center); never the only channel; never imitate a badge.
- watchOS: short look (brief, privacy-aware, not the only channel); long look (scrollable, static required and dynamic preferred, sash with app icon, optional content background of white at 18 % opacity, up to four custom actions, system Dismiss button at bottom); double tap triggers the first non-destructive action, so order actions by likelihood.
Avoid:
- Marketing noise, duplicate nags, sensitive content, badges for non-notification numbers (scores, prices).
Platform notes: Communication notifications show a contact avatar badged with the app icon.
Beyond Apple platforms: Same principles for Android and web push: ask permission in context, concise copy, actions, no spam.

## Snippets
URL: https://developer.apple.com/design/human-interface-guidelines/snippets
Essence: Compact views in Siri, Spotlight or Shortcuts that confirm an action or show its result.
Rules:
- Two types: confirmation (system Cancel secondary plus customizable primary) and result (system Done); confirmation is optional.
- Anatomy: spoken dialogue (above the view), custom view, system buttons.
- Check contrast and consistent margins in light and dark.
- Custom view height at most 400 pt; remember text-size settings; deep-link for more detail.
- Primary label should be specific ("Order", not OK/Proceed; default is Continue).
- Convey purpose visually; omit dialogue text from the visual view.
Platform notes: iOS, iPadOS, macOS.
Beyond Apple platforms: Like Assistant cards or quick-reply dialogs: one outcome, one clear confirm.

## Status bars
URL: https://developer.apple.com/design/human-interface-guidelines/status-bars
Essence: iOS/iPadOS top strip showing time, carrier, battery.
Rules:
- Its background is transparent; make it readable by blurring content behind it (scroll edge effect) and do not let controls show behind it as if tappable.
- Hide temporarily for full-screen media; always give a discoverable way (tap) to show it again.
Avoid:
- Permanently hiding it.
Platform notes: iOS and iPadOS only.
Beyond Apple platforms: Android/web: handle safe-area insets and keep system bars legible with scrim/blur.

## Top Shelf
URL: https://developer.apple.com/design/human-interface-guidelines/top-shelf
Essence: tvOS Home Screen area where an app in the Dock showcases content.
Rules:
- Feature new, personalized content and let people resume; carousel layouts have a primary Play and a More Info button.
- Avoid ads and prices.
- Prefer dynamic layered imagery; always supply a static fallback image of 2320x720 pt (@1x) / 4640x1440 (@2x); do not imply it is interactive.
- Layouts: carousel actions (title, optional subtitle), carousel details (title plus attribution and metadata), sectioned content row (fill the screen width, at least one label; images poster 2:3 404x608, square 608x608, 16:9 908x512 pt actual size; mixed sizes scale to the tallest), scrolling inset banner (3 to 8 images of 1940x692 pt, text baked into the image and added to the accessibility label).
Platform notes: tvOS only.
Beyond Apple platforms: Apple-only (TV home hero rows are the analogue on Android TV).

## Watch faces
URL: https://developer.apple.com/design/human-interface-guidelines/watch-faces
Essence: The primary watchOS view; apps can share preconfigured faces featuring their complications.
Rules:
- Share watch faces featuring your complications to drive installs; the system prompts installing the app if missing.
- Provide a preview (illustrated or hardware bezel).
- Offer faces for all devices; some faces need Series 4+ (Explorer: Series 3 cellular and later), so offer a compatible alternative and label supported devices.
- If a user picks an incompatible face, fall back to an alternative instead of an error.
Platform notes: watchOS only.
Beyond Apple platforms: Apple-only.

## Widgets
URL: https://developer.apple.com/design/human-interface-guidelines/widgets
Essence: Glanceable, periodically updated app content and light interaction on Home Screen, Lock Screen, desktop, Smart Stack, StandBy and visionOS surfaces.
Rules:
- Pick a simple idea tied to the app's main purpose; offer timely, changing content and deep links; do not replicate the app icon.
- Offer sizes only where useful; do not just stretch content; keep the primary purpose the same across sizes; one description for all sizes.
- Balance density: glanceable first, detail on longer look.
- Brand through color/typeface/glyph, small logo (top right) only if needed.
- Choose between auto content and user configuration; hint sign-in if authentication adds value.
- Do not mirror widget appearance inside the app.
- Updates are periodic, not real time; show "last updated" if useful; let the system refresh dates/times; use animation up to two seconds. Use Live Activities for real-time.
- Interactivity: buttons and toggles only for simple actions; other taps open the app at the relevant place; avoid app-like layouts; inline accessory widgets have one tap target.
- Margins: 16 pt standard, 11 pt tighter groups; smaller on Mac desktop and Lock Screen; use ContainerRelativeShape for corner radius.
- Text: system font and SF Symbols; no text below 11 pt; never rasterize text; Dynamic Type Large to AX5.
- Color: do not rely on color alone; tinted/clear appearances desaturate images, so use full-color images sparingly (e.g. album art, smaller than the widget).
- Rendering modes: full color (support light and dark, semantic colors), accented (group views into accent and primary groups), vibrant (Lock Screen: opaque grayscale; white/light gray for primary; check contrast incl. Always-On).
- Provide realistic gallery preview, placeholder made of semi-opaque shapes, description starting with an action verb (no "This widget..."); optionally color the Add button.
- Accessory styles: inline (above clock), circular, rectangular; treat like complications; support Always-On.
- StandBy/CarPlay: small widget scaled up with background removable; large type, little color/imagery; low-light red tint.
- Apple HomeView: small widgets; Modular face up to four widgets; per-person Home Screen.
- visionOS: persistent 3D objects; design two proximity thresholds (simplified with larger type and no buttons when distant; detailed nearby); scale 75-125 %; mounting elevated (default) or recessed (vertical only); paper vs glass treatment; test all tint palettes and frame widths.
- watchOS: colorful meaningful background (default black), supply relevance info so the system raises it in Smart Stack.
- Key sizes (pt): iPhone 393x852 screen small 158x158, medium 338x158, large 338x354, circular 72, rectangular 160x72, inline 234x26; visionOS small 158x158, medium 338x158, large 338x354, XL 450x338; Smart Stack 152x69.5 to 198x81.5. Full iPad tables in the live page.
Avoid:
- Tiny fonts, dense app-like UIs, static content, color-only meaning.
Platform notes: Not on tvOS.
Beyond Apple platforms: Android App Widgets/Glance and web dashboards: glanceable, deep-linking, limited refresh.
