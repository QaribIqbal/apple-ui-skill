# Patterns — HIG digest
Source pages: 25. Digest written 2026-10-22. Live pages are authoritative when in doubt.

## Charting data
URL: https://developer.apple.com/design/human-interface-guidelines/charting-data
Essence: When and how to present data as a chart so people can read trends and comparisons quickly.
Rules:
- Use a chart only to highlight something about a dataset; if people merely need the data, offer a scrollable, searchable, sortable list or table instead.
- Keep each chart simple; reveal extra detail on demand (different levels of detail, subsets, or progressively richer versions of the chart).
- Prefer familiar chart types (bar, line); if a chart type is novel, teach how to read it (e.g. animate each ring in turn).
- Add descriptive text (title, subtitle, annotations, a one-line headline summary) to surface the takeaway.
- Provide accessibility labels for values and components plus accessible elements for interaction; a headline never replaces labels.
- Size the chart to its job: large enough for labels and interaction, small for glanceable previews.
- Stay consistent across charts with a similar purpose; when several charts show the same dataset, keep type, colors, marks and annotations identical (small preview and expanded version should match).
Avoid:
- Cramming in as much data as possible; inventing a different style per chart.
Platform notes: none.
Beyond Apple platforms: Fully applies to any web/Flutter/Android dashboard.

## Collaboration and sharing
URL: https://developer.apple.com/design/human-interface-guidelines/collaboration-and-sharing
Essence: Use system sharing surfaces and a Collaboration button so sharing and co-editing feel simple and familiar.
Rules:
- Put the Share button somewhere easy to reach, such as a toolbar; use the system share sheet/popover (or ShareLink in SwiftUI).
- Summarize sharing permissions in a short phrase ("Only invited people can edit", "Everyone can make changes").
- Offer few, grouped sharing options: who can access, edit vs read-only, whether collaborators can add people.
- Show the Collaboration button as soon as collaboration starts, next to Share.
- The collaboration popover has three sections (people and message/call buttons, your custom items, manage button); add custom items only when essential.
- Allow customizing the "Manage Shared File" button title.
- Consider notifying through Messages (changes, joins/leaves, mentions) with a universal link into the right view.
Avoid:
- Overloading the collaboration popover.
Platform notes: visionOS pauses screen sharing for others while the sharer is in a Full Space. watchOS uses ShareLink.
Beyond Apple platforms: Pattern (one share entry point, plain-language permissions, deep links in notifications) carries over to any app.

## Drag and drop
URL: https://developer.apple.com/design/human-interface-guidelines/drag-and-drop
Essence: Let people move or copy content between locations by dragging, with continuous feedback.
Rules:
- Support drag and drop broadly; system text controls give it for free.
- Always offer an alternative (menu commands for copy/move, accessibility drag/drop descriptors).
- Default: drop within the same container moves, different container copies, between apps always copies; holding Option at drop forces a copy in the same container.
- Support multi-item drag; show a count badge on macOS and flocking on iPad.
- Make drags undoable, or confirm first when irreversible.
- Show a translucent drag image once the drag exceeds about 3 pt; keep it until drop; do not let it change radically or constantly.
- Highlight only valid destinations and only while hovering; show "not allowed" otherwise; on failed drop animate back to source or fade out.
- Auto-scroll destinations; offer multiple fidelity versions (vector, then lossless PNG, then JPEG) and accept the richest one; extract only the relevant part of dropped data.
- Show progress or a placeholder for slow transfers; keep dropped content selected; match source text style or adopt destination style.
- Spring loading: dragging over buttons/segments can activate them.
Avoid:
- Showing destination highlight when the drop is not allowed; hiding the result of a drop.
Platform notes: macOS - allow dragging from inactive windows without activating them, and drag to Finder in a reopenable format; iPadOS - add items to an in-progress drag; visionOS - dropping in empty space can launch an app.
Beyond Apple platforms: Same logic for web/desktop; always give a non-drag path.

