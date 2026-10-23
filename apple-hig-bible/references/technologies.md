# Technologies — HIG digest
Source pages: 29. Digest written 2026-10-22. Live pages are authoritative when in doubt.

## AirPlay
URL: https://developer.apple.com/design/human-interface-guidelines/airplay
Essence: How media apps should behave when streaming to Apple TV, HomePod and AirPlay speakers, and how to show AirPlay branding.
Rules:
- Prefer the system media player; build a custom one only if it truly cannot meet your needs.
- Offer the full range of HLS resolutions so the content looks good on a 4K TV, not just the phone's 720p.
- Stream only what people expect: no background loops or in-app-only short clips.
- Support both streaming and mirroring, and support remote-control events (lock screen, Siri, HomePod).
- Keep playback going when the app backgrounds or the device locks; never auto-mirror in that case.
- Do not interrupt other apps' playback unless starting immersive content; keep the rest of the app usable and do not start other videos while AirPlay is active.
- Custom players need buttons with distinct states (starting, playing, unavailable), Apple symbols only, and the AirPlay control in the lower-right (iOS/iPadOS 16+).
- Branding: black icon on light, white on dark, matching other tech icons; icon and name are noninteractive only; one word "AirPlay", used as a noun; your app stays more prominent than AirPlay.
Avoid:
- Using the AirPlay icon or name inside custom buttons; using the icon in place of the word in a sentence.
Platform notes: Not supported on watchOS.
Beyond Apple platforms: Same media rules apply to Cast/remote playback: prefer the platform player, keep playback alive in background, expose remote controls.

## Always On
URL: https://developer.apple.com/design/human-interface-guidelines/always-on
Essence: Designing for the dimmed, low-power glanceable state on iPhone 14 Pro+ and Apple Watch.
Rules:
- Redact sensitive data (balances, health data, notification contents) in the dimmed state.
- Keep genuinely glanceable info (workout pace, flight arrival, ride arrival) visible; users can turn Always On off.
- Keep the key content legible and dim secondary text, images and color fills; remove row backgrounds and big images or replace with dimmed colors.
- Keep the layout stable when entering/leaving; show interactive controls as unavailable rather than removing them.
- Update rarely and subtly (e.g. only the score, not play-by-play); motion is more noticeable on a face-up iPhone.
- Wind motion down to a resting state smoothly instead of freezing instantly.
Avoid:
- Distracting layout changes at the transition; frequent updates while dim.
Platform notes: iOS (iPhone 14 Pro and later) and watchOS only.
Beyond Apple platforms: Applies to any ambient/lock-screen/AOD surface: redact private data, dim secondary content, low motion.

## App Clips
URL: https://developer.apple.com/design/human-interface-guidelines/app-clips
Essence: Lightweight, instantly available slices of an app for a single task or a demo, launched from codes, NFC, links or Maps.
Rules:
- Let people finish the task or full demo without installing the full app; no ads, not just marketing.
- Include only essential features: linear UI, no tab bar, no settings, minimal screens and form fields.
- Open straight to the relevant screen; bundle assets, no splash screen, no waiting; keep download size tiny and avoid extra downloads.
- No web views; use native UI (otherwise link to the website).
- Make it shareable via deep links to specific points.
- Payments: support Apple Pay; avoid required accounts (ask after the task) or use Sign in with Apple; storing off-device because the system may delete App Clip data.
- On install, the full app replaces the clip; do not make people log in again.
- Recommend the full app politely at a natural pause with SKOverlay; never repeatedly or mid-task, never via push.
- Notifications last 8 hours after launch by default; ask for more only if the task spans over a day; no promotional notifications.
- Business platforms: brand the clip as the individual business, tone down your own, and handle switching between locations.
- App Clip card: photo/graphic (not a UI screenshot), no text in image, 1800x1200 px PNG/JPEG without transparency; title max 30 characters, subtitle max 56; action verb View (media/info), Play (games), Open (else).
- App Clip Codes: use only generated codes, never alter colors/add effects/rotate/animate/overlay; NFC variant when reachable, scan-only when not; flat or cylindrical surface only (code width at most 1/6 of cylinder circumference).
- Code sizes: printed min 3/4 in (1.9 cm) diameter; digital min 256x256 px (PNG/SVG); NFC tag min 35 mm (printed code 1.37 in / 3.48 cm); keep distance-to-size ratio at most 20:1, ideally 10:1; clear space equals gap between center glyph and the ring.
- Printing: matte, non-textured, UV-resistant outdoors; at least 300 dpi (rasterize at 600 ppi); convert sRGB to CMYK with relative colorimetric intent; test prints; Type 5 NFC tags; add a call to action ("Scan to ...", "Hold your iPhone near ...").
Avoid:
- Account walls, splash screens, web views, ad content, modified or glossy-printed codes, translating Apple trademarks.
Platform notes: iOS and iPadOS only.
Beyond Apple platforms: Android Instant Apps / web mini-flows share the same principles: tiny, one task, no login wall, native speed.

