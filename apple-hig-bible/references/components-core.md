# Components — content, layout, navigation, presentation, selection & input, status — HIG digest
Source pages: 42. Digest written 2026-10-22. Live pages are authoritative when in doubt.

# Content
## Charts
URL: https://developer.apple.com/design/human-interface-guidelines/charts
Essence: Building blocks and accessibility rules for individual charts.
Rules:
- Vocabulary: marks (bar, line, point) on a scale inside a plot area, with axes, ticks, grid lines, labels, titles/subtitles/annotations, and a legend for non-positional encodings.
- Bars compare categories or parts of a whole (and sums over time); lines show change over time/trends; points show relationships, outliers, clusters. Combine line plus points to show trend and individual values.
- Axis range: fixed when bounds are meaningful (battery 0-100%), dynamic when data varies widely. Bars should start at zero; for data far from zero (heart rate) a non-zero lower bound may reveal differences.
- Use familiar tick sequences (0, 5, 10), not 1, 6, 11. Keep grid-line density low when the chart is interactive so data stays prominent.
- Establish hierarchy: data most prominent, axes and descriptions secondary.
- In compact widths, maximize plot width, keep vertical axis labels short, move units into the title.
- Interactivity is optional enrichment; critical information must not require interaction. Expand hit targets to the whole plot area (scrubbing) when marks are tiny.
- Support keyboard/Switch Control with a logical navigation order or subset-level focus for large datasets.
- Highlight changes beyond animation (VoiceOver, reduced motion).
- Align the chart's leading edge with surrounding views; put gridline labels on the trailing side to keep that edge clean.
- Do not rely on color alone: add shapes/patterns; separate adjacent color areas (stacked bars) with separators.
- Accessibility: provide an overview (chart type, what axes mean, bounds) or Audio Graphs; label individual marks only when the purpose is exact values, otherwise summarize groups; use real values not "rapidly/gradually"; spell out dates and units ("June 6", "60 minutes"); describe meaning, not colors; be consistent about axis order; hide visible axis and tick text from assistive tech.
Avoid:
- Zero baseline that hides meaningful variation; subjective wording in labels.
Platform notes: watchOS - keep to glanceable charts with simple interaction.
Beyond Apple platforms: Chart anatomy and accessibility advice apply to any charting library.

## Image views
URL: https://developer.apple.com/design/human-interface-guidelines/image-views
Essence: Displaying a non-interactive image or animated sequence.
Rules:
- Use an image view when the main purpose is displaying an image; for interactive images use a system button holding the image.
- For icons prefer SF Symbols or interface icons (they take accent color) over bitmap image views.
- Ensure text over images contrasts well; add a shadow or background layer.
- Prescale and use equal sizes for all frames of an animation.
- macOS: image well for editable image; image button for clickable. tvOS: layered images for depth.
Avoid:
- Adding button behavior to a plain image view.
Platform notes: watchOS - prefer SwiftUI animation.
Beyond Apple platforms: Same advice for overlay text legibility and uniform frame sizes.

## Text views
URL: https://developer.apple.com/design/human-interface-guidelines/text-views
Essence: Multiline, optionally editable styled text.
Rules:
- Use for long, editable or specially formatted text; use a label or text field for short text.
- Default alignment is leading with the system label color.
- Keep text legible; support Dynamic Type and test with Bold Text.
- Make useful text (error messages, serial numbers, IP addresses) selectable and copyable.
- iOS/iPadOS: show the keyboard type matching the content.
- tvOS: use text fields for editable text (text views are display-only).
Avoid:
- Decorative style that hurts readability.
Platform notes: as above.
Beyond Apple platforms: Same for textarea and selectable text on web.

## Web views
URL: https://developer.apple.com/design/human-interface-guidelines/web-views
Essence: Embedding web content inside an app.
Rules:
- Provide forward/back navigation (not default) when users may visit multiple pages.
- Use for brief in-context access, not as a custom browser.
Avoid:
- Rebuilding Safari.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: Applies to in-app browsers/WebView in Flutter and Android.

# Layout and organization
## Boxes
URL: https://developer.apple.com/design/human-interface-guidelines/boxes
Essence: A bordered or tinted group for related content.
Rules:
- Keep boxes small relative to the container; near window-size boxes lose meaning.
- Use padding and alignment for subgroups, not nested boxes.
- Optional short title in sentence case without end punctuation (colon in a settings pane); it helps VoiceOver.
Avoid:
- Nested boxes that make the UI busy.
Platform notes: iOS/iPadOS use secondary/tertiary background; macOS puts the title above. Not on tvOS/watchOS.
Beyond Apple platforms: Cards/grouped sections should follow the same restraint.

