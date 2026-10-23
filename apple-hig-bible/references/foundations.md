# Foundations — HIG digest
Source pages: 18. Digest written 2026-10-22. Live pages are authoritative when in doubt.

## Accessibility
URL: https://developer.apple.com/design/human-interface-guidelines/accessibility
Essence: Make every interface intuitive, perceivable (no single sensory channel) and adaptable to system settings across vision, hearing, mobility, speech and cognitive needs.
Rules:
- Text size: allow enlarging text at least 200 percent (140 percent on watchOS); use Dynamic Type or equivalent custom scaling.
- Default / minimum text size: iOS and iPadOS 17 / 11 pt; macOS 13 / 10 pt; tvOS 29 / 23 pt; visionOS 17 / 12 pt; watchOS 16 / 12 pt. Thin custom fonts need larger sizes.
- Contrast (WCAG AA values used by Accessibility Inspector): 4.5:1 for text up to 17 pt, 3:1 for 18 pt text and above, 3:1 for any bold text. Check both light and dark appearances; offer a higher-contrast scheme when Increase Contrast is on. APCA is an accepted alternative measure.
- Prefer system colors (they have accessible variants). Never convey info by color alone (red/green, blue/orange are risky): add shapes, icons or labels, and consider letting users customize chart or character colors.
- Label everything for VoiceOver, Voice Control and Switch Control; support Full Keyboard Access and do not override system shortcuts.
- Control size default / minimum: iOS and iPadOS 44x44 / 28x28 pt; macOS 28x28 / 20x20; tvOS 66x66 / 56x56; visionOS 60x60 / 28x28; watchOS 44x44 / 28x28.
- Spacing matters as much as size: about 12 pt padding around bezeled elements, about 24 pt around unbezeled elements' visible edges.
- Use the simplest gestures for frequent actions, avoid custom multi-finger or two-hand gestures, and always provide an on-screen alternative (for example a button beside a swipe-to-dismiss).
- Hearing: offer captions, subtitles, audio descriptions and transcripts as fits the media; pair sounds with haptics and with visual cues (especially for off-screen events).
- Cognitive: keep actions simple and consistent, prefer system gestures, avoid auto-dismissing timed UI (dismiss on explicit action), offer game difficulty options, no autoplay without controls, respect Dim Flashing Lights.
- Reduce Motion: reduce automatic or repeated animation (zoom, scale, peripheral motion); tighten springs, track motion to the gesture, avoid z-depth animation, replace x/y/z transitions with fades, avoid animating into or out of blurs.
- Assistive Access: keep only core functions, one interaction per screen, and require two confirmations for hard-to-undo actions such as deletion.
- Audit with Accessibility Inspector; publish Accessibility Nutrition Labels on the App Store.
Avoid:
- Relying on audio-only, color-only or gesture-only cues; timed auto-dismissals; overriding system keyboard shortcuts; autoplaying media with no controls.
Platform notes: visionOS: keep UI in field of view, prefer horizontal layouts over vertical, slow peripheral animation, do not lock content to the head (blocks Pointer Control), minimize large repetitive gestures.
Beyond Apple platforms: Directly maps to WCAG 2.2 AA and Material accessibility; use 44 pt as a cross-platform touch target floor and the contrast ratios above on web and Flutter.

