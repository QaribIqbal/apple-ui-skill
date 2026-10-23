# Motion and glass recipes

The HIG files say *when* to animate and *where* glass belongs. This file says *how* to build it so it feels native: tested recipes for press feedback, springs, transitions, a Wallet-style card stack and translucent bars.

**These are techniques, not a look.** They carry no colours, fonts or layouts. Each app picks its own palette, type and structure; tint the glass and choose sizes to match that app's design. The numbers below are good starting points; tune them by feel, but keep them consistent within an app (HIG Motion: the same element always moves the same way).

Every recipe has a Reduce Motion or Reduce Transparency fallback. That fallback is required, not optional.

---

## 1. Press feedback (the "Pressable" feel)

Every tappable element (cards, rows, custom buttons, chips) responds while the finger is down, the iOS way: no ripple.

- On touch down: spring the scale to **0.96** and dim opacity to about **0.85**.
- On release or cancel: spring back to 1.0.
- On tap: a light **selection haptic**.
- Spring: mass 1, stiffness **500**, damping **30**. Start each new spring from the current value *and velocity*, so a quick tap-release-tap never jumps (interruptible motion).
- Keep a **44 × 44 pt** minimum hit area even when the visual is smaller.
- Turn off the platform's ripple, splash and hover highlight app-wide so nothing fights it.
- **Reduce Motion:** no scale; just dim to 0.6 while pressed.

Flutter: an `AnimationController.unbounded` driven by `SpringSimulation(SpringDescription(mass: 1, stiffness: 500, damping: 30), value, target, velocity)`, wrapped in `Transform.scale` + `Opacity`; `HapticFeedback.selectionClick()` on tap; `ThemeData(splashFactory: NoSplash.splashFactory, highlightColor: Colors.transparent)`.
SwiftUI: a `ButtonStyle` with `.scaleEffect(isPressed ? 0.96 : 1)`, `.opacity(isPressed ? 0.85 : 1)`, `.animation(.spring(response: 0.28, dampingFraction: 0.7), value: isPressed)` and `.sensoryFeedback(.selection, trigger:)`.
CSS: `transition: transform .25s cubic-bezier(.3,1.4,.6,1), opacity .2s` and `:active { transform: scale(.96); opacity: .85 }`.

## 2. Motion vocabulary

Use one small set of motions everywhere:

| Name | Values | Use |
|---|---|---|
| Press spring | stiffness 500, damping 30 | Press feedback |
| Snappy spring | stiffness 380, damping 32 | Layout changes, selection indicators, expanding content |
| Fade | 200 ms, ease-out | Appearing/disappearing content, state changes |
| Flight | ~300 ms, ease-out cubic | Shared-element transitions |
| Sheet snap | 250 ms, ease-out cubic | Snapping a sheet to a detent |

Also:
- Use the **iOS slide-in page transition** on every platform (Flutter: `CupertinoPageTransitionsBuilder` for Android too), so back-swipe and push feel the same everywhere.
- Use **bounce scrolling with no overscroll glow** (Flutter: a `ScrollBehavior` returning `BouncingScrollPhysics` and no overscroll indicator).
- Use an iOS-style **pull to refresh**.

## 3. Staggered entrance