## Entering data
URL: https://developer.apple.com/design/human-interface-guidelines/entering-data
Essence: Reduce typing and errors when collecting information.
Rules:
- Gather data from the system or with permission instead of asking (settings, location, calendar).
- Label fields clearly (a prompt such as "username@company.com" or a label "Email") and prefill sensible defaults.
- Use secure entry fields (filled dots) for sensitive data; never prepopulate a password field.
- Prefer pickers, menus or other selection over free text when options are finite.
- Accept paste and drag and drop.
- Validate as the person types or leaves a field and give immediate feedback; use number formatters for numbers (decimals, percent, currency).
- Disable Next/Continue until required data is provided, and make requirements clear.
Avoid:
- Making people fix mistakes after a long form; asking for what you can detect.
Platform notes: macOS - expansion tooltip shows clipped field text.
Beyond Apple platforms: Directly applicable to any form (inline validation, input types, defaults).

## Feedback
URL: https://developer.apple.com/design/human-interface-guidelines/feedback
Essence: Tell people status, results, warnings and chances to correct, scaled to importance.
Rules:
- Match delivery to significance: passive status inline; critical warnings interrupt.
- Combine channels (color, text, sound, haptics) so feedback works for everyone including VoiceOver users.
- Put status near the item it describes (e.g. unread count in the toolbar) so no navigation is needed.
- Reserve alerts for critical, ideally actionable information; overuse dilutes them.
- Warn before unexpected, irreversible data loss; do not warn when loss is the expected result (deleting a file in a file manager).
- Confirm completion only for important tasks (payments); people expect success, so tell them mostly about failure.
- When a command cannot run, say so and explain why.
Avoid:
- Frequent alerts for trivial info.
Platform notes: watchOS - avoid indeterminate progress indicators; promise a notification on completion instead.
Beyond Apple platforms: Universal; toasts/snackbars for passive success, dialogs only for blocking issues.

## File management
URL: https://developer.apple.com/design/human-interface-guidelines/file-management
Essence: Creating, opening, saving and previewing documents in document-based apps.
Rules:
- Provide New/Open commands with keyboard shortcuts (iPadOS/macOS) and an Add (+) button; on macOS put them in the File menu.
- A custom file browser should respect the platform file system model and allow browsing beyond the starting folder.
- Autosave periodically, on close and on app switch; do not require an explicit Save.
- Hide file extensions by default, reflecting the user's choice everywhere.
- Use Quick Look to preview files you cannot open; provide a generator for custom file types.
- iOS 18 document launcher: title card with two buttons (primary usually creates a document), a distinct simple background, accessories that never hide the title or buttons, gentle sparse animation.
- File provider extensions: list only relevant files, let people pick export destination, do not add a second toolbar.
- macOS: use the default panel; customize the Open button title (e.g. Insert), Save panel for name/format/location, default "Untitled" name. If autosave is off, show unsaved state with a dot in the close button and Window menu and prompt on close/quit.
Avoid:
- Custom file UIs without a strong reason.
Platform notes: Not applicable on tvOS/watchOS.
Beyond Apple platforms: Autosave-by-default and "recent files" apply to web/Flutter editors.

## Going full screen
URL: https://developer.apple.com/design/human-interface-guidelines/going-full-screen
Essence: Optional distraction-free mode for games, media and focused tasks.
Rules:
- Offer full screen when it helps concentration (games, video, slideshows, deep work).
- Adapt layout subtly; never resize the window programmatically.
- Keep essential controls available or easily revealed; hide toolbars only when content is the focus and restore them by tap, swipe down or cursor to top.
- Let the Dock be revealed on iPadOS/macOS except in games.
- Pause games/slideshows when people switch away and resume on return.
- Let the person choose when to exit.
- iOS: keep the Home indicator auto-hide default; defer system gestures (two swipes) only if accidental exits occur.
- macOS: use system full screen (handles camera notch); do not change display mode; entry via the green button, View menu or Control-Command-F; no custom window-mode menus.
Avoid:
- Auto-exiting full screen; jarring layout jumps.
Platform notes: Not on tvOS/visionOS/watchOS.
Beyond Apple platforms: Same for web Fullscreen API and kiosk/immersive modes.