## Collections
URL: https://developer.apple.com/design/human-interface-guidelines/collections
Essence: Ordered, visual grids/rows for image-based content.
Rules:
- Use the standard row or grid; avoid custom layouts.
- Use a list/table instead for text-heavy content.
- Give items adequate padding so focus/hover effects are visible and nothing overlaps.
- Defaults: tap select, long-press edit, swipe scroll; add custom gestures only if needed.
- Animate insert, delete and reorder.
- iOS: avoid dynamic layout changes while people are interacting unless user-triggered.
Avoid: Surprising layout shifts.
Platform notes: Not on watchOS.
Beyond Apple platforms: Same for photo grids and carousels.

## Column views
URL: https://developer.apple.com/design/human-interface-guidelines/column-views
Essence: macOS browser with one column per hierarchy level.
Rules:
- Use for deep hierarchies navigated back and forth when sorting is not needed.
- Root level in the first column; show a preview/info for leaf selections; let people resize columns.
Avoid: n/a.
Platform notes: macOS only; use split views on iPadOS/visionOS.
Beyond Apple platforms: Miller columns for file/category browsers on desktop web.

## Disclosure controls
URL: https://developer.apple.com/design/human-interface-guidelines/disclosure-controls
Essence: Show or hide secondary details.
Rules:
- Keep most-used controls always visible; hide advanced ones by default.
- Disclosure triangle: points toward the leading edge when collapsed, down when open; label it with what it reveals ("Advanced Options").
- Disclosure button: points down when collapsed, up when open; place it next to the content it expands; at most one per view.
- iOS/iPadOS/visionOS use DisclosureGroup.
Avoid: Multiple disclosure buttons in one view.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: Accordions/expanders with descriptive labels.

## Labels
URL: https://developer.apple.com/design/human-interface-guidelines/labels
Essence: Static, non-editable text.
Rules:
- Use for small read-only text; text field for small editable, text view for long text.
- Prefer system fonts and Dynamic Type.
- Four label shades convey importance: label (primary), secondary (subheading), tertiary (unavailable items), quaternary (watermark).
- Make useful text (errors, locations, IPs) selectable.
- watchOS: use date/time/timer text components that self-update and fit space.
Avoid: Custom fonts that harm legibility.
Platform notes: as above.
Beyond Apple platforms: Establish a 3-4 step text color ladder.

## Lists and tables
URL: https://developer.apple.com/design/human-interface-guidelines/lists-and-tables
Essence: Rows (and columns) of scannable data for browsing, selecting, editing.
Rules:
- Prefer rows for text; use collections for varied-size or image-heavy items.
- Allow editing/reordering where sensible; iOS requires edit mode for multi-selection.
- Selection feedback: navigation lists keep the row highlighted; option lists flash briefly then show a checkmark.
- Keep row text short; truncate in the middle when beginning and end matter; show only titles when bodies are long and open a detail view.
- Multicolumn tables: headings are nouns or short noun phrases with no ending punctuation; single-column tables need a label/header for context.
- Choose list style to fit (iOS grouped style with headers/footers; watchOS elliptical; macOS bordered with alternating rows).
- iOS/iPadOS/visionOS: info button only reveals more info; use the disclosure indicator for drill-down; do not combine an alphabetical index with trailing controls.
- macOS: click heading to sort (click again reverses), resizable columns, alternating row colors, outline view for hierarchy.
- tvOS: account for row focus scaling and rounded corners (do not mask).
- watchOS: limit rows, constrain detail view length for vertical paging.
Avoid: Over-large rows with long text; index plus trailing disclosure controls.
Platform notes: as above.
Beyond Apple platforms: Core of any data list; sorting, truncation and selection rules carry over.

## Lockups
URL: https://developer.apple.com/design/human-interface-guidelines/lockups
Essence: tvOS focus units (content view, header, footer): cards, caption buttons, monograms, posters.
Rules:
- Leave enough space as a focused lockup expands; use consistent sizes in a row.
- Caption buttons tilt with swipe direction; monograms prefer photos over initials; posters show title/subtitle only on focus.
Avoid: n/a.
Platform notes: tvOS only.
Beyond Apple platforms: Apple-only.

