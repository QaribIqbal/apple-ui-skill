# Inputs — HIG digest
Source pages: 13. Digest written 2026-10-22. Live pages are authoritative when in doubt.

## Action button
URL: https://developer.apple.com/design/human-interface-guidelines/action-button
Essence: A hardware button on supported iPhone and Apple Watch Ultra that runs a user-chosen function or App Shortcut.
Rules:
- Expose your app's essential functions as App Shortcuts (e.g. "Start Egg Timer"); do not offer a plain "open app" action, the system already does.
- Action labels: title-style capitalization, begin with a verb, present tense, no articles or prepositions, at most three words ("Start Race", not "Started Race" or "Start the Race").
- Let the system teach setup; do not duplicate Settings guidance in your own content.
- iOS: complete the action without leaving context where possible, via Live Activities or snippets (Set Timer asks for a duration then starts a Live Activity).
- watchOS: first press can start a workout, waypoint or dive; add at most one simple secondary function (mark segment, next modality) because people press without looking.
- Use later presses to advance, not to stop; keep stopping in the UI.
- Pressing Action plus side button should pause the current activity, except in diving apps where pausing is unsafe.
Avoid:
- Multiple secondary functions; repeating system tips.
Platform notes: iPhone and Apple Watch Ultra only; not iPadOS, macOS, tvOS, visionOS.
Beyond Apple platforms: Apple-only hardware; the lesson is to offer short, verb-first quick actions for hardware shortcuts.

## Apple Pencil and Scribble
URL: https://developer.apple.com/design/human-interface-guidelines/apple-pencil-and-scribble
Essence: Precise stylus input for iPad: drawing, marking, hover, gestures, and handwriting-to-text with Scribble.
Rules:
- Support real-world marking habits (writing in margins); a mark appears the instant the tip touches, with no mode or button needed first.
- All controls must respond to Pencil as well as finger, or they seem broken.
- Use tilt (altitude), pressure, azimuth and barrel roll for strokes; map pressure to continuous properties such as opacity or brush size.
- Show immediate, direct visual feedback on the content touched.
- Design for left and right hands; keep controls out of hand-covered zones or let users move them.
- Hover: preview the mark (size, color) before touching; do not change the preview with height; show a mid-range value for dynamic properties; never start an action on hover (especially destructive); consider showing a contextual tool-size menu near the tip; show hover previews for Pencil only, not for pointers.
- Double tap: honor the user's system setting (switch to eraser, previous tool, color picker, off); custom behavior must be opt-in with a visible mode control; do not modify content or destroy data with it.
- Squeeze (Pencil Pro): single, quick, discrete action; show resulting UI (e.g. a menu) near the tip; keep it nondestructive and undoable; users may map it to an App Shortcut.
- Barrel roll: change mark characteristics only (e.g. highlighter angle), never navigation or controls.
- Scribble: works in all standard text fields (not password fields); do not require tapping a custom field first; make it available wherever text feels natural (e.g. blank area below a Reminders list).
- While writing: no autocomplete suggestions, hide placeholder as soon as writing starts, keep the field stationary and un-autoscrolled, enlarge the field before or after (not during) writing.
- PencilKit: for drawing over PDFs/photos turn off dynamic Dark Mode color adjustment; in compact layouts add undo/redo buttons and support the 3-finger undo/redo gesture.
Avoid:
- Hover-triggered actions, double-tap or squeeze actions that can lose data, resizing fields mid-stroke.
Platform notes: iPadOS only.
Beyond Apple platforms: Stylus/pen apps on any platform should draw on contact, support pressure/tilt, never act on hover, and keep pen shortcuts undoable.