## App icons
URL: https://developer.apple.com/design/human-interface-guidelines/app-icons
Essence: A simple, distinctive, consistent layered icon that the system masks and lights with Liquid Glass effects.
Rules:
- Supply layers (background plus foreground) rather than a flat image where possible; iOS, iPadOS, macOS and watchOS icons are built in Icon Composer; tvOS (2 to 5 layers) and visionOS (background plus 1 to 2 layers) via Xcode image stacks.
- Layout sizes: iOS, iPadOS, macOS 1024x1024 px square; visionOS 1024x1024 px; watchOS 1088x1088 px; tvOS 800x480 px landscape rectangle. The system scales to smaller sizes.
- Provide unmasked square (or rectangular for tvOS) layers; the system applies rounded or circular masking. Do not pre-round corners. Keep key content centered, especially for circular masks (visionOS, watchOS).
- Foreground layers need crisp, hard edges (no feathering); vary layer opacity for depth; backgrounds should be full-bleed and opaque (solid color or gradient); prefer vector (SVG/PDF) layers with text outlined, PNG for raster or mesh gradients.
- Keep it simple: one core idea, few shapes, simple background; filled overlapping shapes work well; illustrations beat photos; avoid thin lines, sharp corners and UI replicas or screenshots.
- Text in icons only when essential (not "Play", "New"); on tvOS keep text above other layers.
- Do not bake in highlights, drop shadows, bevels, blurs or glows; the system supplies dynamic effects. Group layers to apply effects at group level.
- Appearances on iOS, iPadOS, macOS: default, dark, clear (light/dark), tinted (light/dark). Keep core features consistent across all; dark icons derive from the light icon, avoid excessively bright imagery, and color backgrounds give best dark contrast.
- Keep one visually consistent icon across every platform; alternate icons (iOS, iPadOS, tvOS, visionOS compat) must stay clearly related to the app, and iOS/iPadOS alternates need their own dark/clear/tinted variants.
- Color spaces: sRGB, Gray Gamma 2.2, Display P3 (not on visionOS).
Avoid:
- Replicas of Apple hardware; feathered edges; pre-masked layers; concave "hole" shapes on visionOS backgrounds; pure black backgrounds on watchOS; text-heavy icons.
Platform notes: tvOS needs a safe zone because foreground layers are cropped more than background during focus parallax.
Beyond Apple platforms: Android adaptive icons and web app icons share the same logic (safe zone, simple glyph, system masking).

## Branding
URL: https://developer.apple.com/design/human-interface-guidelines/branding
Essence: Express brand through voice, color and content while staying familiar and letting content lead.
Rules:
- Use the brand's voice and tone in all copy.
- Apply the accent color judiciously: reserve it for primary actions and status indicators (badges, selected tab icon); better to put brand color in the content layer so it shows beneath Liquid Glass controls.
- Custom fonts are fine for headlines and subheads if legible at all sizes and supporting Bold Text and Dynamic Type; keep system fonts for body and captions.
- Build brand expression with standard components; if customized, keep sizing, placement and behavior platform-appropriate.
- Branding defers to content; do not spend screen space on logo-only elements and do not repeat the logo across screens unless it provides context.
- Use standard patterns in expected places (symbols, navigation, modality) even in highly stylized UIs.
- Show brand in onboarding or welcome, not the launch screen (it vanishes too fast).
- Apple trademarks must not appear in the app name or images.
Avoid:
- Brand color on every control; logo-only banners; branded launch screens.
Platform notes: none.
Beyond Apple platforms: Universal: tone, restrained accent color, content first.

## Color
URL: https://developer.apple.com/design/human-interface-guidelines/color
Essence: Use color purposefully and semantically, with adaptive light, dark and increased-contrast variants and wide-gamut awareness.
Rules:
- One color, one meaning: do not reuse the same color for interactive and non-interactive elements, or for different statuses.
- Every custom color needs light and dark variants plus an increased-contrast variant of each (even if the app ships in one appearance, so Liquid Glass can adapt).
- Prefer system and dynamic semantic colors; never hard-code system color values (they change per release); do not repurpose semantic roles (no separator color as text, no secondary label as background).
- Test in sunlight and dim light, on True Tone displays, on different TVs, and in sRGB vs Display P3; colors look darker outdoors, more saturated in the dark.
- Check colors against translucent bars and varying artwork; use system color pickers when users choose colors.
- Inclusive color: never depend on color alone; ensure contrast; check cultural meaning (red, white differ by locale).
- iOS and iPadOS background hierarchy: primary for the overall view, secondary for grouped content in it, tertiary for groups within secondary; use the grouped set for grouped table views, the plain system set otherwise. Foreground roles: label, secondary, tertiary, quaternary, placeholder, separator, opaque separator, link.
- Liquid Glass has no color of its own; it picks up the content behind it. Tint sparingly, only for emphasis such as the primary action, and color the background (not the label) of prominent buttons; do not tint many controls.
- On colorful backgrounds prefer monochrome toolbar and tab bar labels; on neutral content the brand accent works well. Keep content under controls from clashing in its resting state.
- Color management: tag images with a profile; sRGB is the safe default; Display P3 (16 bit per channel PNG) for richer color on supported displays; provide sRGB fallbacks via asset catalog if P3 colors or gradients clip.
- macOS: system accent color multicolor lets your accent show; a user-chosen accent overrides yours except fixed-color sidebar icons; many named dynamic colors exist (label, control, selection, separator, window background).
- 12 system hues: red, orange, yellow, green, mint, teal, cyan, blue, indigo, purple, pink, brown; iOS has six system grays (systemGray through systemGray6).
Avoid:
- Color-only status; overly colorful label colors on busy backgrounds; relying on exact system RGB values.
Platform notes: tvOS: limited palette tied to logo and do not signal focus by color alone (use scale and animation). visionOS: sparing color on glass, prefer bold text and large areas, balance brightness in full immersion. watchOS: background color should carry meaning, avoid full-screen color in long-lived views (workouts), support tinted complications.
Beyond Apple platforms: Same semantic-token approach as design tokens on web and Flutter themes: define surface, label, separator, accent roles with light, dark and high-contrast values.