## Apple In-App Purchase
URL: https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase
Essence: Selling digital goods and subscriptions in-app (physical goods use Apple Pay instead).
Rules:
- Four types: consumable, non-consumable, auto-renewable subscription, non-renewing subscription.
- Let people try before buying (free tier, trial, metered paywall); make the store look native to your app.
- Short product names that do not wrap; always display the total billing price for every item; hide or explain the store when payments are disallowed.
- Never modify or replicate the system purchase confirmation sheet.
- Family Sharing: mention it where people learn about content and tailor welcome copy for family members.
- Refund help: show a help screen with a plain "Refund"/"Request a Refund" action, no scrolling or extra screens to reach it, purchase context (image, name, date); never characterize Apple's refund policy.
- Subscriptions: show value in onboarding, offer multiple levels/durations, prompt at relevant moments but not to existing subscribers, provide sign-in/restore.
- Sign-up screen must show name, duration, contents, localized price, intro price + duration + standard price, terms/privacy links, and a restore/sign-in option; explain free-trial auto-billing explicitly; ask only necessary info; include a sign-up entry in settings.
- Offer codes: one-time use (large-scale not needed) vs custom (alphanumeric ASCII only); support in-app redemption with a "Redeem Code" button and welcome new subscribers right after redemption.
- Show renewal date and plan summary; use system subscription-management UI; cancelling must always be easy (no hiding it), with optional retention nudges.
Avoid:
- Hiding cancel, vague trial terms, extra fields before purchase.
Platform notes: watchOS - use a modal sheet or one-button-per-option / list-plus-button for compact comparison, with a Close button.
Beyond Apple platforms: Subscription paywall transparency (price, period, trial end, easy cancel) is good practice everywhere and required by Play policies.

## Apple Pay
URL: https://developer.apple.com/design/human-interface-guidelines/apple-pay
Essence: Rules for offering Apple Pay checkout (physical goods, services, donations, recurring payments) in apps and on the web.
Rules:
- Offer it only on supported devices/browsers; make it the primary (not necessarily only) option when a card is available, in the same step as other options, first or larger.
- Apple Pay buttons only start payment or setup; use the API-provided button (localized, VoiceOver-ready); never recreate it. Custom buttons must not show the logo or "Apple Pay" text.
- Do not hide or grey-out the button; if info is missing (size, color), explain after tap and navigate to the field.
- Offer buttons on product pages for single-item buying, express checkout for carts; coupons enterable on the sheet; collect optional data (gift note) before or after checkout.
- Do not require an account before purchase; offer registration on the confirmation page.
- Payment sheet: only essential data (no shipping address for digital goods); shipping methods with name, cost, date range; line items for charges/discounts/recurring/donation, short enough for one line; show "Pay [Business Name]" matching the bank statement; "Pay [Merchant (via You)]" for marketplaces; "Amount Pending" when final cost is unknown.
- Do not add your own spinners; defer to the sheet's progress UI.
- Errors: be specific and field-based ("Zip code doesn't match city"), noun phrase, sentence case, no end punctuation, 128 characters or fewer; be lenient (accept Zip+4, phone formats); cancel any in-flight payment on dismissal.
- Subscriptions: explain billing frequency, trial amount, regular amount and start date in line items; show the sheet only when cost increases.
- Donations: "Donation $50.00" line item; presets such as $25/$50/$100 plus "Other Amount".
- Button types: Buy, Book, Check Out, Donate, Subscribe, Set Up, Pay, Order, Rent, Reload, Add Money, Top Up, Support, Contribute, Tip, plain. Styles: black (light backgrounds), white with outline (light backgrounds lacking contrast), white (dark); prefer automatic.
- Button size: min width 100 pt (140 pt for Book/Buy/Check Out/Donate/Subscribe/Set Up variants), min height 30 pt, min margin 1/10 of button height; not smaller than other payment buttons; in side-by-side layouts it sits right of Add to Cart, in stacked layouts above it; corner radius may match your buttons.
- Mark graphic: unmodified, height at least that of other payment marks, clear space 1/10 height, never a button.
- Text: "Apple Pay" two words, never plural or possessive, not translated; do not mimic Apple fonts.
- Web icon for authorization: 60x60 pt (120 px @2x, 180 px @3x).
Avoid:
- Separating Apple Pay into an extra step, opening new windows mid-checkout, forced business-logic validation.
Platform notes: Not on tvOS.
Beyond Apple platforms: General checkout rules (lenient validation, field-specific errors, guest checkout, no surprise windows) transfer to any payment UI such as Google Pay.

## Augmented reality
URL: https://developer.apple.com/design/human-interface-guidelines/augmented-reality
Essence: Designing ARKit experiences on iPhone/iPad that blend virtual objects with the camera view.
Rules:
- Offer AR only on capable devices; do not show an error, just omit the feature.
- Use the whole screen for the world; keep controls minimal and translucent, in screen space, reachable without repositioning the device.
- Update scenes at 60 fps; scale to real size, place on detected surfaces, match lighting, add soft top-down shadows; prefer small/coarse reflections.
- Add sound and haptics for contact feedback; minimize text in 3D, and keep 3D text facing the viewer at constant size.
- Use the system coaching overlay for initialization and relocalization; hide unrelated UI while it shows.
- Placement: show an indicator aligned to the plane, place objects immediately and refine later (nudge back onto the surface), use plane classification (floor/table), do not align precisely to surface edges.
- Interaction: direct manipulation with familiar gestures (one-finger drag, two-finger rotate); accept touches near small objects; scale only when real-world size is not the point; never use scaling to change apparent distance; test pinch vs rotate conflicts; objects stay attached and visible while moving.
- Comfort/safety: place objects so the device need not be held close, short levels, introduce movement gradually, avoid encouraging sudden motion.
- Image detection: wait up to 1 second before removing content when an image disappears; keep reference images to 100 or fewer; track only those that need positions.
- Language: friendly ("Try moving your phone more slowly") not technical ("Excessive motion detected"); offer fixes and a reset option; make relocalization cancellable; hide placed objects during relocalization.
- AR glyph/badge: unaltered, clear space 10% of height, same corner on photos, only for ARKit experiences, use badges only on mixed catalogs.
Avoid:
- Technical jargon in prompts, cluttered overlays, forcing users to wait for tracking.
Platform notes: visionOS uses ARKit with permission for surfaces and hand tracking.
Beyond Apple platforms: Same coaching, comfort, and plain-language rules apply to ARCore/WebXR.