## Launching
URL: https://developer.apple.com/design/human-interface-guidelines/launching
Essence: Start instantly and land the user where they left off.
Rules:
- Launch in a couple of seconds at most; restore previous state (scroll position, windows).
- Launch screen (iOS/iPadOS/tvOS) must look almost identical to the first screen, match orientation and appearance mode, or be only the solid color the app shows first.
- Put a splash screen, if any, at the start of onboarding, not at launch.
- iOS: launch in current orientation if both are supported.
- tvOS live apps: start playback after a few seconds idle.
Avoid:
- Text, logos, branding, ads on the launch screen (text is not localized).
Platform notes: visionOS - consider launching a Shared Space window even for immersive apps.
Beyond Apple platforms: Use skeleton/first-frame placeholders matching the first screen; avoid splash delays.

## Live-viewing apps
URL: https://developer.apple.com/design/human-interface-guidelines/live-viewing-apps
Essence: Make live content the star and quick to start.
Rules:
- Live content in first tab, one tap (or zero) to play; a Watch Now button that vanishes on press.
- Mark live items distinctly from on-demand (badge, sash, "Live" row); show progress of in-progress content.
- Playback is the primary action; keep other actions (Start Over, Record, Favorite) in a fixed order.
- Content footer for channel browsing: subtle darkening, badge current item, categories match the guide, symmetrical invoke/dismiss gestures.
- Instant visual feedback on channel change; audio stops when leaving the live tab.
- EPG: show current program and a quick return; support paging and My Channels/Favorites; familiar categories; keep playing (PiP) while browsing.
- Cloud DVR: record from the info panel, choose episode vs series, filters, play/delete in DVR area, automatic storage management.
Avoid: Burying live content.
Platform notes: none.
Beyond Apple platforms: Applies to streaming apps on any platform.

## Loading
URL: https://developer.apple.com/design/human-interface-guidelines/loading
Essence: Loading should finish before the person notices; otherwise show progress gracefully.
Rules:
- Show something immediately (placeholder text, graphics) and swap in real content.
- Load in the background so people can keep using the app.
- For long loads, show tips or hints and estimate duration to avoid repeating them.
- Download large assets in the background after install or during updates.
- Use determinate progress when duration is known, indeterminate otherwise; games may use custom loading views.
Avoid: A blank screen while waiting; watchOS loading indicators except for a second or two.
Platform notes: watchOS - show content immediately; a brief indicator beats a blank screen.
Beyond Apple platforms: Use skeleton screens and optimistic UI on web/mobile.

## Managing accounts
URL: https://developer.apple.com/design/human-interface-guidelines/managing-accounts
Essence: Ask for accounts only when needed and make sign-in and deletion painless.
Rules:
- Require an account only if core functionality needs it; delay sign-in as long as possible (let people browse first).
- Explain benefits on the sign-in screen; offer Sign in with Apple or passkeys; passwords require two-factor.
- Name the authentication method precisely ("Sign In with Face ID"); reference only methods available on the device.
- No in-app biometric opt-in toggle (it is a system setting); do not call account authentication a "passcode".
- If accounts can be created in-app, provide in-app deletion (not just deactivation) or a direct, discoverable link; keep in-app and web flows equally short; optionally schedule deletion but offer immediate; state when it completes and notify.
- Explain subscription billing/cancellation on deletion; revoke Sign in with Apple tokens.
- tvOS: minimize data entry, authenticate via another device, no repeated profile picking, avoid sign-out when signed in at system level.
Avoid: Forced sign-in at launch.
Platform notes: watchOS - use iCloud Keychain sync.
Beyond Apple platforms: Guest browsing, passkeys, clear delete-account path apply everywhere.