## Outline views
URL: https://developer.apple.com/design/human-interface-guidelines/outline-views
Essence: macOS hierarchical table with disclosure triangles.
Rules:
- Expose hierarchy in the first column only; use a table for flat data.
- Column headings are nouns/short noun phrases without colon; required for multi-column views.
- Sorting by the primary column sorts at every level; clicking again reverses.
- Resizable columns; Option-click a triangle expands all descendants; remember expansion state.
- Single-click may edit while double-click opens; use middle-ellipsis truncation, alternating rows, and a toolbar search field for long outlines.
Avoid: Hierarchy in non-primary columns.
Platform notes: macOS only.
Beyond Apple platforms: Tree grids on web.

## Split views
URL: https://developer.apple.com/design/human-interface-guidelines/split-views
Essence: Adjacent panes showing hierarchy levels or supplementary tools.
Rules:
- Persistently highlight the current selection in each leading pane.
- Consider drag and drop between panes.
- iOS: use only in regular width; iPadOS: two or three panes, plan for narrow/compact/intermediate widths.
- macOS: sensible min/max pane sizes so the divider stays visible; allow hiding panes with several ways to restore; prefer the thin 1 pt divider.
- tvOS: one-third/two-thirds default (or half-half); one title above the whole view.
- visionOS: prefer a split view over a new window for supplementary info.
- watchOS: show the most relevant detail first; vertical tab view for multiple details.
Avoid: Split views in compact width.
Platform notes: as above.
Beyond Apple platforms: Master-detail layouts collapse to stacked navigation on narrow screens.

## Tab views
URL: https://developer.apple.com/design/human-interface-guidelines/tab-views
Essence: macOS mutually exclusive panes with a tabbed control.
Rules:
- Use for closely related content; controls within a pane affect only that pane.
- Label tabs with nouns, Title Case.
- No pop-up button to switch tabs (two clicks, hides options) unless too many panes; max six tabs.
- Inset the tab view with a margin; the tab strip may be hidden for programmatic switching.
- iOS/iPadOS: use a segmented control instead.
Avoid: More than six tabs.
Platform notes: macOS (and watchOS paging).
Beyond Apple platforms: Same as web tab panels.

# Navigation and search
## Path controls
URL: https://developer.apple.com/design/human-interface-guidelines/path-controls
Essence: macOS display of a file path, standard (linear) or pop-up style.
Rules:
- Put it in the window body (e.g. bottom of the body), not in a toolbar or status bar.
- If editable, support dragging an item onto it.
Avoid: Placing it in the window frame.
Platform notes: macOS only.
Beyond Apple platforms: Breadcrumbs belong in content, not chrome.

## Search fields
URL: https://developer.apple.com/design/human-interface-guidelines/search-fields
Essence: Text entry with search icon, clear button and placeholder for finding content.
Rules:
- Placeholder text states what can be searched.
- Search as people type; show recent searches and live suggestions.
- Put the most relevant results first and categorize them; offer a scope bar to filter.
- Scope bar: default to the broad scope and let people narrow it (entire mailbox, then this mailbox). Tokens turn terms into editable filter chips; pair with suggestions so people discover them.
- iOS placement: search as a tab in the tab bar (standard tab with landing page for discovery-rich apps; button appearance that focuses the field with keyboard immediately for quick lookups); bottom toolbar if room (preferred when search is a priority); top toolbar when bottom content must stay uncovered; inline field when search applies to a single list (position above the list, pin on scroll).
- iPadOS/macOS: field at trailing end of toolbar for split-view apps; at top of a sidebar to filter sidebar content; as a sidebar/tab item for a dedicated discovery area, auto-focused (except iPad with only the virtual keyboard); keep placement consistent across iPad and Mac and adapt on narrow windows.
- tvOS: provide suggestions (little typing). watchOS: tapping opens a full-screen input.
Avoid: Hiding search in a place unrelated to its scope.
Platform notes: as above.
Beyond Apple platforms: Search-as-you-type, suggestions, filter chips and scoped placeholders carry over to any app.

## Sidebars
URL: https://developer.apple.com/design/human-interface-guidelines/sidebars
Essence: Leading-side navigation for top-level areas or collections.
Rules:
- Prefer a tab bar first on iPhone/iPad; use an adaptable tab bar/sidebar when many areas exist.
- Show at most two levels of hierarchy; use disclosure controls for large content; deeper hierarchies need a split view with a content list.
- Group titles short and descriptive.
- Let people customize and (usually) hide the sidebar, but never hide it by default (discoverability); provide edge swipe on iPad, button or View-menu commands on macOS.
- Use familiar SF Symbols for items (custom symbols rather than bitmaps).
- Icons follow the accent color (including the macOS system accent); use fixed colors sparingly for meaning.
- Let rich content extend beneath the floating sidebar (horizontal scroll or background extension effect).
- macOS: row height scales with small/medium/large size setting; auto-collapse on narrow windows; do not put critical items at the bottom.
- visionOS: a sidebar inside a tab for secondary navigation must not change the active tab.
Avoid: Critical actions at the bottom of a macOS sidebar.
Platform notes: Not on watchOS.
Beyond Apple platforms: Left nav drawers on desktop web follow the same two-level and collapse rules.