## CareKit
URL: https://developer.apple.com/design/human-interface-guidelines/carekit
Essence: Building care-plan apps (tasks, charts, contacts) while treating health data with maximum care.
Rules:
- Provide a clear privacy policy URL; get permission before reading any device/health data and protect it however obtained.
- Ask for HealthKit access only in context (weight when logging weight), every time it is needed; add a short purpose line to the system permission screen; do not clone it; manage sharing only via system Settings > Privacy.
- Use views for their purpose: tasks (actions, logging), charts (progress), contacts (call/message/email/map).
- Task styles: simple (one step), instructions (one step plus notes), log (record events with timestamps), checklist (multi-step, with text), grid (compact buttons, short titles). A task needs a title and schedule; instructions and group ID are optional.
- Use color to reinforce task categories but never as the only signal; use the product's marketing name for medicines, trim redundant words, add images/video for complex steps.
- Charts (bar, scatter, line): short labels, units stated once on the axis, distinct (not same-hue) colors with sufficient contrast, legend when unclear, units of time labeled, consolidate large data sets, offset tiny values so they stay readable.
- Notifications: minimize, coalesce, and offer a detail view for quick actions.
- Symbols: prefer built-in or SF Symbols; custom symbols must be health-relevant, never logos or decoration.
- Branding: subtle (color, tone); no advertising.
Avoid:
- Color-only meaning, extra permission screens, notification overload.
Platform notes: iOS and iPadOS only.
Beyond Apple platforms: Health-data consent in context, restraint with reminders, and clear, small-label charts apply to any care or habit app.

## CarPlay
URL: https://developer.apple.com/design/human-interface-guidelines/carplay
Essence: In-car UI built from system templates, designed for glance-and-go use while driving.
Rules:
- No interactions on iPhone while CarPlay is active; any setup must occur before driving.
- Never lock the driver out because the phone needs input; work with the phone locked and out of reach; show errors in CarPlay and never tell people to pick up the phone.
- Audio: do not autoplay unless resuming or a single-source app; do not open an audio session until ready (it silences the radio); start playback as soon as audio is ready with Now Playing shown immediately; resume only after resumable interruptions; balance relative levels but never change master volume.
- Layout: clean, scannable, consistent, large tap targets, key content and controls in the upper half; display sizes range 800x480 (5:3) to 1920x720 (8:3), scaled automatically.
- Color: a limited palette matching the logo; different colors for interactive vs noninteractive items; test in a real car in day and night and bright sun; support light and dark; consider color-blind users.
- Icons: provide @2x/@3x artwork; reuse your iPhone icon at 120x120 px (@2x) / 180x180 px (@3x); do not use a pure black icon background.
Avoid:
- Clutter, redirecting to the phone, same color for tappable and static items.
Platform notes: iOS only; audio/video apps also run on HomeView.
Beyond Apple platforms: Android Auto and any in-vehicle UI: minimal interaction, large targets, template-driven, never require the phone.

## Game Center
URL: https://developer.apple.com/design/human-interface-guidelines/game-center
Essence: Integrating achievements, leaderboards, challenges and multiplayer via Game Center.
Rules:
- Sign players in at launch if not already signed in.
- Access point: show on menu/settings screens (not during gameplay, splash, cutscenes, tutorials); pick a screen corner, keep controls clear of both its collapsed and expanded size; consider pausing while the overlay is open.
- Custom links: use official artwork unaltered; use exact terms (Game Center, Achievements, Leaderboards, Challenges, Add Friends) not synonyms.
- Achievements: map to four states (locked, in progress, hidden, completed); order = upload order; title and description max two lines each (title in title case, description in sentence case); use progressive achievements; unique art each, content centered because of a circular mask; image 512x512 pt (1024 px @2x), sRGB/P3, 72 dpi minimum (tvOS 320x320 pt, 200 pt mask).
- Leaderboards: classic (all-time best) vs recurring (resets daily/weekly); group with sets (difficulty, activity, genre); one image each 512x512 pt with 512x312 pt crop area (tvOS 659x371 pt with focus sizes).
- Challenges: 1-5 minute skill-based tasks, score = most recent attempt (not personal best); deep-link directly into the level, run onboarding first when needed; art 1920x1080 pt with 1465x767 pt safe crop; localize text in art.
- Multiplayer: party codes (typically eight alphanumeric characters), allow late join/early leave, show current code, allow manual entry; activity art same size as challenges.
Avoid:
- Placing controls near the access point; reusing one image for multiple achievements.
Platform notes: tvOS dashboard image 600x180 pt (use logo, not app icon); watchOS has no system Game Center UI.
Beyond Apple platforms: Gamification patterns (progress toasts, short fair challenges, shareable join codes) apply to any game or loyalty feature.