## Dark Mode
URL: https://developer.apple.com/design/human-interface-guidelines/dark-mode
Essence: Respect the systemwide dark palette so the app is comfortable in low light and always legible.
Rules:
- Follow the system appearance; do not add an app-specific light/dark setting.
- Support Auto switching while the app is running.
- Dark palette is dimmer backgrounds and brighter foregrounds, not a pure inversion; use semantic colors or Color Set assets with bright and dim variants, never fixed values.
- Contrast: minimum 4.5:1; aim for 7:1 for custom foreground and background, especially small text. Test with Increase Contrast and Reduce Transparency on and off, since dark text on dark backgrounds can lose contrast.
- Soften white image backgrounds slightly so they do not glow.
- Use SF Symbols and system label colors (primary through quaternary); use system views for text so vibrancy is handled.
- Make separate light/dark icon or image variants when an asset looks wrong in one mode (for example outline for a moon icon on light, border for oil drop on dark).
- iOS and iPadOS use base (dimmer) and elevated (brighter) backgrounds; elevated applies to popovers, sheets, multitasking neighbors; prefer system backgrounds so the depth cue works.
- macOS: desktop tinting with graphite accent; give neutral-state custom component backgrounds some transparency, but not when the component is in a colored state.
- A permanently dark UI is acceptable for immersive media.
Avoid:
- Per-app appearance toggles; hard-coded colors; assuming dark is inverted light.
Platform notes: Dark Mode not supported on visionOS or watchOS (visionOS glass adapts to surroundings).
Beyond Apple platforms: Use prefers-color-scheme; follow OS setting; lift elevated surfaces lighter rather than using shadows alone.

## Icons
URL: https://developer.apple.com/design/human-interface-guidelines/icons
Essence: Interface icons (glyphs) express one simple concept and stay consistent in size, weight and detail.
Rules:
- Highly simplified, familiar metaphors tied directly to the action.
- Keep size, level of detail, stroke weight and perspective consistent across the set; match icon weight to adjacent text.
- Optically center asymmetric icons by adding padding in the asset.
- Do not make selected-state versions for standard system bars and buttons; the system does it.
- Use gender-neutral figures; avoid culture-specific imagery.
- Text in icons only when essential; localize characters; for abstract text blocks provide a flipped RTL version.
- Make custom glyphs as vector (PDF or SVG); PNG needs multiple scales. Provide accessibility labels.
- Use standard SF Symbols for common actions: cut scissors, copy document.on.document, paste document.on.clipboard, done checkmark, cancel xmark, delete trash, undo arrow.uturn.backward, redo arrow.uturn.forward, compose square.and.pencil, duplicate plus.square.on.square, rename pencil, move folder, attach paperclip, add plus, more ellipsis, select checkmark.circle, search magnifyingglass, filter line.3.horizontal.decrease, share square.and.arrow.up, print printer, account person.crop.circle, like hand.thumbsup, dislike hand.thumbsdown, alarm, archive archivebox, calendar.
- macOS document icons: folded-corner shape; supply background fill and optional center image (half the canvas, occupying about 80 percent of it with a 10 percent margin); sizes from 16x16 up to 512x512 at @1x/@2x; keep the top-right corner free; simplify small sizes.
Avoid:
- Apple hardware replicas; busy details; mixing stroke weights.
Platform notes: Document icons are macOS only.
Beyond Apple platforms: The standard symbol mapping is a good vocabulary for icon choice anywhere; keep a single stroke weight across the set.