## Tab bars
URL: https://developer.apple.com/design/human-interface-guidelines/tab-bars
Essence: Top-level section navigation that preserves each section's state.
Rules:
- Navigate, don't act: use a toolbar for actions.
- Keep the tab bar visible during navigation (only a modal may cover it).
- Fewer tabs are easier (iPhone shows about five; extras fold into a More tab, which you should avoid).
- Never disable or hide a tab, even if empty; explain why content is unavailable.
- Include labels, single words where possible, title case, plus a recognizable SF Symbol (filled variants preferred); icons sit above labels in compact width, beside in regular.
- Badge (red oval with number or "!") only for critical new information.
- Avoid tab label/accent colors similar to bright content behind the translucent bar; consider monochrome.
- iOS: floating Liquid Glass bar; may minimize on scroll with an accessory (e.g. mini player); optional trailing search tab.
- iPadOS: bar near top, optionally convertible to sidebar; let people customize tabs, default five or fewer.
- tvOS: bar is 68 pt tall, 46 pt from the top (fixed); live-viewing order is Live, recorded, other.
- visionOS: vertical bar, symbol plus short label for every tab.
Avoid: Overflow tabs; action buttons in the bar.
Platform notes: As above; macOS none; not watchOS.
Beyond Apple platforms: Bottom nav on Android/Flutter: 3-5 destinations, always-visible labels, no disabled destinations.

## Token fields
URL: https://developer.apple.com/design/human-interface-guidelines/token-fields
Essence: macOS text field that turns entries into draggable tokens (e.g. recipients).
Rules:
- Add a context menu per token for info/edit actions.
- Offer extra ways to create tokens besides comma (e.g. Return).
- Tune suggestion delay so suggestions do not distract while typing.
Avoid: Instant, intrusive suggestions.
Platform notes: macOS only.
Beyond Apple platforms: Chip inputs on web/Flutter.

# Presentation
## Action sheets
URL: https://developer.apple.com/design/human-interface-guidelines/action-sheets
Essence: Modal list of choices tied to an action the user just started.
Rules:
- Use an action sheet (not an alert) when offering extra choices (e.g. cancel mail draft: delete or save); on iOS use it rather than a menu since people expect it after an action.
- Use sparingly; one-line title; message only if needed.
- Provide Cancel at the bottom (upper-left on watchOS); destructive choices styled destructive and placed at the top.
- Avoid scrolling sheets; on watchOS at most four buttons including Cancel.
Avoid: Scrolling, long titles.
Platform notes: Not on visionOS; SwiftUI confirmationDialog.
Beyond Apple platforms: Bottom sheet / action menu for confirm-with-options.

## Alerts
URL: https://developer.apple.com/design/human-interface-guidelines/alerts
Essence: Interrupting modal for critical information needing a response.
Rules:
- Use sparingly; only actionable, essential content; informative-only messages belong inline.
- No alerts for common, undoable destructive actions (deleting a mail); do alert for rare, irreversible ones.
- Avoid alerts at app start; show cached data plus a quiet label instead.
- Up to three buttons; a title plus optional short message; optional text field only when input resolves the situation (secure for passwords).
- Title: say what happened, why, in context; avoid "Error"; at most two lines; complete sentence gets sentence case and punctuation, fragment gets title case without period.
- Neutral, direct tone; don't explain the buttons.
- Button titles: one or two verbs relating to the text ("Erase", "View All"); "OK" only for purely informational alerts; avoid Yes/No; always "Cancel" for cancelling; title case, no ending punctuation.
- Put the likeliest/default button trailing (or top when stacked); Cancel leading (or bottom); never make Cancel the default; Done if a single default button.
- Destructive style only when the destructive action wasn't deliberately chosen (Empty Trash confirm is not red).
- Allow Esc / Command-Period dismissal.
- iOS: choose action sheet for choices; avoid scrolling alerts. macOS: icon, suppression checkbox, Help button; caution symbol sparingly. visionOS: accessory max height 154 pt, 16 pt corners.
Avoid: Vague titles, multiple alerts at once, OK as default for confirmations.
Platform notes: as above.
Beyond Apple platforms: Confirm dialogs on web/Android should use verb-labeled buttons and reserve red for unintended destruction.