## Generative AI
URL: https://developer.apple.com/design/human-interface-guidelines/generative-ai
Essence: Responsible, transparent, controllable design of features that generate or transform text, images and other content.
Rules:
- Keep people in control: let them dismiss, edit, undo, retry, or adjust generated content; surface Edit/Undo/Retry/Adjust near the output and confirm when a correction took effect.
- Add AI only where it brings clear value (time saved, better communication, creativity); give a non-AI fallback so the app works if AI is unavailable or declined.
- Disclose where AI is used; never pass off AI as a human; follow local disclosure laws.
- Set expectations: brief tutorial, curated example prompts for open-ended inputs, known limits explained up front and why bad results happen.
- Inclusion: ask users for attributes instead of inferring gender, culture or relationships; test across diverse people to find stereotypes.
- Privacy: prefer on-device models (private, fast, offline); use servers only when needed, process locally first, minimize and disclose what is sent, stored or used for training; ask permission for personal/usage data, collect the minimum, always allow opt-out; explain benefits concisely.
- Evaluate models and datasets: know licensing, diversity, availability (device, network, battery); test for bias and misinformation.
- Hallucinations: scope tasks tightly; avoid asking for facts without verified sources; say output may contain errors; do not use where an error could harm.
- Irreversible or significant actions (deleting, buying) need explicit confirmation; never automate them silently.
- Blocked or poor results: coach with better example prompts and plain wording ("Unable to use that description").
- Stress-test with vague, out-of-scope, sensitive, and abusive inputs; reduce copyright replication (pre-approved prompts, instruct model to avoid styles).
- Latency: generative is slow; build a loading experience or generate in the background; use specific progress text ("Summarizing key themes from your notes") not "Processing..."; offer alternate versions when helpful.
- Provide optional, unobtrusive feedback (thumbs up/down plus detailed); keep the model decoupled from the UX so it can be swapped; plan continuous improvement.
Avoid:
- Hiding AI use, automating destructive actions, vague spinners, forced feedback.
Platform notes: none.
Beyond Apple platforms: Fully portable and a strong reference for any LLM feature: disclosure, undo/retry, fallback, confirm risky actions, specific progress messages.

## HealthKit
URL: https://developer.apple.com/design/human-interface-guidelines/healthkit
Essence: Reading and writing health/fitness data via HealthKit, plus Activity ring and Apple Health branding rules.
Rules:
- Request health access only if you offer health functionality, only in context and each time it is needed; add short purpose text to the standard permission sheet; never duplicate it; keep sharing control only in system Settings.
- Provide a clear privacy-policy URL.
- Activity rings: only for Move, Exercise, Stand; one person only (label or avatar); never decorative, branding, or in the app icon/marketing; never recolor, filter, or change opacity; keep outer margin at least the ring gap and never crop; set a circle via corner radius, not a mask; separate other rings with padding/lines/labels; do not duplicate system activity notifications or show rings in them.
- Apple Health icon: Apple-provided only, shown next to the name "Apple Health", at least as large as neighboring app icons, never a button, never masked/altered, clear space 1/10 height, never in running text; do not use Health screenshots.
- Copy: say "Apple Health" (two words) or "Apple Health app", never "HealthKit"; use the system translation of Health.
Avoid:
- Requesting health data upfront at launch; mimicking rings with other data.
Platform notes: Not on macOS, tvOS, visionOS.
Beyond Apple platforms: Contextual, just-in-time permission requests and honoring system-level privacy controls apply to Health Connect and any sensitive data.

## HomeKit
URL: https://developer.apple.com/design/human-interface-guidelines/homekit
Essence: Integrating with the Home app model (homes, rooms, zones, accessories, scenes) and Siri voice control.
Rules:
- Use HomeKit vocabulary: home, room, zone, accessory, service, characteristic (never shown in UI; show descriptive names such as "ceiling fan light"), scene (not "action set"), automation.
- Surface room/zone/home info in the accessory detail view; support multiple homes; do not duplicate home settings or ask to re-set them up; defer to the Home app database on conflicts and show conflicts visually side by side.
- Use the system setup flow; show a clear purpose string for Home data; no required account or personal info (offer optional cloud account after setup); do not force other platform setups; offer custom post-setup experience afterwards.
- Names: suggest good service names (never company or model numbers); rules: alphanumeric, spaces and apostrophes only, start and end with a letter or digit, no emoji; avoid room names inside service names ("kitchen light").
- Siri: show example commands using the user's chosen service name right after setup and teach richer phrases later; recommend zones and service groups; offer Shortcuts only for functionality HomeKit lacks, and explain the difference.
- Ask before writing to the HomeKit database; never overwrite settings without explicit direction.
- Cameras: do not cover the video; show a mic button only if two-way audio is supported.
- Branding: Apple-provided icons only (black on light, white on dark, or matching color), noninteractive, never in text; your app stays more prominent; "HomeKit" one word, "Apple Home" two words; use "works with/compatible with", not as a descriptor; do not imply HomeKit performs actions; never translate.
Avoid:
- Duplicating Home app settings, forcing accounts at setup.
Platform notes: none.
Beyond Apple platforms: Smart-home apps elsewhere benefit from the same room/zone naming, no-account-first setup, and voice-friendly naming advice.

## iCloud
URL: https://developer.apple.com/design/human-interface-guidelines/icloud
Essence: Seamless cross-device sync where people never think about where content lives.
Rules:
- Work with iCloud automatically when the user has it on; if a choice is needed, ask once at first launch: all data or none.
- Do not ask which individual documents to keep in iCloud; do file management for them.
- Keep content current; for very large documents let users control downloads, indicate a newer version exists, and show subtle feedback if a download takes more than a few seconds.
- Respect the paid, finite quota: store user-created content, not regenerable resources; remember backups include the whole Documents folder.
- When offline/iCloud off, no alert needed; unobtrusively note that changes will not reach other devices until restored.
- Sync app state (last page, device-independent settings) not device-specific preferences.
- Deleting removes the document everywhere: warn and confirm.
- Resolve version conflicts automatically; otherwise show an unobtrusive, early, easy-to-compare chooser.
- Include iCloud content in search; for games sync save progress (GameSave) with conflict alerts.
Avoid:
- Per-document storage prompts, noisy "iCloud unavailable" alerts, storing regenerable data.
Platform notes: none.
Beyond Apple platforms: Direct template for any cloud-sync UX: silent offline handling, delete-everywhere warning, simple conflict chooser, sync state not just files.