## Images
URL: https://developer.apple.com/design/human-interface-guidelines/images
Essence: Deliver correctly scaled, formatted and color-profiled artwork for each device.
Rules:
- Points abstract pixels; provide scale factors: iOS @2x and @3x; iPadOS and watchOS @2x; macOS and tvOS @1x and @2x; visionOS @2x or higher (vector preferred).
- Design at lowest resolution; align vector control points to whole values at 1x.
- Formats: PNG (de-interlaced) for raster, 8-bit palette PNG when full color is not needed, JPEG or HEIC for photos, stereo HEIC for spatial photos, PDF or SVG for flat/interface icons.
- Embed a color profile in every image; test on real devices.
- tvOS: layered images (2 to 5 layers) enable parallax; app icon must be layered; keep background opaque, text in the foreground, subtle depth, and leave a safe zone.
- visionOS: prefer vector; rasters above @2x need quality filtering, over @6x hurts performance; spatial photos belong in standalone views, text over them uses feathered glass.
- watchOS: avoid transparency except for template images; use autoscaling PDFs designed for 40/42 mm at 2x (scale 38mm 90%, 41mm 106%, 44mm 110%, 45/49mm 119%).
Avoid:
- Shipping @1x only; inline spatial photos mixed with content; many simultaneous spatial scenes.
Platform notes: see rules above.
Beyond Apple platforms: Same as responsive images: srcset or density buckets, vectors for icons, embedded color profile, WebP/HEIC for photos.

## Immersive experiences
URL: https://developer.apple.com/design/human-interface-guidelines/immersive-experiences
Essence: visionOS guidance for Full Space, immersion styles, comfort and custom environments.
Rules:
- Offer immersion styles by need: dimmed passthrough, mixed (unbounded), progressive (default range 120 to 360 degrees, Digital Crown adjustable), full (360 degrees, replaces passthrough).
- Progressive and full define roughly a 1.5 m boundary around the head; going past it fades the experience.
- Launch in the Shared Space or mixed style by default; reserve immersion for meaningful moments; let users choose when to enter and exit with a clear, labeled exit control.
- Use subtle cues (dimming, tint, motion, spatial audio) to guide attention; keep passthrough tints subtle.
- Do not require movement; avoid obscuring too much passthrough in mixed style; make transitions gentle.
- Virtual hands: match real hand gestures, not oversized; fade to real hands if tracking drops.
- Environments: expansive, minimal distracting motion, ground plane, spatial audio without heavy looping, mesh with lighting over flat 360 images, avoid repeated assets.
Avoid:
- Sudden immersion changes, forcing physical movement, fully immersive launch by default.
Platform notes: visionOS only.
Beyond Apple platforms: Applies to VR and AR apps generally (comfort, exit control, grounding).

## Inclusion
URL: https://developer.apple.com/design/human-interface-guidelines/inclusion
Essence: Respectful, plain, accessible, culturally aware content and functionality for everyone.
Rules:
- Examine copy and imagery from varied perspectives (age, gender, race, ability, culture, language, religion, economics); inoffensive is not the same as inclusive.
- Address people as "you"; avoid "the user"; reserve "we" for your company.
- Avoid unexplained jargon, colloquialisms and idioms; use humor carefully.
- Avoid unnecessary gender references and use gender-neutral nouns and nongendered figures; if gender is needed offer nonbinary, self-identify, decline to state.
- Show diverse people and relatable settings; avoid stereotypes (including in security questions and family assumptions).
- Treat disability as a spectrum, including temporary and situational; use people-first language.
- Prepare for internationalization: language and region formats; use SF Symbols for locale-aware glyphs; check color meanings per culture.
- Provide onboarding that can be skipped.
Avoid:
- Stereotypes; culture-bound references; disability as negative metaphor.
Platform notes: none.
Beyond Apple platforms: Directly reusable for UX writing and imagery review.