## Page controls
URL: https://developer.apple.com/design/human-interface-guidelines/page-controls
Essence: Dot indicators for a flat, ordered list of pages.
Rules:
- Only for sequential pages, not hierarchy; centered horizontally near the bottom.
- About 10 dots max; beyond that use a grid.
- Custom indicator images: simple, no inner detail or text; at most two kinds (e.g. a location glyph for the current-location page); don't color them.
- iOS: tap sides for next/previous or scrub; don't animate transitions during scrubbing; background style automatic (when not primary), prominent (primary nav), minimal (no scrubbing).
- Don't show a scroll indicator on the same axis as a page control.
- tvOS: full-screen peer pages only. watchOS: vertical pagination with Digital Crown, pages one screen tall.
Avoid: Many unique indicator images.
Platform notes: Not on macOS; visionOS non-interactive.
Beyond Apple platforms: Carousel dots follow the same cap and placement.

## Panels
URL: https://developer.apple.com/design/human-interface-guidelines/panels
Essence: macOS floating supplementary window (inspector, fonts, colors).
Rules:
- Use for quick controls tied to the active selection; inspectors update with selection, an Info window does not (use a window).
- Prefer simple controls (sliders, steppers) over typing.
- Short noun title; bring all panels forward when the app activates, hide when inactive; keep out of the Window menu list; usually no minimize button; menus say "Show Fonts" not "panel".
- HUD style only for media-heavy apps or when a standard panel would hide content; keep small, sparse color, keep one style across modes.
Avoid: HUDs without reason.
Platform notes: macOS only; elsewhere use a modal.
Beyond Apple platforms: Floating inspector pattern for desktop web.

## Popovers
URL: https://developer.apple.com/design/human-interface-guidelines/popovers
Essence: Transient, anchored view for a small amount of information or a few related actions.
Rules:
- Keep content small; arrow points to the trigger without covering it or essential content.
- Close button (Cancel/Done) only when it clarifies; otherwise dismiss on outside click or selection; stay open for multi-select.
- Save work on auto-close of nonmodal popovers; discard only on explicit Cancel.
- One popover at a time, never nested; nothing above it except an alert; allow switching in one click.
- Size to content; animate size changes.
- Not for warnings (use an alert). Don't say "popover" in help text.
- iOS/iPadOS: in compact width use a sheet instead. macOS: optionally detachable into a panel with minimal visual change.
Avoid: Popover chains.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: Web popovers/dropdowns: single, anchored, outside-click dismiss; bottom sheet on mobile.

## Scroll views
URL: https://developer.apple.com/design/human-interface-guidelines/scroll-views
Essence: Navigating content larger than its container.
Rules:
- Keep default gestures and keyboard shortcuts; custom scrolling still needs elastic behavior.
- Hint scrollability with partially visible edge content.
- Never nest same-orientation scroll views (different orientations are fine).
- Paging: define page size with a bit of overlap (a line of text) for context.
- Auto-scroll only as needed: to reveal selection or search hit, insertion point when typing, while drag-selecting past an edge.
- Zoom needs sensible min and max scale.
- Scroll edge effects: use only when content scrolls behind floating bars; prefer automatic style; one effect per view (keep pane effects consistent in height).
- iOS: with page-by-page mode show a page control and hide same-axis indicator. macOS: small/mini scrollbars in panels (same size for all controls). tvOS: auto-scroll to focus. visionOS: small fixed indicator, jog bar; Look to Scroll for reading/browsing (not dense controls), consistent across similar views, no parallax effects, full-width/height areas. watchOS: prefer vertical scrolling and Digital Crown, tab views for pages one screen tall.
Avoid: Nested same-direction scrolling.
Platform notes: as above.
Beyond Apple platforms: Same for web/Flutter; add scroll affordance via peeking next item.