## Camera Control
URL: https://developer.apple.com/design/human-interface-guidelines/camera-control
Essence: iPhone 16 hardware control (press and slide) that opens a camera app and adjusts capture parameters via an overlay.
Rules:
- Two control types: slider (range, e.g. contrast) and picker (discrete options, e.g. grid on/off); system also offers standard zoom and exposure controls.
- Use SF Symbols only (custom symbols are unsupported); a symbol cannot show current state.
- Keep control names short (they follow Dynamic Type).
- Add units or symbols to slider values (EV, %).
- Define prominent values so sliding snaps to common or evenly spaced values (zoom steps).
- Keep your own UI out of the overlay areas in both orientations; maximize the viewfinder; do not duplicate controls the overlay is showing.
- Enable or disable controls by mode (e.g. disable video controls in photo mode); controls cannot be added or removed at runtime.
- Order common controls toward the middle; the system remembers the last used control.
- Provide a locked camera capture extension so it launches from lock, Home Screen or other apps.
Platform notes: iPhone 16 family only.
Beyond Apple platforms: Apple-only; general lesson is to leave the viewfinder uncluttered and avoid duplicate controls.

## Digital Crown
URL: https://developer.apple.com/design/human-interface-guidelines/digital-crown
Essence: Rotary hardware input on Apple Watch (primary navigation) and Apple Vision Pro (system functions).
Rules:
- Vision Pro: system uses it for volume, immersion level, recenter, accessibility, exit to Home View; apps do not receive crown data.
- Apple Watch (watchOS 10+): crown is the main navigation input: scroll lists, switch vertical tabs, move through the Smart Stack and Home Screen.
- Anchor navigation to vertical list, tab and scroll views, and always back it up with touch.
- Use it to inspect data when navigation is not needed (World Clock advancing the time).
- Always give visual feedback when the crown turns; otherwise users assume it does nothing.
- Match the rate of change to the turning speed; avoid values scrolling too fast to land on.
- Keep default linear haptic detents when they suit; disable them if they clash with animation; use linear instead of row-based detents when row heights vary a lot.
- Crown presses are reserved by the system.
Platform notes: Apple Watch and Vision Pro only.
Beyond Apple platforms: Same logic for rotary bezels on Wear OS: tie rotation to scroll/value, with visible feedback and haptic detents.

## Eyes
URL: https://developer.apple.com/design/human-interface-guidelines/eyes
Essence: In visionOS people look at an element to target it; the system shows a hover effect and a pinch selects it.
Rules:
- Gaze data is private: apps are told only when the user taps, not where they looked.
- Always provide alternative interactions (accessibility features).
- Keep needed content in the field of view; avoid forcing quick eye shifts across large areas or depths; place reading content at least 1 m away.
- Prefer standard components, which give consistent hover feedback.
- Give targets space: at least 16 pt margin around each, or centers at least 60 pt apart.
- Minimize clutter and movement near targets; do not reveal new content next to something being looked at; do not fill the view with a repeating pattern or texture.
- Use gentle cues (centering, contrast, scale, subtle motion) to draw attention to the likely target.
- Make interactive shapes rounded (eyes drift to corners); for multi-part components provide one containing shape so the whole region highlights.
- Custom hover effects: two states defined ahead of time, executed out of process (cannot run code or trigger actions); use sparingly for special moments; delay choice: none for subtle/inviting, short for quick-use expansion (tab bar), longer for extra info (tooltip); keep at least one primary view unchanged for stability; test on a device.
Avoid:
- Too many custom hover effects, crowding targets, movement that steals gaze.
Platform notes: visionOS only; unrelated to the keyboard/controller focus system.
Beyond Apple platforms: Gaze-based AR/VR UIs elsewhere benefit from the same spacing (about 60 pt) and rounded-target rules.