## ID Verifier
URL: https://developer.apple.com/design/human-interface-guidelines/id-verifier
Essence: Reading mobile IDs (ISO 18013-5) in person from an iPhone app.
Rules:
- Ask for the minimum data: use an age-threshold request (ageAtLeast) rather than birth date.
- Display Only requests show data in system UI and never send it to your app; Data Transfer needs a legal requirement and an extra entitlement.
- Register the organization (Apple Business Register) so the name and logo appear on the customer's device.
- Start with a button labeled "Verify Age" or "Verify Identity"; no NFC/QR symbol, never the Apple logo.
- In Display Only flows, give the verifier "Matches Person" / "Doesn't Match Person" buttons.
Avoid:
- Over-collecting data; implying a specific transport on the button.
Platform notes: iPhone only (iOS 17+).
Beyond Apple platforms: Data-minimization via predicates ("over 21") instead of raw values is a general privacy pattern.

## iMessage apps and stickers
URL: https://developer.apple.com/design/human-interface-guidelines/imessage-apps-and-stickers
Essence: Apps and sticker packs that live inside Messages conversations.
Rules:
- One primary experience per iMessage app; split different functions into separate apps.
- Surface shareable content from the main app (lists, itineraries, quick group decisions).
- Put essential features in the compact view (it sits below the transcript, about keyboard height); allow text editing only in the expanded view.
- Stickers: expressive and legible on any background, rotated or scaled; use transparency; every sticker gets a localized alternative description for VoiceOver.
- Sticker sizes (@3x): small 300x300, regular 408x408, large 618x618 px; one size per pack; file at most 500 KB; PNG (8-bit alpha), APNG (animated), GIF (single-color transparency), JPEG (none).
- Supply a square-cornered icon (system rounds it); App Store 1024x1024; Settings 58 px @2x / 87 px @3x; Messages icons 148x110, 143x100, 120x90 (180x135 @3x), 64x48 (96x72), 54x40 (81x60).
Avoid:
- Mixing sticker sizes, hiding key actions in the expanded view.
Platform notes: iOS and iPadOS only.
Beyond Apple platforms: Same compact-vs-expanded split applies to mini-apps or share extensions in other messengers.

## Live Photos
URL: https://developer.apple.com/design/human-interface-guidelines/live-photos
Essence: Handling photos that include motion and sound consistently.
Rules:
- Apply edits to all frames, or offer conversion to a still.
- Keep the Live Photo intact; do not show frames or audio separately.
- When sharing, allow previewing the whole Live Photo and always offer sharing as a still.
- Show download progress and when it becomes playable.
- Where unsupported, display as a still without faking the effect.
- Distinguish from stills with a hint of motion (custom effect) or the system badge (with or without text) in a consistent corner; never a button that looks like video play.
Avoid:
- Video-like play buttons, splitting the asset.
Platform notes: Not on watchOS; visionOS can view but not capture.
Beyond Apple platforms: Motion-photo/GIF formats should degrade to a still gracefully with an indicator.

## Mac Catalyst
URL: https://developer.apple.com/design/human-interface-guidelines/mac-catalyst
Essence: Turning an iPad app into a native-feeling Mac app.
Rules:
- Good candidates already support drag and drop, keyboard shortcuts/navigation, multitasking and multiple windows; unsuitable if core features need gyroscope, rear camera, ARKit, handwriting etc.
- iPad idiom scales the UI to 77% (17 pt body becomes 13 pt); the Mac idiom renders at 100% with sharper text and needs a layout audit, text styles instead of fixed sizes, and a separate asset catalog.
- Replace a tab bar with a sidebar split view (preferred) or a segmented control for flat hierarchies; list top-level items in the View menu; offer Next/Previous buttons in addition to swipe.
- Gestures map automatically (tap to click, touch-and-hold to click-and-hold, pan to drag; pinch/rotate go to the view under the pointer).
- Provide a macOS-style app icon.
- Layout: multiple columns, regular size classes, inspector beside content instead of popovers, top-down flow, move controls from screen edges into the window toolbar and list the commands in the menu bar.
- Menus: every command should be in the menu bar; context menus on every object.
Avoid:
- Merely showing an iPad layout in a window.
Platform notes: iPadOS and macOS only.
Beyond Apple platforms: Responsive-web or Flutter desktop targets need the same desktop adaptations: menus, keyboard, hover, toolbar, resizable multi-column layouts.