## Layout
URL: https://developer.apple.com/design/human-interface-guidelines/layout
Essence: Establish hierarchy and adapt gracefully to size, orientation, text size and locale using safe areas, guides and size classes.
Rules:
- Order by importance: top and leading side first (reading order); align items to aid scanning, indent to show subordination, group with space, containers or separators.
- Use progressive disclosure (disclosure triangles, menus, nested views) to reduce initial content.
- Separate controls from content with Liquid Glass and scroll edge effects, not solid background bars; extend full-screen backgrounds under sidebars, toolbars and tab bars; use background extension effect if panels hide key image areas.
- Use size classes (compact or regular, horizontal and vertical), not device type or orientation, to choose layout; consider all combinations.
- Do not change functionality with size, only how much is visible (for example tab bar to sidebar at larger widths).
- Respect safe areas and system margins; use system layout guides for readable text widths.
- Support Dynamic Type: stack horizontal items vertically, let rows grow, avoid truncation, reduce columns at large sizes.
- Preview with the smallest and largest layouts, different locales and text sizes. Scale background art to fill rather than changing aspect ratio.
- tvOS: inset primary content 60 pt top and bottom, 80 pt sides. Grid widths (unfocused): 2 columns 860 pt, 3 columns 560, 4 columns 410, 5 columns 320, 6 columns 260, 7 columns 217, 8 columns 184, 9 columns 160; horizontal spacing 40 pt, minimum vertical spacing 100 pt; keep spacing consistent; allow room for focus scaling.
- visionOS: support resizing, keep content horizontally centered at large sizes, set min/max sizes only to prevent overlap (not to block resizing), keep button centers at least 60 pt apart, supplemental content in adjacent window not ornaments.
- watchOS: no more than three glyph buttons or two text buttons in a row; support autorotation for showing QR codes or images.
- macOS: do not put controls or critical info at the window bottom edge; avoid content behind the camera housing.
Avoid:
- Fixed widths, solid bars under glass controls, layouts keyed to device idiom or orientation.
Platform notes: see rules above.
Beyond Apple platforms: Maps to responsive breakpoints driven by available container width, safe-area insets (CSS env()), readable line length, and RTL-aware (logical) alignment.

## Materials
URL: https://developer.apple.com/design/human-interface-guidelines/materials
Essence: Use Liquid Glass for the control and navigation layer and standard blur/vibrancy materials for structure in the content layer.
Rules:
- Liquid Glass is a floating functional layer (tab bars, sidebars, toolbars); never use it in the content layer, except transient controls like sliders and toggles that adopt it while active.
- Use custom Liquid Glass sparingly and only on the most important functional elements; standard components adopt it automatically.
- Regular variant: blurs and adjusts luminosity for legibility; use where text is heavy (alerts, sidebars, popovers). Clear variant: highly translucent, only over visually rich media backgrounds; add a dark dimming layer of about 35 percent opacity if content behind is bright.
- Standard materials: choose by semantic purpose, not by apparent color; use system vibrant colors on top; thicker is more opaque for contrast, thinner shows more context.
- iOS and iPadOS: four materials (ultraThin, thin, regular default, thick); label vibrancy levels (label, secondary, tertiary, quaternary), fill levels (fill, secondary, tertiary), one separator level; avoid quaternary on thin and ultraThin.
- tvOS materials: ultraThin for full-screen light, thin for overlays needing light, regular for overlays, thick for overlays needing dark.
- visionOS: glass window material is fixed; prefer translucency over opaque colors; thin for interactive/selected items, regular for sidebars/groups, thick for dark elements atop regular; vibrancy levels label, secondaryLabel, tertiaryLabel (inactive only).
- watchOS: keep default material backgrounds on full-screen modals.
Avoid:
- Glass on content; stacking many custom glass controls; choosing materials by color.
Platform notes: macOS offers behind-window or within-window blending modes.
Beyond Apple platforms: Web equivalent is backdrop-filter blur with a scrim; keep text contrast checks over blurred layers and respect reduced-transparency settings.