## Sheets
URL: https://developer.apple.com/design/human-interface-guidelines/sheets
Essence: Scoped task presented over the parent view.
Rules:
- Use for short, focused tasks (attach a file, choose a location); use full-screen modal, a window, or immersive for long flows.
- One sheet at a time from the main interface; close the first before opening another.
- Use nonmodal (iOS/iPadOS), split view (visionOS) or panel (macOS) for supplementary tools.
- Buttons: Cancel/Close (dismiss without saving), Done (finish), Back (previous step). Pair Done with Cancel or Back; never show all three.
- iOS/iPadOS: Cancel leading, Done trailing in top toolbar; multi-step placement can vary by step.
- Detents: large (default) and medium (about half height); use medium for progressive disclosure (share sheet) but compose sheets stay full; include a grabber (also VoiceOver-accessible, tap cycles detents); swipe-down dismisses, with an action sheet confirmation for unsaved changes.
- iPadOS: prefer page or form sheet styles.
- macOS: cardlike, parent dimmed but other app windows still interactive; sensible default size; use a panel for repeated input (find/replace).
- visionOS: centered, not from the bottom; not covering most of the window.
- watchOS: full screen; use only when custom title or content needed; brief and occasional.
Avoid: Done-only sheets; stacked sheets.
Platform notes: as above.
Beyond Apple platforms: Bottom sheets with drag handle, Cancel/Save pairing, discard confirmation.

## Windows
URL: https://developer.apple.com/design/human-interface-guidelines/windows
Essence: Window management on iPadOS, macOS and visionOS.
Rules:
- Adapt fluidly to any size for multitasking.
- Open new windows deliberately (e.g. Compose); offer "open in new window" options instead of defaulting to it.
- Don't build custom window chrome; call them "windows" in UI text.
- Primary window carries navigation and content; auxiliary windows serve one task.
- iPadOS: keep leading toolbar items clear of window controls.
- macOS: states Main, Key, Inactive must show system appearances; avoid critical info in a bottom bar (use an inspector).
- visionOS: windows default to 1280x720 pt, keep the glass background, set min and max sizes, minimal depth; volumes for rich 3D, dynamic scaling, one extra ornament at most, baseplate glow.
Avoid: Custom window frames.
Platform notes: Not on iOS/tvOS/watchOS.
Beyond Apple platforms: Responsive window sizing and restraint with pop-out windows on desktop apps.

# Selection and input
## Color wells
URL: https://developer.apple.com/design/human-interface-guidelines/color-wells
Essence: A swatch that opens a color picker to change an element's color.
Rules:
- Prefer the system color picker (familiar, saved palettes shared across apps).
- macOS: well highlights while active and updates after selection; supports dragging colors between wells and from the picker.
Avoid: Custom pickers without need.
Platform notes: Not on tvOS/watchOS.
Beyond Apple platforms: Use the native/system picker (e.g. input type=color) where possible.

## Combo boxes
URL: https://developer.apple.com/design/human-interface-guidelines/combo-boxes
Essence: macOS text field plus pull-down list; custom values are allowed but not added to the list.
Rules:
- Default to a meaningful value from the list (need not be first).
- Introductory label in title case ending with a colon.
- Offer likely choices; keep items no wider than the field.
Avoid: Items that truncate.
Platform notes: macOS only.
Beyond Apple platforms: Editable dropdown / autocomplete input.

## Digit entry views
URL: https://developer.apple.com/design/human-interface-guidelines/digit-entry-views
Essence: tvOS full-screen PIN/digit input.
Rules:
- Use secure digit fields for sensitive data.
- State the purpose with a title and prompt.
Avoid: Showing sensitive digits.
Platform notes: tvOS only.
Beyond Apple platforms: Apple-only; OTP/PIN field conventions similar.

## Image wells
URL: https://developer.apple.com/design/human-interface-guidelines/image-wells
Essence: macOS editable image view (copy, paste, drag in, delete).
Rules:
- Revert to a default image when cleared if one is required.
- Provide standard Copy/Paste menu items and shortcuts.
Avoid: n/a.
Platform notes: macOS only.
Beyond Apple platforms: Avatar/image drop zones.

## Pickers
URL: https://developer.apple.com/design/human-interface-guidelines/pickers
Essence: Scrollable lists of distinct values; includes date pickers.
Rules:
- Use for medium-to-long lists; use a pull-down button for short lists and a list/table (with index) for very large sets.
- Make hidden values predictable (alphabetized countries, logical order).
- Show the picker in context near the field (bottom of window or popover) rather than switching views.
- Minute granularity: intervals must divide 60 (e.g. 15-minute steps).
- iOS date picker styles: compact (button in accent color, opens modal calendar/time editor; use when space is tight), inline, wheels, automatic; modes: date, time, date and time, countdown (max 23:59).
- macOS: textual style for tight space and precise entry; graphical for calendar browsing, ranges, clock face.
- watchOS: wheels with Digital Crown; long lists open via navigation link.
Avoid: Pickers for two or three options.
Platform notes: as above.
Beyond Apple platforms: Native date/time inputs; choose sensible minute step.