## Machine learning
URL: https://developer.apple.com/design/human-interface-guidelines/machine-learning
Essence: A pattern library for designing ML-driven features: feedback, calibration, mistakes, corrections, options, confidence, attribution, limitations.
Rules:
- Classify the feature first: critical vs complementary, private vs public data, proactive vs reactive, visible vs invisible, dynamic vs static. Critical, sensitive, and proactive features need higher accuracy and carry more risk.
- Explicit feedback: only when necessary and always voluntary; describe consequences in plain words ("Suggest less pop music", "Mute politics for a week") not "Dislike"; icons only with text; offer progressively specific options; act immediately and persist the change.
- Implicit feedback: secure it, tell people how data flows and let them restrict it; avoid filter bubbles; combine several signals; withhold sensitive suggestions on shared devices; prefer recent behavior; update at a cadence matching the user's mental model; expect shifts when UI changes; beware confirmation bias.
- Calibration (e.g., Face ID setup): only when the feature cannot work without it; explain the benefit (what, not how); collect the minimum; do it once and early; give a goal and progress; help immediately when stalled without blaming; confirm success; allow cancel anytime without judgment; let users edit or delete the data later.
- Mistakes: anticipate them, scale remedies to consequences (wrong keyboard word vs missed flight), make common errors easy to fix, be extra careful in proactive features, and watch for regressions elsewhere.
- Corrections: familiar controls (show the steps taken), instant effect, persisted, re-correctable; guided (alternatives list) beats freeform; never use corrections to excuse poor quality.
- Multiple options: diverse options, few enough to fit one screen, most likely first (preselected), easy to distinguish; learn from selections.
- Confidence: verify it correlates with quality; translate to concepts people understand (ranking, "high chance", actionable "good time to buy") not "97% match"; hide results under a threshold, especially for proactive features; adapt UI by confidence (e.g., ask for confirmation).
- Attribution: factual, balanced specificity ("Because you've read mysteries"), no emotional claims, no jargon.
- Limitations: set expectations beforehand, show how to get good results (placeholder hints, live guidance), explain bad results, announce when a limit is lifted.
Avoid:
- Emotional attributions, required feedback, repeating calibration, relying on corrections for quality.
Platform notes: none.
Beyond Apple platforms: Portable to any recommendation, search, or AI feature on web/Android/Flutter.