## Focus and selection
URL: https://developer.apple.com/design/human-interface-guidelines/focus-and-selection
Essence: How keyboards, remotes and controllers show and move the "current target" across the interface.
Rules:
- Focus shows which item an interaction targets; focusing sometimes also selects, but not when selection would cause a disruptive context change (tvOS: selecting opens or activates).
- Use system focus effects; make custom ones only when unavoidable.
- Never move focus without user action. Exception: with discrete directional input (keyboard, remote, controller) when the focused item vanishes, move focus to a nearby remaining item; with other input, hide the indicator.
- iPadOS/macOS: full keyboard access reaches controls, so support focus only for content elements (list items, text and search fields); tvOS needs every element focusable.
- Use a focus ring for text and search fields, a row/cell highlight in lists and collections (accent-colored background with white text when focused, gray when unfocused).
- iPadOS: focus groups (sidebar, grid, list); Tab moves between groups in reading order (leading to trailing, top to bottom), arrow keys move within a group; halo effect (ring) customizable to rounded or Bezier shapes; set group identifiers and priority so the primary item gets focus first.
- tvOS: in full-screen content, gestures act on the content, not focus; avoid a pointer; design for up to five item states (unfocused, focused, pressed/chosen, selected, unavailable) and supply sharp assets for the enlarged focused size without crowding neighbors.
- visionOS: same focus system for keyboards and controllers; gaze uses the separate hover effect.
Avoid:
- Surprise focus jumps; pointers on TV (unless gameplay needs it).
Platform notes: Not iOS or watchOS.
Beyond Apple platforms: On web/Flutter, always show a visible focus ring for keyboard users, keep tab order logical, and never steal focus unprompted.

## Game controls
URL: https://developer.apple.com/design/human-interface-guidelines/game-controls
Essence: Supporting touch, game controllers and keyboard/mouse for games on every Apple platform.
Rules:
- Always support the platform's default input; treat controllers as optional (unless you mark the game controller-required in tvOS/visionOS, and then detect and prompt gracefully).
- Touch: only overlay virtual controls when needed; prefer direct tapping on game objects; keep frequent controls at least 44x44 pt and secondary controls (menus) at least 28x28 pt; place near thumbs, away from Home indicator and Dynamic Island; menus at top.
- Controls need visible plus haptic/sound press feedback visible even under a finger.
- Use meaningful action symbols, not "A/X/R1"; show or hide controls contextually; merge multi-button combos into gestures (double tap, hold).
- Movement left side (floating thumbstick where the thumb lands), camera right side by direct pan.
- Controllers: auto-detect pairing, label with the connected controller's real glyphs (prefer SF Symbols over text), support multiple controllers.
- UI mapping: A activates; B cancels/back; shoulders switch screens/sections; sticks and D-pad move selection; Home reserved for system; Menu opens settings or pauses.
- Keyboard: prefer single-key bindings (I = Inventory, Space = main action); consider key proximity to WASD; test with Apple keyboards (Command sits by Space); let players rebind keys.
- visionOS: spatial controllers mimic hands (look + trigger for indirect, reach + trigger for direct).
Avoid:
- Abstract button art, clumsy multi-button sequences, overlapping system UI.
Platform notes: Not watchOS.
Beyond Apple platforms: Same touch targets, press feedback, rebindable keys and glyph matching apply to Android/Unity games.

## Gestures
URL: https://developer.apple.com/design/human-interface-guidelines/gestures
Essence: Direct-manipulation motions (touch, air, trackpad) and which ones people expect.
Rules:
- Offer more than one way to do things (voice, keyboard, Switch Control); never make a gesture the only path.
- Keep standard gestures meaning what users expect; do not reuse tap or swipe for app-unique actions, and do not invent gestures for standard actions like scrolling.
- Respond instantly and show progress/extent while the gesture runs.
- Explain when a gesture is unavailable (locked object, disabled button).
- Custom gestures only for specialized, frequent tasks; must be discoverable, easy, distinct, and not the only route; teach them; do not collide with system gestures (edge swipes, visionOS palm roll).
- Shortcut gestures supplement visible controls (swipe back plus Back button).
- Standard set: tap (activate), swipe (scroll, reveal, dismiss), drag (move), touch-and-hold (more controls), double tap (zoom or primary action on watch), zoom, rotate.
- iOS/iPadOS extras: three-finger swipe left/right = undo/redo; three-finger pinch = copy/paste; four-finger swipe (iPad) = switch apps; shake = undo/redo. Allow simultaneous gestures mainly in games.
- visionOS: indirect gestures (look + pinch) preferred for UI; direct touch for nearby, infrequent use; avoid requiring specific body movements or a specific hand; custom gestures need Full Space and hand-tracking permission, must be ergonomic; keep content away from the palm area that triggers system overlays; avoid wrist-roll gestures.
- watchOS double tap: scrolls lists, advances tabs, or runs a declared primary action (pick the most common button; do not set one in scrolling views).
Avoid:
- Conflicting with system gestures, hidden-only gestures.
Platform notes: Gesture availability varies; see the supported-in table for each platform.
Beyond Apple platforms: Mobile web/Flutter: never rely on swipe-only actions; provide visible buttons; avoid overriding edge-back and system gestures.