## Managing notifications
URL: https://developer.apple.com/design/human-interface-guidelines/managing-notifications
Essence: Send relevant notifications with truthful urgency and with permission.
Rules:
- Permission is required; users can change it in Settings, so also provide in-app notification settings.
- Interruption levels: Passive, Active (default), Time Sensitive (immediate and relevant within about an hour, breaks through Focus), Critical (health/safety, needs entitlement, overrides silent switch).
- Be honest about urgency; never fake priority.
- Communication notifications (calls/messages) use sender-based delivery.
- Never send marketing without explicit opt-in, and never mark marketing Time Sensitive; explain types in an opt-in prompt with clear accept/decline.
Avoid: Using urgency to push low-value info.
Platform notes: watchOS - settings mirror iPhone; swipe options like Mute 1 Hour.
Beyond Apple platforms: Same urgency tiers and opt-in logic for web push/Android channels.

## Modality
URL: https://developer.apple.com/design/human-interface-guidelines/modality
Essence: Use a separate, blocking mode only when it clearly helps focus or decisions.
Rules:
- Present modally only for clear benefit: critical info, confirming/modifying an action, a narrow task, or immersion.
- Keep modal tasks short and simple; avoid an "app within an app"; if subviews are needed provide a single path and avoid buttons that resemble the dismiss button.
- Use full-screen modal for media or complex multistep tasks (markup, photo editing).
- Always provide an obvious dismiss: iOS/iPadOS/watchOS top toolbar button or swipe down; macOS/tvOS a button in content.
- Confirm before dismissing if user content would be lost (e.g. action sheet with Save).
- Title the modal with its task so people keep their place.
- Show one modal at a time (an alert may sit on top, but never two alerts).
Avoid: Stacked modals; hiding the previous context in long tasks.
Platform notes: none.
Beyond Apple platforms: Same for dialogs/bottom sheets on web/Android: one at a time, visible close, confirm on discard.

## Multitasking
URL: https://developer.apple.com/design/human-interface-guidelines/multitasking
Essence: Apps must handle being switched away from, resized and interrupted.
Rules:
- Always be ready to save and restore context.
- Pause games/media when switched away; resume seamlessly.
- Audio interruptions: pause indefinitely for primary audio (music, podcasts); duck or briefly pause for short ones (navigation prompts) and resume.
- Finish user-initiated tasks in the background (downloads, video processing).
- Use notifications sparingly: only for important/time-sensitive task completion.
- iPad: adapt gracefully to windowed sizes; apps are not told the multitasking configuration.
- visionOS: do not alter window edges, do not pause video when looking away, expect audio ducking.
Avoid: Notifying for routine completions.
Platform notes: Not supported in watchOS.
Beyond Apple platforms: Responsive layouts and state persistence (web tabs, Android multi-window).

## Offering help
URL: https://developer.apple.com/design/human-interface-guidelines/offering-help
Essence: Contextual, dismissible help matched to the task.
Rules:
- Match help to task complexity: inline hint for 1-2 steps, tutorial for complex tasks; tie it to the current action and make it dismissible.
- Use platform-consistent wording (tap vs click) and imagery for the current input device; keep it inclusive.
- Do not explain standard components; show animation or graphics for unusual controls.
- Tips: transient, short (1-2 sentences), actionable, only for features achievable in about three actions or fewer; popover tip preserves flow, inline tip keeps context visible; use filled symbols; use eligibility rules and a cadence (e.g. once per 24 hours); optional button to settings or more info.
- Tooltips (macOS/visionOS): describe only that control, start with a verb, no repeating the control name, 60-75 characters max, sentence case, optionally state-dependent.
Avoid: Promotional tip content; help for obvious controls.
Platform notes: Tooltips only macOS/visionOS.
Beyond Apple platforms: Coach marks and tooltips follow the same brevity rules.