## Motion
URL: https://developer.apple.com/design/human-interface-guidelines/motion
Essence: Purposeful, brief, cancelable animation that follows gestures and respects user comfort.
Rules:
- Add motion only when it supports the task; never as the sole carrier of information (back with haptics or audio).
- Feedback motion should be realistic and consistent with gestures (a view that slides down dismisses upward, not sideways).
- Keep feedback animations short and precise; avoid animating high-frequency interactions; let people cancel or skip motion.
- Use animated SF Symbols where appropriate.
- Games: target a steady 30 to 60 fps; allow performance and battery options.
- visionOS: avoid motion at the edges of vision, make large moving objects more translucent or lower contrast, fade-out/in instead of moving objects, never rotate the virtual world, provide a stationary frame of reference, avoid sustained oscillation near 0.2 Hz.
Avoid:
- Gratuitous animation; forcing waits; screen-wide movement without reference.
Platform notes: watchOS animations always include built-in easing.
Beyond Apple platforms: Honor prefers-reduced-motion; keep UI transitions short and interruptible.

## Privacy
URL: https://developer.apple.com/design/human-interface-guidelines/privacy
Essence: Ask for only what is needed, at the right moment, with honest explanation, and protect stored data.
Rules:
- Request the minimum data; defer requests until the user reaches a feature that needs it; ask at launch only when the app obviously cannot work without it.
- Permission purpose strings: one short, specific, active-voice sentence in sentence case with a period (good: what is recorded and why; bad: vague passive or imperative).
- Pre-alert screens: a single button labeled "Continue" or "Next" (never "Allow"), no cancel or skip, no extra actions except legal consent. For tracking, no incentives, fake request lookalikes, images of the alert or annotations.
- Use the system location button for one-time location sharing; customization is limited (title, glyph fill, colors, corner radius) and text must fit at all accessibility sizes and languages.
- Process data on device where possible; use passkeys, Sign in with Apple, or password autofill; add 2FA and biometrics; store secrets in keychain; never plain text; do not invent custom authentication.
- Disclose data practices in App Store privacy details.
Avoid:
- Manipulative pre-permission screens; asking for permissions upfront; plain-text secrets.
Platform notes: macOS: sign with Developer ID, sandbox (required on Mac App Store), do not assume a single signed-in user. visionOS: ARKit data only in Full Space with permission; eye input is private by design.
Beyond Apple platforms: Same principles for Android runtime permissions and web permission prompts (contextual ask, explain why).

## Right to left
URL: https://developer.apple.com/design/human-interface-guidelines/right-to-left
Essence: Mirror the interface for Arabic and Hebrew without breaking numbers, media and universal symbols.
Rules:
- Use system components and standard layouts so mirroring is automatic.
- Align text to the interface direction; align a paragraph of three or more lines to its own language; align all items in a list the same way.
- Never reverse digits inside a number (phone, card, "541"); reverse the order of numerals shown as a progress or counting sequence.
- Flip progress controls (sliders, progress bars) and their end glyphs; flip back/next/previous navigation (back points right); do not flip a control that names a literal direction.
- When Arabic or Hebrew sits next to all-caps Latin, increase the RTL font size by about 2 pt for visual balance.
- Do not flip photos, illustrations or art; reverse the order of ordered image sets (chronological, alphabetical).
- Flip icons that depict text or reading direction, or forward/backward motion; localize icons that contain letters; do not flip logos, checkmarks, universal signs, clocks or real-world objects (handed tools stay).
- For complex custom icons, flip components selectively (badges that mirror real UI flip; prohibition slash keeps its direction).
- SF Symbols provide RTL and Arabic/Hebrew variants; custom symbols can declare directionality.
Avoid:
- Flipping logos or images; reversing digit order; fixed left/right alignment.
Platform notes: none.
Beyond Apple platforms: Use logical CSS properties (start/end), Flutter Directionality, and mirror only directional icons; essential reference for Urdu/Arabic apps.