## Gyroscope and accelerometer
URL: https://developer.apple.com/design/human-interface-guidelines/gyro-and-accelerometer
Essence: Motion sensor data for iOS, iPadOS, watchOS (and Siri Remote gyro on tvOS).
Rules:
- Use motion data only when it gives a clear benefit (fitness feedback, gameplay).
- Provide a purpose string explaining why you need access; it appears in the first permission prompt.
- Outside active gameplay, avoid motion-based direct manipulation of the UI: hard to repeat, physically difficult for some, battery draining.
Avoid:
- Collecting data without benefit.
Platform notes: none beyond the above.
Beyond Apple platforms: Android/web sensor APIs have the same expectations: justify, request permission in context, don't depend on tilt for core UI.

## Keyboards
URL: https://developer.apple.com/design/human-interface-guidelines/keyboards
Essence: Physical keyboard support, shortcuts and key bindings.
Rules:
- Support Full Keyboard Access (iOS, iPadOS, macOS, visionOS) so every control can be reached and activated by keyboard; on iPadOS, rely on it for buttons, segmented controls and switches rather than adding custom keyboard navigation to controls.
- Do not repurpose standard shortcuts; only repurpose when the action makes no sense in your app (e.g. Command-I for Get Info if no italic).
- Essential standard shortcuts: Command-C/X/V (copy/cut/paste), Z (undo), Shift-Command-Z (redo), A (select all), S (save), P (print), N (new), O (open), W (close), Q (quit), F (find), G / Shift-G (find next/previous), B/I/U (bold/italic/underline), H (hide), M (minimize), Comma (Settings), Question mark (Help), Period (cancel), Tab / Shift-Tab (forward/back through controls), Esc (cancel), Command-Tab (app switch), Command-Space (Spotlight), Shift-Command-3/4 (screenshots).
- Custom shortcuts only for the most frequent app-specific commands.
- Modifiers: Command first choice; Shift as a secondary variant of a related shortcut; Option sparingly for power features; avoid Control (system uses it).
- List modifiers in order Control, Option, Shift, Command.
- Do not add Shift when the character already sits on the shifted position (Command-Question mark, not Shift-Command-Slash); avoid modifier use on characters missing from some keyboards.
- Let the system localize and mirror shortcuts for other keyboards and RTL layouts.
- Do not make a new shortcut by adding a modifier to an unrelated existing one.
- Modifier conventions: Command-drag moves as a group, Shift-resize keeps aspect ratio, holding an arrow nudges by the smallest unit.
- visionOS: holding Command shows a flat shortcut list by category, so give titles that stand alone without submenu context; a keyboard overlay appears while typing.
Avoid:
- Many custom shortcuts, Control-based shortcuts, hijacked standard shortcuts.
Platform notes: Not watchOS.
Beyond Apple platforms: On web, honor Ctrl in place of Command (Ctrl-C/V/Z/S/F), don't override browser shortcuts, and make everything operable by Tab/Enter/Esc.

## Nearby interactions
URL: https://developer.apple.com/design/human-interface-guidelines/nearby-interactions
Essence: Ultra Wideband-based features that use distance and direction to nearby devices.
Rules:
- Draw inspiration from physical-world actions (bring devices together to transfer audio).
- Use distance, direction and context to drive behavior (suggest the nearest facing contact).
- Change feedback with proximity (arrow becomes pulsing circle) and keep it continuous.
- Combine visual, audio and haptic feedback depending on whether the user is looking at the screen.
- Never make it the only way to do a task.
- Hold the phone in portrait for best accuracy, conveyed implicitly with visuals rather than text if possible.
- Design for the sensor's field of view (like the Ultra Wide camera); outside it you may get distance but no direction.
- Warn that people, pets or large objects between devices reduce accuracy.
- iOS gives distance and direction; watchOS only distance and requires foreground.
Platform notes: Not macOS, tvOS, visionOS.
Beyond Apple platforms: Android UWB/Nearby Share and BLE proximity features follow the same pattern: permission, graceful fallback.