## Onboarding
URL: https://developer.apple.com/design/human-interface-guidelines/onboarding
Essence: Fast, fun, optional introduction after launch.
Rules:
- Teach by doing; prefer context-specific tips over a long up-front flow.
- Any mandatory flow must be brief and not require memorization.
- Tutorials should be skippable, never re-shown after skipping, but findable later (help/settings/account).
- Teach only your app, not the OS.
- Avoid large downloads blocking first use; ship enough content in the package.
- Do not show license text in onboarding (App Store handles it).
- Postpone nonessential setup; ship good defaults.
- Ask permission in onboarding only if the app cannot function without it (explain why); otherwise ask in context at first use.
- Delay rating or purchase prompts until the person is engaged.
Avoid: Overwhelming walkthroughs.
Platform notes: none.
Beyond Apple platforms: Universal.

## Playing audio
URL: https://developer.apple.com/design/human-interface-guidelines/playing-audio
Essence: Audio must respect silence, volume, headphones and routing.
Rules:
- Honor silent mode for nonessential sound; system volume governs final output (adjust only relative mix).
- Headphones: reroute smoothly on connect, pause immediately on disconnect.
- Allow output rerouting; use the system volume view.
- Pick the right audio category: solo ambient, ambient, playback, record, play and record (they differ in silence-switch response, mixing, background play).
- Respond to external controls only when your app is an active audio context; do not redefine control meanings.
- Handle interruptions: resume only for resumable ones (calls) when appropriate; signal when temporary audio ends.
- visionOS: prefer sound, design sounds for custom UI, use Spatial Audio, vary repetitive sounds, tracked vs fixed audio.
- watchOS: 64 kbps HE-AAC.
Avoid: Conveying important info only by sound.
Platform notes: tvOS plays no UI sounds unless user-initiated; macOS notification sounds mix.
Beyond Apple platforms: Respect media sessions/audio focus on web and Android.

## Playing haptics
URL: https://developer.apple.com/design/human-interface-guidelines/playing-haptics
Essence: Use touch feedback that reinforces cause and effect.
Rules:
- Use system patterns for their documented meanings; keep each haptic tied to one cause.
- Complement visuals and sound (match intensity/sharpness to animation).
- Prefer short haptics for discrete events; do not overuse; make haptics optional.
- Standard controls (toggles, sliders, pickers) already play haptics.
- iOS categories: Notification (task outcome), Impact (physical collisions/snaps), Selection (changing values).
- Custom haptics: transient taps and continuous vibrations with sharpness and intensity.
- macOS trackpad patterns: Alignment, Level change, Generic.
- watchOS haptics: Notification, Up, Down, Success, Failure, Retry, Start, Stop, Click.
Avoid: Long-running haptics in normal apps; interfering with camera/mic/gyro.
Platform notes: as above.
Beyond Apple platforms: Android HapticFeedback and web Vibration API follow the same restraint.

## Playing video
URL: https://developer.apple.com/design/human-interface-guidelines/playing-video
Essence: Use the system video player and respect aspect ratio and expected controls.
Rules:
- Prefer the system player; mimic it if custom.
- Always show video at its original aspect ratio, without baked-in letterbox padding. Aspect-fill is default for wide (2:1 to 2.40:1); aspect-fit for 4:3, 16:9, up to 2:1 and ultrawide above 2.40:1.
- Support Space for play/pause and Siri Remote gestures.
- Avoid audio mixing when switching PiP and full screen.
- TV app: black screen immediately, content plays at once, auto-resume without asking, correct profile, previous end time, loading screen only after 2 seconds (black, centered spinner), contextual screen on exit.
- tvOS: small overlays only; interactive overlays pause playback with 0.5 s minimum delay and clear dismissal.
- visionOS: user-started playback, small resizable window, surroundings visible, thumbnails 160 px wide; no auto immersive video.
- watchOS: clips up to 30 seconds, H.264 High, 160 kbps, 208x260 px portrait or 320x180 px landscape, 64 kbps HE-AAC.
Avoid: Poster images that look like controls.
Platform notes: as above.
Beyond Apple platforms: Aspect ratio and expected key shortcuts apply to web players.