## SF Symbols
URL: https://developer.apple.com/design/human-interface-guidelines/sf-symbols
Essence: A large, font-aligned symbol library with rendering modes, weights, scales, variants and animations.
Rules:
- Four rendering modes: monochrome (one color), hierarchical (one color, varied opacity by layer), palette (two or more colors by layer), multicolor (intrinsic colors). Check legibility in each context; use system colors for automatic adaptation.
- Gradient rendering (SF Symbols 7+) looks best at larger sizes.
- Variable color shows changing values (volume, strength) across thresholds, not depth; use hierarchical for depth.
- Nine weights (ultralight to black) match San Francisco font weights; three scales (small, medium default, large) relative to cap height; scale adjusts emphasis without breaking weight matching.
- Variants: outline (default, for toolbars and lists), fill (emphasis, iOS tab bars, selection), slash (unavailable), enclosed (circle, square; better at small sizes); views often choose the variant automatically.
- Animations: appear, disappear, bounce, scale, pulse, variable color, replace (down-up, up-up, off-up), Magic Replace (default), wiggle, breathe, rotate, draw on/off (v7). Use sparingly, each with a clear purpose and matching tone.
- Custom symbols: start from the template, match detail, weight, alignment and perspective; annotate layers for rendering and animation; draw whole shapes (erase layers for cutouts); use negative side margins for badges; provide alt text; avoid baking in enclosures or badges (use component library).
- Terms: cannot use symbols in app icons, logos or trademarked uses; Apple product symbols cannot be customized; no Apple hardware replicas.
Avoid:
- Overusing animation; symbols as app icon art.
Platform notes: Feature availability depends on OS version.
Beyond Apple platforms: Pairing icon weight to text weight and using filled-for-selected, outline-for-default is a portable pattern.

## Spatial layout
URL: https://developer.apple.com/design/human-interface-guidelines/spatial-layout
Essence: visionOS guidance on field of view, depth, scale and spacing.
Rules:
- Keep important content centered in the field of view; do not anchor content to the head; anchor it in space.
- Use depth to show hierarchy and in small amounts; avoid depth on text; do not apply depth to small buttons; changing depth too often tires eyes.
- Dynamic scale keeps windows looking the same size at any distance; fixed scale only for non-interactive, life-size objects. A visionOS point is an angle.
- Limit window count; favor indirect gestures; direct gestures only for nearby, brief interactions.
- Space interactive elements: button centers at least 60 pt apart with at least 16 pt gap; do not overlap controls.
- Let people use the app with minimal movement; the Digital Crown recenters content.
- Align large immersive content to the floor plane.
Avoid:
- Too many windows; text with depth; head-locked content.
Platform notes: visionOS only.
Beyond Apple platforms: Generic AR/VR comfort rules.