## Pointing devices
URL: https://developer.apple.com/design/human-interface-guidelines/pointing-devices
Essence: Mouse and trackpad behavior, especially pointer adaptation on iPadOS and standard Mac gestures.
Rules:
- Be consistent with system trackpad/mouse gestures; do not redefine systemwide ones (Mission Control, Dock reveal).
- Keep behavior consistent across touch, pointer, keyboard and eyes; modifier-key results (e.g. Option-drag duplicates) must match across inputs.
- Let the pointer reveal and hide auto-minimizing controls (Safari toolbar, video controls).
- iPadOS pointer: default is a circle; I-beam over text; content effects: highlight (small, transparent-background elements; translucent rounded rect with gentle parallax; default on bar buttons, tab bars, segmented controls), lift (small, opaque elements; scales up with shadow; app icons), hover (large elements; custom scale/tint/shadow; does not morph pointer, no magnetism).
- Pointer magnetism pulls toward hit regions and along flick trajectories; apply to lift and highlight elements only.
- Hit regions: add about 12 pt padding around bezeled elements, about 24 pt around elements without a bezel; make custom bar button hit regions contiguous; give nonstandard shapes a corner radius for lift.
- Prefer system pointer effects for custom elements that act like standard ones; use them consistently; avoid decorative effects; keep custom shapes simple; use annotations (X/Y, size) instead of instructional text; use scale only where neighbors will not collide, never shadow without scale.
- Pointer accessories (e.g. resize arrows, plus becoming circle.slash) are small, simple and can signal state changes.
- Support band (rubber-band) multi-select in custom views; differentiate pointer vs finger only when useful (precise scrub clicks).
- macOS: primary/secondary click, scroll, smart zoom, swipe between pages, Mission Control, force click lookup, pinch zoom, rotate, App Exposé, Launchpad, Show Desktop; users can customize these; standard cursors: arrow, I-beam, pointing hand (links), open/closed hand (drag content), crosshair, resize arrows, drag copy (Option), drag link (Option-Command), operation not allowed, contextual menu (Control).
- visionOS: pointer context follows where eyes look; pointer hides while gesturing.
Avoid:
- Overriding system gestures, gratuitous pointer effects, hit regions too tight or too loose.
Platform notes: Not tvOS or watchOS; iOS has no special notes.
Beyond Apple platforms: Web/desktop: use pointer cursor on links, text cursor on text, hover states with generous hit areas, and don't hijack system gestures.

## Remotes
URL: https://developer.apple.com/design/human-interface-guidelines/remotes
Essence: Siri Remote (clickpad, touch surface, buttons) as the primary tvOS input.
Rules:
- Use standard gestures for standard actions; custom gestures mainly in gameplay.
- Move focus in the same direction as the swipe; give feedback that shows what a gesture will do.
- Swipe scrolls with momentum; press activates; press-then-swipe scrubs.
- Distinguish press from tap; ignore accidental taps during live video; use positional taps (up/down/left/right) only when intuitive.
- Back: go to the parent screen (top level returns to Home Screen); long press goes Home. In gameplay Back opens a pause menu, and pressing Back again closes it.
- Play/Pause toggles media playback (secondary button in games).
- Touch surface in games: swipe = D-pad, press = primary button.
- Compatible remotes: guide/browse button opens your EPG, page up/down navigates it while open; while content plays, page up/down changes channel; otherwise system routes to default guide app.
Platform notes: tvOS only.
Beyond Apple platforms: TV UIs on any platform: directional (D-pad) focus navigation, predictable Back, big focus states.