## Segmented controls
URL: https://developer.apple.com/design/human-interface-guidelines/segmented-controls
Essence: Linear group of 2+ equal segments acting as buttons: single/multi choice or momentary actions.
Rules:
- Use for closely related choices affecting an object, state or view; good when grouping and visible selection state matter.
- Keep one behavior per control (all selection or all actions).
- Limit segments: about 5-7 on wide layouts, about 5 on iPhone.
- Equal widths; text or images, not mixed; similar content size; nouns/noun phrases for labels, no introductory text needed when labeled.
- iOS: switch between closely related subviews (Event vs Reminder); use a tab bar for separate app sections.
- macOS: introductory text or per-segment labels/tooltips for icon controls; use a tab view for main-area view switching, segmented control in toolbar/inspector; spring loading.
- tvOS: prefer a split view for filtering; keep other focusable items away from segments.
- visionOS: icon segments show tooltip on gaze.
Avoid: Too many segments; mixing actions and selection.
Platform notes: Not on watchOS.
Beyond Apple platforms: Material segmented buttons / toggle groups follow the same rules.

## Sliders
URL: https://developer.apple.com/design/human-interface-guidelines/sliders
Essence: Adjust a value along a track between min and max.
Rules:
- Min on the leading side (horizontal) or bottom (vertical); max trailing or top.
- Customize track/thumb/icons only when it adds meaning (small/large image icons).
- For wide ranges add a text field and stepper to show/enter exact values.
- Do not use a slider for volume on iOS; use the system volume view.
- macOS: ticks (label min/max or periodic labels for nonlinear scales), live feedback, circular sliders for repeating values (rotation 0-360), tooltip value on hover, introductory label with colon.
- visionOS: prefer horizontal. watchOS: +/- buttons, custom glyphs allowed.
Avoid: Inconsistent min/max direction.
Platform notes: Not on tvOS.
Beyond Apple platforms: Pair range inputs with numeric fields; expose value via aria-valuenow.

## Steppers
URL: https://developer.apple.com/design/human-interface-guidelines/steppers
Essence: Two-segment +/- control for small incremental changes (shows no value itself).
Rules:
- Place next to the field showing the value; make obvious which value it changes.
- Pair with a text field when large or variable values are likely (copies to print).
- macOS: Shift-click for larger increments (e.g. 10x).
Avoid: Steppers alone for wide ranges.
Platform notes: Not on watchOS/tvOS.
Beyond Apple platforms: Quantity selectors in e-commerce follow the same pairing.

## Text fields
URL: https://developer.apple.com/design/human-interface-guidelines/text-fields
Essence: Small single-purpose text entry.
Rules:
- Use for names, emails; text view for longer text.
- Placeholder hints purpose but disappears, so also keep a separate label.
- Secure field for passwords/sensitive data.
- Size to the expected text; stack multiple fields vertically with consistent widths and clear label association; sensible tab order.
- Validate: email on blur; username/password before leaving the field; digits-only fields should reject others.
- Use a number formatter (decimals, percent, currency) but respect locale formatting.
- Choose clipping, wrapping or truncation (start/middle/end ellipsis); expansion tooltip on macOS.
- iOS/iPadOS/tvOS/visionOS: match the keyboard type to content; iOS Clear button on trailing end; leading icon for purpose, trailing for extra features (bookmarks).
- tvOS/watchOS: minimize text entry; prefer lists/buttons.
- macOS: combo box if choices are also useful.
Avoid: Placeholder as the only label; long forms on TV/watch.
Platform notes: as above.
Beyond Apple platforms: Direct form-field guidance: visible labels, input types, inline validation.

## Toggles
URL: https://developer.apple.com/design/human-interface-guidelines/toggles
Essence: Choose between two opposing states.
Rules:
- Use only for on/off state of content or setting; other actions need other components.
- Make the affected thing obvious from context or a label.
- State differences must be obvious without relying on color alone (fill, checkmark, dot).
- iOS/iPadOS: switch only inside a list row (no extra label); keep default green unless accent contrast is sufficient; outside lists use a toggle-style button with icon and background change, no explanatory label.
- macOS: switches, checkboxes, radio buttons belong in the window body, not toolbars/status bars. Switch for emphasized settings (mini switch in grouped form rows); do not swap existing checkboxes for switches.
- Checkbox: empty/check/dash (mixed); use for hierarchies of settings with indentation; mixed state for parent when children differ; label groups when unclear.
- Radio buttons: groups of 2-5 mutually exclusive options; avoid more than about 5 (use pop-up); consistent spacing; single on/off use a checkbox.
Avoid: Switches outside list rows on iOS; color-only state.
Platform notes: as above.
Beyond Apple platforms: Material switches/checkboxes follow the same usage (switch = immediate effect, checkbox = form selection).