## Typography
URL: https://developer.apple.com/design/human-interface-guidelines/typography
Essence: Use system type styles (San Francisco, New York) with legible sizes, clear hierarchy and full Dynamic Type support.
Rules:
- Default / minimum sizes: iOS and iPadOS 17 / 11 pt; macOS 13 / 10; tvOS 29 / 23; visionOS 17 / 12; watchOS 16 / 12.
- Avoid ultralight, thin and light weights; prefer regular, medium, semibold, bold.
- Establish hierarchy with weight, size and color; minimize the number of typefaces; keep relative hierarchy when text grows; do not scale every element equally (tab titles may stay fixed).
- System fonts: SF Pro (iOS, iPadOS, macOS, tvOS, visionOS), SF Compact (watchOS; SF Compact Rounded in complications), SF Mono, SF Arabic/Hebrew/Armenian/Georgian, rounded variants, and New York serif. Variable fonts with dynamic optical sizes; do not embed, access via system APIs.
- Use built-in text styles; modify with symbolic traits (bold, loose or tight leading). Loose leading for wide columns or long passages; tight leading acceptable only for fewer than three lines.
- iOS and iPadOS Dynamic Type at the default Large size (size/leading pt, weight): Large Title 34/41 Regular; Title 1 28/34; Title 2 22/28; Title 3 20/25; Headline 17/22 Semibold; Body 17/22 Regular; Callout 16/21; Subhead 15/20; Footnote 13/18; Caption 1 12/16; Caption 2 11/13. Smallest (xSmall): Body 14/19, Large Title 31/38. Largest standard (xxxLarge): Body 23/29, Large Title 40/48. Accessibility sizes AX1 to AX5: Body 28/34, 33/40, 40/48, 47/56, 53/62; Large Title up to 60/70.
- macOS styles (size/line height): Large Title 26/32; Title 1 22/26; Title 2 17/22; Title 3 15/20; Headline 13/16 Bold; Body 13/16; Callout 12/15; Subheadline 11/14; Footnote 10/13; Caption 1 and 2 10/13. macOS has no Dynamic Type.
- tvOS styles: Title 1 76/96 Medium; Title 2 57/66; Title 3 48/56; Headline 38/46; Subtitle 38/46 Regular; Callout 31/38; Body 29/36; Caption 1 25/32; Caption 2 23/30.
- watchOS (default Large, 40/41/42mm): Large Title 36; Title 1 34; Title 2 28; Title 3 19; Headline 16 Semibold; Body 16; Caption 1 15; Caption 2 14; Footnote 1 13; Footnote 2 12 (leading about size + 2.5).
- Tracking (SF Pro): changes with size, for example 11 pt +6, 12 pt 0, 13 pt -6, 15 pt -16, 17 pt -26, 20 pt -23, 24 pt +3, 28 pt +14, 34 pt +12 (per 1/1000 em), approaching 0 at 80 pt and above; use these in mockups only, as the system adjusts tracking automatically.
- Custom fonts must be legible, honor Bold Text and Dynamic Type, and meet the same minimum sizes.
- Dynamic Type adaptation: layout must work at all sizes including accessibility sizes; scale meaningful icons; minimize truncation (aim to show as much useful text at the largest accessibility size as at the largest standard one); stack inline items below text; reduce columns; keep primary elements at top.
- Emphasized weights per style are available (medium, semibold, bold or heavy).
Avoid:
- Thin weights at small sizes; many typefaces; truncating scrollable text; shadows on text to boost contrast on visionOS.
Platform notes: visionOS uses bolder body and title styles, adds Extra Large Title 1 and 2, prefers 2D text, white default text, billboarding labels toward the viewer. macOS provides dynamic system font variants (control, label, menu, tool tips, user fixed pitch).
Beyond Apple platforms: Port the scale (17 pt body, 1.2-ish ratios, roughly 22 pt leading at 17 pt), weight guidance and Dynamic Type behavior to web (rem units, user zoom) and Flutter (textScaler).

## Writing
URL: https://developer.apple.com/design/human-interface-guidelines/writing
Essence: Clear, consistent, human, action-oriented UI copy matched to context and device.
Rules:
- Define voice and a term list; adjust tone to the situation (serious for errors, light for achievements).
- Be brief and plain; read it aloud; avoid jargon and gendered terms.
- Put the most important information first; one idea per screen.
- Buttons and links start with a verb; "Send" beats "Let's do it!"; never "Click here"; use descriptive link text.
- Choose a capitalization style per element type (title case is formal, sentence case casual) and keep it.
- Multi-step flows: "Get Started" to begin, a consistent "Continue" or "Next", "Done" to end.
- Use possessives sparingly ("Favorites" not "Your Favorites"); avoid "we" in errors ("Unable to load content").
- Use device-appropriate verbs (tap vs click) and brevity for small and far screens.
- Empty states: explain and offer a next-step button; do not put permanent info there.
- Errors: next to the problem, no blame, say how to fix ("Choose a password with at least 8 characters"); skip "oops".
- Settings labels: practical; explain what turning on does; link directly to settings instead of describing the path.
- Text fields: clear labels, hint or placeholder with an example, inline instructive errors ("Use only letters for your name", not "Invalid name").
- Pick the delivery method by urgency (notification, alert, action sheet).
Avoid:
- Cute labels, blame, vague errors, "we".
Platform notes: none.
Beyond Apple platforms: Fully portable microcopy guide.