## Maps
URL: https://developer.apple.com/design/human-interface-guidelines/maps
Essence: Designing embedded maps with annotations, overlays, place cards and indoor venue maps.
Rules:
- Keep maps interactive (zoom, pan, rotate); avoid fixed overlays that obstruct them.
- Emphasis style: default fully saturated; muted (desaturated) when your own content must stand out.
- Add search plus category filters; highlight the selected element with outline and color change; cluster nearby pins and expand on zoom.
- Keep the Apple logo and legal link visible (7 pt side padding, 10 pt above/below; fixed to the map; 10 pt above a pull-up card's lowest resting position; hidden on maps smaller than 200x100 px).
- Annotations: tint to brand, icon string of two to three characters; overlays either above roads (default) or above labels (hides map beneath).
- Custom controls need contrast with the map (thin stroke, light shadow, blend modes).
- Place cards: automatic, callout (full or compact), caption ("Open in Apple Maps"), sheet; pick for context, avoid duplicate info, keep the location visible via offset, set a min width; outside a map the card must include a map.
- Indoor maps: progressive detail by zoom, color plus icons, floor picker with concise numbers, dimmed surroundings for context, transit routing, limit scrolling away from venue, match your app's style.
Avoid:
- Clutter at low zoom, covering the logo permanently, copying Apple Maps' look in indoor maps.
Platform notes: watchOS maps are static snapshots (up to five annotations, tap opens Maps); show the smallest region covering all points and fit the screen.
Beyond Apple platforms: Clustering, floor pickers, contrast for map controls, and progressive detail apply equally to Google Maps/Mapbox.

## NFC
URL: https://developer.apple.com/design/human-interface-guidelines/nfc
Essence: Reading NFC tags in-app or in the background on iPhone.
Rules:
- Say "scan" and "hold near", not "tap"/"touch"; contact is not required.
- Avoid jargon (NFC, Core NFC, tag): "Scan the [object name]", "Hold your iPhone near the [object name] to learn more about it."
- Scan-sheet text: one complete sentence in sentence case with a period, naming the object; change it for later scans ("Now hold your iPhone near another [object name]"); keep it short to avoid truncation.
- Background reading works when the screen is on, but not while a scan sheet, Wallet/Apple Pay or the camera is active, in Airplane Mode, or after restart-lock; always also provide in-app scanning.
Avoid:
- Technical wording, asking users to touch objects.
Platform notes: iOS/iPadOS only.
Beyond Apple platforms: Android NFC: same plain-language prompts and an in-app fallback.

## Photo editing
URL: https://developer.apple.com/design/human-interface-guidelines/photo-editing
Essence: Editing extensions that run inside the Photos app, saving edits as new files.
Rules:
- Confirm Cancel (warn edits will be lost) only when edits exist.
- Do not add your own top toolbar; the system modal already has one.
- Let people preview the result before closing.
- Use your app icon for the extension icon.
Avoid:
- Duplicate toolbars, silent discard of work.
Platform notes: iOS, iPadOS, macOS.
Beyond Apple platforms: Confirm-before-discard and preview-before-commit apply to any editor flow.

## ResearchKit
URL: https://developer.apple.com/design/human-interface-guidelines/researchkit
Essence: Medical-study apps: onboarding, consent, surveys, active tasks, profile and dashboard.
Rules:
- Onboarding order: introduction (with quick login for returning users), eligibility (as early as possible, only necessary criteria), informed consent, then data/notification permissions.
- Consent: split into digestible sections with Learn More, show the entire form before agreeing, optional comprehension quiz, then confirmation, signature, contact details, and an emailed PDF copy.
- Request only data critical to the study and explain why.
- Surveys: say how many questions and how long, one question per screen, show progress, keep short (several short beat one long), explanatory text slightly smaller than question text, signal completion.
- Active tasks: simple instructions, state requirements (time/conditions), make completion obvious.
- Provide an always-available profile (edit data, leave study, view consent and privacy policy) and a dashboard showing progress and motivation.
Avoid:
- Long unbroken consent, requesting nonessential data.
Platform notes: iOS and iPadOS.
Beyond Apple platforms: Staged consent and survey patterns are reusable in any research or form-heavy flow.

## SharePlay
URL: https://developer.apple.com/design/human-interface-guidelines/shareplay
Essence: Shared real-time activities synced across devices alongside FaceTime or Messages.
Rules:
- Use for real-time activities; provide a share/save path for asynchronous follow-up.
- Choose one shared view for watching/browsing, or per-person views for roles/games; make activities work across platforms.
- Start with a clear control (SharePlay symbol button) plus system share sheet; joining must be frictionless: go straight to the content, brief sign-in/download views that dismiss automatically, provisional access or Family Sharing for paid content, defer nonessential setup.
- Short invitation description (title, summary, poster); keep people oriented when one person changes the activity (who did it, initials beside contributions).
- Terminology: "SharePlay" as noun or verb, no adjectives (no "virtual SharePlay"), no variants (SharePlayed).
- Support Picture in Picture for shared video on iOS/iPadOS/macOS.
- visionOS: start from a window; resolve conflicts naturally (last change wins, no take-control UI); sync immersion but let busy users opt in; keep volume/subtitles per person; easy leave and rejoin.
- Personas and templates: support people without spatial Personas; side-by-side (watching), surround (tabletop), conversational (background task) templates; stage complex activities; user-initiated, smooth transitions with fades.
- Custom templates: account for in-room users; seat up to five Personas, define all seats up front, at least 1 m apart, ordered for balance, roles independent of seats (spectator seats if limited).
Avoid:
- Forcing view changes on busy participants, role-bound seating.
Platform notes: Not on watchOS.
Beyond Apple platforms: Frictionless join, presence cues, last-write-wins conflict handling carry to web co-editing and watch-party apps.

## ShazamKit
URL: https://developer.apple.com/design/human-interface-guidelines/shazamkit
Essence: Audio recognition against Shazam or custom catalogs.
Rules:
- Request microphone access with a clear reason.
- Stop recording as soon as you have the sample you need.
- Get opt-in before saving recognized songs to the user's iCloud library.
Avoid:
- Leaving the microphone on.
Platform notes: none.
Beyond Apple platforms: Minimal-duration mic use and opt-in storage are general privacy norms.

## Sign in with Apple
URL: https://developer.apple.com/design/human-interface-guidelines/sign-in-with-apple
Essence: Private, one-tap account creation and sign-in with Apple Account (works on web and non-Apple platforms).
Rules:
- Ask for sign-in only in exchange for value and as late as possible; let people explore first.
- If an account is required, explain why and finish setup before offering sign-in methods; allow linking existing accounts; in commerce, offer account creation after purchase (confirmation page).
- Welcome the user immediately; show "Using Sign in with Apple" in account settings.
- Collect minimal data; mark required vs optional (and why); never ask for a password; never ask for a personal email when a private relay address was shared; show users the relay address or use order/phone number for lookup; do not block features if optional data is skipped; show the data you received (greet with name/email).
- Show the button prominently, no smaller than other sign-in buttons, without scrolling; prefer the system button (localized, VoiceOver, correct proportions).
- Styles: white (dark backgrounds), white with outline (light backgrounds with weak contrast; avoid dark/saturated), black (light backgrounds; not on dark). Titles: Sign in with Apple / Sign up with Apple / Continue with Apple.
- Size: min 140 pt wide x 30 pt tall, margin 1/10 of height; adjust corner radius to match other buttons (square to capsule); recommended height 44 pt on iOS.
- Custom buttons: must be instantly recognizable and pass App Review; use Apple's logo artwork at button height, no cropping, no vertical padding; fixed titles; logo and title both black or both white; rectangular with text, circle or rectangle for logo-only (1:1, no extra padding); title font size 43% of button height (height about 233% of font size); title right margin at least 8% of button width; vertically centered; keep default capitalization unless all-caps UI; may change font, background (black/white with subtle texture), corner radius, bezel, shadow; PNG logos only for 44 pt buttons, otherwise SVG/PDF.
Avoid:
- Forcing sign-in before value, requesting passwords, custom Apple logos.
Platform notes: watchOS button title is just "Sign in", dark gray instead of pure black.
Beyond Apple platforms: Social-login button parity (equal size and prominence), delayed sign-in, and minimal data collection are universal; Apple requires its button wherever other third-party sign-ins exist.

## Siri
URL: https://developer.apple.com/design/human-interface-guidelines/siri
Essence: Exposing app actions and content to Siri, Spotlight and Shortcuts via App Intents, and writing good voice responses.
Rules:
- Expose actions (intents) and content (entities) through App Intents; use app schemas for common domains; annotate on-screen content; donate entities to Spotlight and actions as intents.
- Prioritize your most popular actions (especially hands-free contexts); use terms people say (song vs track vs podcast); share personally relevant content, not everything.
- No ads or sales pitches in Siri content; custom responses only when built-in ones fall short.
- Responses: clear and descriptive ("Which soup?" not "Which one?"); as short as possible, no humor; audible and visual versions where the voice response stands alone; inclusive wording without gendered pronouns ("Who should I send it to?"); open-ended question when option lists are too long; device-independent; omit your app name; clean language respecting parental controls.
- Errors should be specific ("Sorry, we're out of chicken noodle soup").
- Copy: call it "Siri", never she/he/her; never impersonate Siri or use reserved phrases like "Call 911" or "Hey Siri"; only "Hey" may be localized (e.g. "Dis Siri", "Oye Siri"); Siri is never translated.
Avoid:
- Long chatter, repeated filler, app-name echo.
Platform notes: none.
Beyond Apple platforms: Voice-assistant responses elsewhere (Google Assistant, Alexa) benefit from the same short, standalone, inclusive, specific-error style.

## Tap to Pay on iPhone
URL: https://developer.apple.com/design/human-interface-guidelines/tap-to-pay-on-iphone
Essence: Letting merchants accept contactless payments on iPhone with no extra hardware, through a PSP.
Rules:
- Have an administrator accept terms before first use; get merchants to accept before they're mid-checkout; show admin-required messaging for others; ensure iOS version is current first.
- Provide a tutorial (supported payment types, positioning card/wallet, PIN entry incl. accessibility mode) in Learn More, after terms, for new users, and in help/settings; or use ProximityReaderDiscovery.
- Checkout: always show the Tap to Pay option even before enabling or while configuring in the background (show a progress indicator); prepare at launch and each foreground; easy to find without scrolling; if it is the only method, open it automatically.
- Button label "Tap to Pay on iPhone" or "Tap to Pay" (only for payment); reuse Charge/Checkout if it's the only method; use SF Symbol wave.3.right.circle(.fill); never the Apple logo; style to match your app.
- Finalize amounts (tip, etc.) and pre-payment options before showing the Tap to Pay screen.
- Results: start processing as soon as possible; show an authorization progress indicator after the tap animation; clearly show approved/declined; offer digital receipt (QR/text); on failure offer cash, other hardware, payment link or retry; handle SCA PIN prompts; give clear error resolutions and support access.
- Non-payment reads (no amount) use generic labels (Look Up, Store Card, Verify, Refund), never "Tap to Pay"; separate clearly labeled button for loyalty transactions.
Avoid:
- Making merchants wait for configuration, reusing payment wording for non-payment actions.
Platform notes: iPhone only.
Beyond Apple platforms: POS flows everywhere benefit from fixed amounts before tapping, immediate fallbacks, and non-blocking setup.

## VoiceOver
URL: https://developer.apple.com/design/human-interface-guidelines/voiceover
Essence: Making your interface usable by screen reader.
Rules:
- Give every key and custom element an alternative label, descriptive of function, and keep labels up to date.
- Describe meaningful images by what the image itself conveys (not what nearby captions say); hide purely decorative images.
- Charts and infographics: concise summary plus access to any interactions.
- Unique screen titles and accurate section headings (the title is the first thing announced).
- Specify grouping, order and links where relationships are only visual (e.g. group image with its caption); reading order follows the language (top-to-bottom, left-to-right for US English).
- Announce visible content or layout changes via accessibility notifications.
- Support the rotor (navigate by headings, links, etc.; also opens braille keyboard).
Avoid:
- Visual-only relationships, unexplained dynamic updates, decorative clutter in the accessibility tree.
Platform notes: visionOS - with VoiceOver on, apps get no custom hand-gesture input unless the user enables Direct Gesture mode.
Beyond Apple platforms: Maps directly to ARIA/TalkBack/Flutter Semantics: labels, headings, grouping, live-region announcements, hide decorative images.

## Wallet
URL: https://developer.apple.com/design/human-interface-guidelines/wallet
Essence: Creating Wallet passes, order tracking, and identity verification with Wallet.
Rules:
- Offer to add passes with system UI right after the triggering action; background-add after one-time authorization for predictable actions; suggest adding passes created elsewhere (once; do not re-ask after a decline); add related passes as a group; show an "Add to Apple Wallet" button for existing passes; offer a "View in Wallet" link.
- Set expiration, relevance and voided data correctly; never delete passes without permission; supply relevance info so passes surface on the Lock Screen; keep passes updated; change messages only for time-critical updates (gate change yes, support number no, never marketing).
- Fields: logo/logo text, header (visible collapsed), primary, secondary/auxiliary, footer, back; use semantic tags (required for poster event and semantic boarding passes) alongside fields for older OS.
- Design: simple and clean, not a copy of the physical item; uncluttered front with essential info in the header; identifiable via brand color/imagery; sufficient text contrast over images; device-neutral wording (not "Slide to view"); do not rely on elements that Apple Watch drops; no padding on images (watchOS crops).
- Styles: boarding pass, coupon, event ticket (poster variants), store card, generic, poster generic.
- Images: PNG @2x/@3x, no embedded text or barcodes, small files; logo 50 pt tall, 50-160 pt wide; primary logo 30 pt tall, 30-126 wide; secondary logo 12 pt tall, 12-135 wide; icon 38x38 pt; strip 375x144 pt; thumbnail 90 pt tall, 60-90 wide (transparent, rounded art); background 343x503 pt (poster artwork 358x448 pt, keep content in the safe area above the bottom material strip); footer 268x15 pt; avoid inner shadows on logos; keep text off busy strip areas.
- Order tracking: add via Apple Pay or "Track with Apple Wallet" button; show data immediately ("Check back later..."); update fulfillment statuses (Order Placed, Processing, Ready for Pickup, Out for Delivery, Delivered, Issue, Canceled); 300x300 px PNG/JPEG logo and product images with opaque backgrounds, plain product shots; short, localized text; price matches confirmed price; universal link to manage order; itemize line items; prioritized app list; avoid duplicate notifications; several contact methods; tracking links, pickup barcode, clear instructions; fulfillment screen focused on tracking; explain Issue/Canceled directly.
- Identity (Verify with Wallet): show only when the device supports it with a fallback; ask only at the moment needed (not at account creation); purpose string is a brief active-voice sentence in sentence case with period; request thresholds (age at least) not birth date; state retention duration; pick button variant (age, identity, continue, or generic verify); white on black, optional outline.
Avoid:
- Text baked into images, noncritical change messages, deleting passes silently.
Platform notes: watchOS shows passes in a scrolling card carousel with a scrolling details screen and crops strip images; not on tvOS.
Beyond Apple platforms: Ticket/pass UIs on Google Wallet follow similar tiers: critical info in header, concise primary data, push updates only for critical changes.