## Virtual keyboards
URL: https://developer.apple.com/design/human-interface-guidelines/virtual-keyboards
Essence: On-screen text entry tuned to content type.
Rules:
- Set keyboard/content type to match input (email, number pad, decimal, phone, URL, web search, etc.) so the right keys and autocorrect appear.
- Customize the Return key label when it clarifies (Search).
- Custom input views: only when they clearly help; play the standard keyboard click sound.
- Custom keyboards (system-wide extensions): obvious switching (Globe), do not duplicate Emoji/Dictation keys, offer a tutorial in the app (not in the keyboard); not used in secure or phone fields.
- iOS/iPadOS: use the keyboard layout guide so important UI stays visible; accessory controls above the keyboard must be relevant and use Liquid Glass/standard toolbar.
- tvOS linear keyboard (grid for other devices); visionOS movable keyboard window; watchOS cannot change keyboard type, set content type.
Avoid: Wrong keyboard type for the field.
Platform notes: Not on macOS.
Beyond Apple platforms: Set inputmode/autocomplete attributes on web, keyboardType on Flutter/Android.

# Status
## Activity rings
URL: https://developer.apple.com/design/human-interface-guidelines/activity-rings
Essence: Apple's Move/Exercise/Stand rings, strictly for those metrics.
Rules:
- Show only when relevant to health/fitness; only for Move, Exercise, Stand; one person only, clearly labeled.
- Never recolor, filter or change opacity; always on black; enclose in a circle via corner radius; keep a black margin around the outer ring (min margin equals the gap between rings); scale appropriately.
- Use matching colors for associated labels; separate other ring-like graphics.
- Don't duplicate system Activity notifications; no decoration or branding use.
- iOS: three rings with Apple Watch, Move only otherwise.
Avoid: Using rings for other data or in app icons.
Platform notes: Not on macOS/tvOS/visionOS.
Beyond Apple platforms: Apple-only; but ring progress charts should not be mixed with other ring styles.

## Gauges
URL: https://developer.apple.com/design/human-interface-guidelines/gauges
Essence: Value within a range on a circular or linear path.
Rules:
- Standard gauge shows an indicator; capacity style shows a fill; accessory variant matches complications/Lock Screen widgets.
- Label current value and both endpoints concisely (VoiceOver reads visible labels).
- Gradient fills can convey meaning (hot-to-cold).
- macOS level indicators: capacity (continuous for large ranges, discrete segments filling fully), rating, relevance; change fill color at meaningful thresholds (default green).
Avoid: Many discrete segments for large ranges.
Platform notes: Not on tvOS.
Beyond Apple platforms: Meters and progress rings with labeled min/max.

## Progress indicators
URL: https://developer.apple.com/design/human-interface-guidelines/progress-indicators
Essence: Show that work is happening and, when possible, how long.
Rules:
- Determinate (bar or circular fill) when duration is known; indeterminate spinner otherwise.
- Prefer determinate; report advancement accurately and evenly (not 90% in 5 s then 5 min).
- Keep indicators animating; if stalled, explain the problem and what to do.
- Switch bar from indeterminate to determinate when possible; never change from spinner to bar.
- Add a short, specific description if useful (avoid "Loading" or "Authenticating").
- Put it in a consistent location.
- Offer Cancel when safe; add Pause if cancelling loses progress; confirm via alert when cancel has consequences.
- iOS refresh control: pull-to-refresh complemented by automatic updates; title only if valuable (last update time), never how-to text.
- macOS: spinner for background tasks or tight spaces, unlabeled; bar or spinner variants.
- watchOS: tint color configurable.
Avoid: Stationary indicators; vague labels.
Platform notes: as above.
Beyond Apple platforms: Linear/circular progress with determinate preference, cancel affordance and consistent placement.

## Rating indicators
URL: https://developer.apple.com/design/human-interface-guidelines/rating-indicators
Essence: macOS row of symbols (stars) showing rank.
Rules:
- Let people change ratings inline in lists.
- If you swap the star, ensure the symbol clearly reads as a rating scale.
- Shows whole symbols only with fixed spacing.
Avoid: Obscure rating symbols.
Platform notes: macOS only.
Beyond Apple platforms: Star ratings; use the star for recognition.