## Printing
URL: https://developer.apple.com/design/human-interface-guidelines/printing
Essence: Use the system print UI and expose print only when possible.
Rules:
- Place Print in the File menu (macOS) or the action sheet/toolbar (iOS/iPadOS).
- Dim or remove Print when nothing can be printed or no printer exists.
- Use the system view for page range, copies, duplex.
- macOS: custom print panel category named after the app, page setup for rarely changed settings, show option dependencies, hide advanced options under a disclosure labeled Advanced Options, preview effects, keep settings with the document.
Avoid: Reimplementing system options.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: Print stylesheets and PDF export on web.

## Ratings and reviews
URL: https://developer.apple.com/design/human-interface-guidelines/ratings-and-reviews
Essence: Ask for ratings at the right moment.
Rules:
- Ask only after demonstrated engagement (task or level completed); never on first launch or in onboarding.
- Pick natural breaks, never mid-task.
- Space requests by at least a week or two.
- Use the system prompt: one-tap dismiss, capped at 3 per app per 365 days.
- Weigh resetting summary rating against fewer total ratings.
Avoid: Pestering.
Platform notes: none.
Beyond Apple platforms: Same timing on Play Store/web.

## Searching
URL: https://developer.apple.com/design/human-interface-guidelines/searching
Essence: One discoverable, scoped, suggestion-rich search.
Rules:
- If search is important give it primary position (toolbar, or a dedicated tab in tab-bar apps).
- Make all content searchable from one place; local search as a filter is fine.
- Show the current scope (placeholder, scope bar, or title).
- Offer recent searches and live suggestions; offer filters by attribute; clear history option and mind privacy.
- Index content for Spotlight with metadata; use system open/save views with built-in search; Quick Look generator for custom files.
Avoid: Showing search history where others can see it.
Platform notes: none.
Beyond Apple platforms: Direct for any search UI.

## Settings
URL: https://developer.apple.com/design/human-interface-guidelines/settings
Essence: Few, sensible settings in the right place.
Rules:
- Pick defaults that serve most people; minimize the number of settings.
- Open settings with Command-Comma (Esc in games).
- Don't ask what can be detected (controller, Dark Mode); don't duplicate system settings (accessibility, scrolling, auth).
- Put infrequent general options in the settings area; put task-specific options (filters, ordering, visible parts) in the screens they affect.
- Only rarely changed options belong in the system Settings app; add a button that opens it.
- macOS: Settings item in the App menu, not toolbar; dim minimize/maximize; non-customizable toolbar with active pane highlighted; title is the pane name or "App Name Settings"; restore last pane.
- watchOS: no custom system settings; put a few options at the bottom of the main view or in a More menu.
Avoid: Settings that disconnect an option from its context.
Platform notes: as above.
Beyond Apple platforms: Contextual options beat a giant preferences page everywhere.

## Undo and redo
URL: https://developer.apple.com/design/human-interface-guidelines/undo-and-redo
Essence: Reversible actions encourage exploration.
Rules:
- Name what will be undone (Undo Typing, Redo Bold; iOS alert "Undo Name").
- Reveal the result (scroll to the restored content).
- Allow many levels; consider batch undo and revert-all.
- Dedicated buttons only when necessary, using system symbols in a toolbar.
- iOS: don't redefine shake or three-finger swipe. macOS: top of Edit menu, Command-Z and Shift-Command-Z.
Avoid: Arbitrary limits on undo depth.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: Toast with Undo for destructive actions on mobile web/Android.

## Workouts
URL: https://developer.apple.com/design/human-interface-guidelines/workouts
Essence: Fitness sessions on Apple Watch/iPhone/iPad showing relevant live data.
Rules:
- Show the metrics people care about (time, calories, distance) and relevant controls (lap).
- Distinct look for an active session; easy pause/resume/stop with clear start/stop feedback.
- Large high-contrast text for motion.
- Explain missing sensor data (e.g. swimming); end with a summary and Activity rings.
- Discard extremely short sessions or ask.
- Use Activity rings only per their documented meaning.
Avoid: Distracting info during a session.
Platform notes: Not on macOS/tvOS/visionOS.
Beyond Apple platforms: Apple-only (HealthKit/WorkoutKit), but large-glance metrics apply to any fitness UI.