When a list or grid first loads, each item fades in and rises **8 pt**, starting a little after the one before it (about 40–60 ms apart, capped so long lists don't drag). Run it once on first load, not on every rebuild or scroll.
**Reduce Motion:** show everything at once.

## 4. Shared-element flight (card to details)

When a card opens a details screen, the card's image *becomes* the details header instead of the screen just sliding in.

- Wrap the image on both screens in a shared element (Flutter `Hero`, SwiftUI `matchedGeometryEffect` or `.navigationTransition(.zoom)`, web View Transitions API) with the same tag.
- Animate the **corner radius** during the flight: from the card's radius to 0 for an edge-to-edge header, and back on pop. Flutter: a `flightShuttleBuilder` that wraps the child in a `ClipRRect` whose radius follows the animation (ease-out cubic).
- Allow it during the back-swipe gesture (`transitionOnUserGestures: true`).
- **No reload after landing:** draw the image with the same cache settings on both screens (same URL, same decode width, no fade-in), so the decoded image is reused.
- **Reduce Motion:** skip the flight; use the normal transition.

## 5. Wallet-style card stack

How Apple Wallet shows cards: a vertical stack where each card sits behind the one below it, showing only its top strip.

- Cards keep real card proportions: aspect ratio **1.586** (ISO credit card). Height = available width / 1.586.
- Each card peeks about **64 pt** above the next. Stack height = card height + (count − 1) × peek.
- Paint back to front so the **first card is in front and fully visible at the bottom**, the rest stacked behind it showing their top edges.
- Each card has a soft shadow so the layers read (for example 0 4 14 at about 13% black).
- Each card uses press feedback (§1). **Tap** opens details with a shared-element flight (§4), so the card lifts out of the stack into the details screen. **Touch and hold** opens a menu or action sheet (View offers, Edit, Remove).
- **Loading:** show the same stack layout with plain placeholder cards (three is plenty), so nothing jumps when data arrives.
- **Removing a card:** hide it immediately, show an **Undo toast** (§7), and only delete on the server once the toast expires. Commit pending removals if the app goes to the background.
- Put a short footer hint under the stack: "Tap a card for details. Touch and hold for more options."
- **Reduce Motion:** keep the stack; skip the flight.

## 6. Translucent glass bars and controls

Glass is for the **control layer only**: tab bars, toolbars, floating buttons, sheets, toasts, dialogs and badges over images. Content (cards, lists, text blocks) stays solid. Never stack glass on glass.

**Recipe for a glass surface:**
1. Clip to the shape.
2. Blur what's behind: blur radius (sigma) about **20** (about 8 for thin bars, about 30 for dialogs).
3. Boost the colour of the blurred backdrop: saturation about **1.6–1.8**, so colours behind glow through instead of turning grey.
4. Lay a tint on top: the app's surface colour at about **40–80% opacity**, more opaque where text must be read (dialogs, toasts) and lighter for bars.
5. Add a **1 pt rim**: a gradient stroke from bright (about 55% white) at the top-left to faint (about 8%) at the bottom-right, like light catching an edge.
6. Add a soft shadow underneath: about 0 8 24 at 12% black.
7. Isolate it for repainting (Flutter `RepaintBoundary`) because blur is expensive.

**Floating tab bar** (iOS 26 style): a glass capsule floating above the home indicator, inset from the screen edges (about 20 pt), about 64 pt tall, rather than a bar glued to the bottom edge. The selected tab gets a soft tinted pill behind it. Search can be a separate round glass button at the trailing end. Let content scroll underneath (Flutter `Scaffold(extendBody: true)`) and add bottom padding so the last item clears the bar. A `liquid_glass_widgets` package (Flutter) or the system `TabView` (SwiftUI, iOS 26) does this natively.

**Collapsing large title bar:** a large title that shrinks into the nav bar on scroll, with the bar background slightly translucent (about 85% of the page background) so content shows through as it passes under.

**Floating glass back button:** a 44 pt circular glass button with a chevron, inset about 12 pt from the edge, especially over photo headers.

**Text over photos:** put a dark scrim (about 35% black) inside the glass and use white text, so it stays readable over any image. Inside scrolling lists use a cheap version (scrim + thin light border, no blur) to keep scrolling smooth.

**Bottom action bar:** the screen's main button sits inside a glass capsule floating above the safe area. Keep the corners concentric: inner radius = outer radius − padding.

**Accessibility fallback (required):** when **Reduce Transparency** or **Increase Contrast** is on, every glass surface becomes a solid surface with a hairline border and no blur, and the floating tab bar becomes a standard solid tab bar. Flutter on iOS doesn't expose Reduce Transparency, so read `UIAccessibility.isReduceTransparencyEnabled` through a small method channel in `AppDelegate.swift` and re-check when the app resumes. Use `MediaQuery.highContrastOf` for Increase Contrast. Web: `@media (prefers-reduced-transparency: reduce), (prefers-contrast: more)`. SwiftUI handles it for you.

## 7. Sheets, toasts and dialogs in motion

- **Sheets:** slide up over a dimmed backdrop (about 40% black), with a grabber and two resting heights (about half and nearly full). Dragging the header resizes the sheet. A flick uses its *velocity* to pick the nearest resting height (projected position = current + velocity × 0.15), or dismisses below the lowest. Scroll views inside hand off the drag to the sheet smoothly. **Reduce Motion:** the sheet appears without sliding.
- **Undo toast:** instead of "Are you sure?" for reversible actions. A glass pill floating above the tab bar that fades in and rises about 12 pt. It shows a short message plus **Undo**, lasts about 4 s, and only one is shown at a time. Mark it as a live region so screen readers announce it. **Reduce Motion:** fade only.
- **Alerts** (rare, irreversible choices only): a glass panel over a light dim (about 30% black) that fades in. Buttons are stacked full width, each 44 pt tall.

## 8. Loading

- Use **skeletons shaped like the real content** (a shimmering card shape, a stack of placeholder cards) instead of spinners for lists and pages. Keep the same layout so nothing shifts when data arrives.
- Use spinners only inside buttons (replace the label and disable the button) and for very short waits.
- Show cached content first, then refresh quietly.

## 9. Haptics

Use them lightly and consistently: a selection tick for taps and tab changes, success or warning for completed or failed actions. Never on scroll. Platform haptics respect the user's system settings.
