# VERTI — Static Website Specification

## 1. Objective and scope

Build a responsive static website that faithfully reproduces the main VERTI screens supplied in Figma. This is an independent test project; the earlier SOLLUX brief and PDF do not apply.

Implement only the content, sections, assets, and visual states used by the main screens. The current screen set contains a header and an About VERTI hero section. Do not add pages, menus, forms, sliders, animations, or other product functionality that is outside this scope.

## 2. Verified Figma references

All five supplied references were successfully accessed through the Figma connector on November 3, 2026.

| Reference | Node | Link |
| --- | --- | --- |
| Logo and hamburger | `398:245` | [Component overview](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=398-245) |
| Header | `398:262` | [Header section](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=398-262) |
| Buttons | `375:32` | [Button variants and states](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=375-32) |
| Eyebrow | `422:27` | [Eyebrow variants](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=422-27) |
| Main screens | `743:488` | [AI tasks screen set](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-488) |

### Main reference frames

| Frame | Reference viewport | Node | Link |
| --- | --- | --- | --- |
| AI -360px | 360 × 667 | `743:685` | [Mobile](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-685) |
| AI -768px | 768 × 900 | `743:631` | [Tablet](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-631) |
| AI -992px | 992 × 700 | `743:585` | [Small desktop](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-585) |
| AI -1280px | 1280 × 720 | `743:739` | [Desktop](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-739) |
| AI -1440px | 1440 × 900 | `743:539` | [Large desktop](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-539) |
| AI -1920px | 1920 × 950 | `743:538` | [Wide desktop](https://www.figma.com/design/1RtecFkM23fveA7pMJdht8/Verti?node-id=743-538) |

These dimensions are comparison viewports, not fixed page dimensions. In particular, the mobile content extends beyond its 667px reference viewport and must remain accessible through natural scrolling. The mobile reference width is 360px, not 375px.

### Source precedence

1. Explicit user requirements recorded in this specification.
2. Actual instance properties, visual appearance, Auto Layout, and layout grids in the main reference frames.
3. Shared component variants, styles, and variables referenced by those instances.
4. Component descriptions and documentation notes.

Do not implement documentation boards as website sections. Reinspect the relevant nodes before implementation. Generated reference code is an inspection aid, not the required architecture or layout implementation.

## 3. Technology and delivery

### Required pre-implementation inspection

Before writing implementation code, inspect all six main reference frames (360, 768, 992, 1280, 1440, and 1920px) through Figma. Record a six-frame measurement matrix in `docs/design-measurements.md` covering container padding and limits, grid columns and gutters, element spans and offsets, section spacing and alignment, typography, image container dimensions and aspect ratios, crop/focal position, and component variants and states used by the screens.

Distinguish directly observed values from derived ratios and implementation interpretations. Do not invent missing measurements. Resolve material ambiguities before coding the affected layout. This inspection and its recorded matrix are mandatory, not an optional implementation-time follow-up.

The implementer independently retrieves measurements, variables, styles, and layout properties from Figma and documents any necessary calculations. The user is not required to provide measurement tables or calculations. Questions to the user should concern only material ambiguities that cannot be resolved from the available design and this specification.

- Semantic HTML and CSS, with Tailwind CSS 4.
- No application JavaScript, React, other UI frameworks, backend, database, or runtime component libraries.
- Use the simplest practical Tailwind compilation workflow. Build-time tools are allowed and must not introduce browser-side JavaScript.
- Deliver HTML, compiled CSS, source CSS, local assets, and a README explaining installation, CSS compilation, and how to view the page.
- Preserve the English copy shown in Figma, including the heading “The story behind Verti”, the eyebrow “01 / About VERTI”, the descriptive paragraph, and “Discover Our Work”.

## 4. Tailwind and design system

- Configure Tailwind 4 through its CSS-first theme configuration, using the Figma design system as the source of tokens.
- Override the relevant default color and typography namespaces with project tokens. Do not rely on unrelated default colors or font scales.
- Define named tokens for font families, sizes, weights, line heights, letter spacing, colors, and reusable spacing or visual values needed by the supplied screens.
- Prefer Tailwind utility classes in HTML.
- When authoring reusable CSS classes, prefer `@apply` with token-backed utilities. For example, prefer `@apply bg-primary` over a handwritten `background: var(--color-primary)` declaration when both express the requirement correctly.
- Direct CSS remains allowed for theme declarations, selectors, pseudo-elements, or behavior that utilities cannot express clearly. Do not force `@apply` where it is invalid or less maintainable.
- Avoid repeating arbitrary values when a reusable design token is appropriate.
- Implement only the component variants used by the main screens and their applicable CSS states; do not reproduce the entire component library.

### Confirmed values from inspected desktop and mobile screens

| Role | Value |
| --- | --- |
| Heading font | Playfair Display, SemiBold, weight 600 |
| Body and UI font | Lato, Regular, weight 400 |
| Main text | `#111111` |
| Secondary text / default eyebrow | `#565F52` |
| Primary brand | `#022803` |
| Header background / inverse text | `#FEFDFD` |
| Hero background | `#F1F5EF` |
| Header bottom border | `#9DB993` |

These are confirmed values used by inspected instances, not a complete export of the entire design system. Inspect the remaining frames and required hover variants before completing the token mapping.

### Variable access and token mapping

Figma variable definitions were successfully retrieved for the 360px and 1440px frames. No separate token export or API credential is required for the currently accessible, node-bound values.

- Preserve a documented mapping from Figma names to Tailwind theme tokens and utilities, for example `color/brand/primary` → `--color-primary` → `bg-primary`.
- Confirmed spacing bindings include `space/4` = 4px, `space/16` = 16px, and `space/32` = 32px. Preserve their visual size when converting to rem units.
- Retrieve the values used by every target frame and required button state. A successful node-level lookup is not proof that every collection, mode, alias, or unused library token has been exported.
- When a required value comes from an inaccessible external library or an unavailable mode, request access to that source or a targeted token export. Never request API secrets in the specification.
- Preserve meaningful semantic token names even when two tokens currently resolve to the same value.

## 5. Responsive layout

### General rules

- Build fluid layouts using available space and proportional tracks rather than fixed pixel widths for major columns.
- Derive gutters, padding, alignment, spans, and container constraints from Figma.
- Fixed spacing, icon dimensions, and documented component sizes are allowed; the restriction concerns rigid page layout, not all pixel values.
- Use a centered main page container with a maximum outer width of 1920px, including its horizontal padding (`border-box`). Available content width is 1920px minus the applicable left and right padding at the maximum size. Below that limit, the container follows the available viewport width.
- Apply the same centered 1920px outer-width limit and responsive padding convention to the header. Above 1920px, neither the header content nor the main content keeps expanding; preserve the 1920px layout and its padding. Images may break out across internal padding as specified in Section 8, but not beyond the outer 1920px container.
- Avoid horizontal page scrolling, text overlap, distorted assets, and accidental clipping.
- Use 360px as the base reference, with responsive changes at 768, 992, 1280, 1440, and 1920px where the supplied frames require them. Convert breakpoint values consistently to Tailwind theme units.
- The minimum supported viewport width is 360px. A separate 320px layout or acceptance check is not required. Validate intermediate widths, shorter viewport heights, and viewports wider than 1920px to confirm centered container behavior.

### Desktop: 992px and above

- Use a fluid 12-column grid, following each frame's grid settings and the user's explicit requirement.
- Place the text block on the left and the image on the right.
- Determine spans from the Figma grid and round ambiguous element boundaries to the nearest intended whole-column span. Align major layout blocks to grid lines; do not reproduce incidental few-pixel offsets or add pixel nudges to compensate for them.
- The sole deliberate grid-alignment exception is the responsive image breakout described below. Internal component padding and decorative artwork are not major grid blocks.
- Do not copy fixed column widths or absolute positioning from generated reference code.

### Tablet and mobile: below 992px

- Use a single-column layout rather than the desktop 12-column grid.
- Place the image first and the text block below it, as shown in the 768px and 360px frames.
- Main blocks use the available container width. Preserve their distinct inner padding and image treatment.
- Do not equate full-width layout blocks with forcing every child, such as a button, to full width. Match the corresponding instance's sizing mode.

## 6. Typography

- Use a base conversion of **16px = 1rem** at the browser's default font-size setting. Set the root font size to `100%`; do not use a 62.5% reset or force a fixed 16px root that overrides the user's browser preference.
- Convert Figma pixel values to rem by dividing by 16: 16px = 1rem, 20px = 1.25rem, 24px = 1.5rem, and 64px = 4rem. Apply this convention to typography and rem-based spacing tokens; retain unitless values or pixel units where appropriate, such as proportional layout tracks or fine borders.
- Pixel values in the reference tables describe Figma measurements at the default root size, not a requirement to express all CSS values in pixels. Responsive breakpoint changes remain discrete; rem units must still respect user font-size preferences.
- Match the font size, weight, line height, and letter spacing of each reference frame.
- Typography changes discretely at breakpoints. Do not use `clamp()`, viewport-based font sizes, or fluid interpolation.
- Preserve intentional editorial line breaks where explicitly authored in the design. Otherwise let text wrap according to the correct container width.

### Verified typography samples

| Role | 360px frame | 1440px frame |
| --- | --- | --- |
| Main heading | 28px / 36.4px, weight 600, tracking 1px | 64px / 70.4px, weight 600, tracking 1.5px |
| Body | 16px / 24px, weight 400 | 20px / 28px, weight 400 |
| Eyebrow | 14px / 20px, tracking 1.68px | 20px / 28px, tracking 2.4px |
| Button label | 20px / 28px | 24px / 32px |

Inspect the other four frames for their exact values; do not assume they inherit one of these samples.

## 7. Header, logo, and hamburger

- The header is sticky at the top of the viewport and retains its place in normal document flow.
- Match the actual main-screen instance's padding, background, border, shadow, and dimensions. Do not apply the documentation preview's nominal height to all screens.
- Use the original logo artwork as SVG, preserving proportions and the appropriate theme and size variant. Export the complete logo asset rather than recreating its lettering.
- Confirmed logo variants: Default 146 × 58px, MD 109.5 × 43.5px, SM 73 × 29px. The inspected 1440px screen uses MD; the 360px screen uses SM.
- Create the hamburger artwork with HTML/CSS, without raster images, SVG artwork, or an icon library, as explicitly requested by the user.
- Match its square outline, line geometry, color, and responsive size. Documented artwork sizes are Default 50px, MD 37.5px, and SM 25px; account separately for the instance's border box.
- Reproduce only the hamburger’s closed visual appearance using HTML/CSS. It is decorative: do not implement menu opening, button semantics, keyboard focus, or expanded-state attributes for it.

## 8. Hero / About VERTI

- Header and hero together occupy at least the small viewport height (`100svh`). Collapsing the mobile browser address bar does not increase the section height. Content may naturally increase the page height.
- The hero's minimum height equals the small viewport height (`100svh`) minus the header's actual layout height. Use a layout that accounts for responsive header sizing rather than an unrelated fixed subtraction.
- Allow the hero to grow naturally when its content needs more space. Never clip content to fit a reference frame height.
- Use the small viewport height (`100svh`) for the page minimum height so mobile browser toolbar expansion and collapse do not resize the hero. Retain natural content growth and provide a `100vh` fallback where needed.
- Match each frame's Auto Layout alignment, content order, spacing, and image placement.
- Use the original living-wall photograph. Hero images must always use `object-fit: cover` (Tailwind `object-cover`) and fill their image container without distortion.
- Preserve the image container's aspect ratio exactly as shown in each corresponding Figma reference screen. Define responsive aspect ratios from those containers, not from the source image's intrinsic dimensions; do not apply one shared ratio to all screen variants.
- Between reference widths, retain the aspect ratio assigned to the active breakpoint and allow the container dimensions to scale proportionally. Change the ratio at the appropriate breakpoint when required by the next reference screen.
- Match the crop and focal point separately for each layout using the appropriate `object-position`. Cropping is expected with `cover`; stretching or changing the container ratio to display the entire source image is not allowed.
- Where the reference image intentionally breaks out to the right, apply a negative right margin to its wrapper equal in magnitude to the right padding of the enclosing padded layout container. Reuse the same responsive spacing token for both values so the image reaches the container’s outer right edge. Do not use an arbitrary pixel offset, transform, or viewport-width workaround.
- On mobile and tablet, the image must also break out of the padded container: apply negative left and right margins equal in magnitude to the respective left and right padding. Expand its wrapper width to include both released padding areas so the image fills the full outer container width.
- Account for each breakout in the wrapper’s width so the image actually fills the released padding area. Preserve the required aspect ratio based on this final rendered width. Use shared responsive padding tokens for the matching negative margins. These deliberate image breakouts apply on desktop, tablet, and mobile; they must not cause horizontal page scrolling.
- Preserve the visible decorative corner marks where present. Do not carry them into screen variants where they are absent or outside the visible composition without checking the source.

## 9. Buttons, eyebrow, and assets

- Use the primary filled, no-icon button variant shown in the main screens, including its inset keyline and responsive size.
- Confirmed reference button sizes are 374 × 62px for Default and 320 × 52px for SM. Treat these as component references, not fixed grid column widths. Respect the actual instance's width mode and prevent overflow at narrower widths.
- Apply the corresponding design-system hover, active, and focus styles using CSS where applicable. If a required state is absent from Figma, the implementer may define it using project colors and an accessible, clearly visible keyboard focus treatment without additional approval. Document these fallback states in `docs/design-measurements.md`. Do not add a component showcase or unrelated states to the page.
- This is a visual prototype. All displayed CTAs and navigation links, including the logo link, use `<a href="#">` and have no real destination or application action. Do not use semantic `<button>` elements for these placeholder links. The hamburger remains non-interactive decoration.
- Preserve native anchor semantics and keyboard focus for `href="#"` elements; implement their applicable hover, active, and focus styles. Do not mislabel them as disabled or hide focusable links from assistive technology. The links are decorative in product intent but remain native links technically.
- Native `href="#"` navigation may move the page to the top and update the URL fragment. Accept this browser behavior; do not add JavaScript to suppress it. Document this prototype limitation in the README.
- The eyebrow is uppercase with a 72 × 2px underline in the inspected instances. Use a 16px text-to-underline layout gap for the 1440px LG instance and a 4px gap for the 360px SM instance. Inspect the other frames independently rather than applying the contradictory prose descriptions.
- Use original Figma assets and supplied fonts. If the required Playfair Display SemiBold (600) or Lato Regular (400) font files are missing, the implementer may download them from an official font source and store them locally with their licenses. Record the source, font files, weights, and local asset paths in `docs/design-measurements.md`. Download implementation assets locally; temporary Figma connector URLs must not be used as permanent website dependencies.
- Provide meaningful alternative text for informative images, mark decoration appropriately, use a logical heading hierarchy, and retain visible focus for real links or controls.

## 10. Resolved source discrepancies and remaining inspection

- Eyebrow descriptions mention 24px (LG) and 12px (SM) text-to-underline gaps, while inspected screen instances resolve to 16px (LG) and 4px (SM). Follow the actual screen instance for this implementation; document any later correction rather than silently mixing the two sources.
- The header component description mentions a nominal 98px height, while the main screens use smaller responsive instances. Main-screen instances take precedence.
- Measured main-screen header heights are approximately 50px at 360px, 64.5px at 768/992/1280px, and 68.5px at 1440/1920px. These are visual comparison measurements, not instructions to hardcode page geometry; derive header height from the actual logo, padding, and border.
- Normalize incidental few-pixel deviations to the intended grid alignment. The image breakout is the explicit exception: use a matching negative right margin on desktop and matching negative left and right margins on mobile/tablet, as specified in Section 8. Do not introduce horizontal page scrolling.
- Metadata confirms all six frame dimensions. Detailed design context and rendered previews were inspected for the 360px and 1440px frames. Exact token values, grid settings, and image crops for the other four frames still require implementation-time inspection.
- These resolutions apply to the implementation specification. The source Figma file has not been modified.

## 11. Browser support and verification

Support current stable Chrome, Firefox, Edge, and Safari at delivery time, including Safari on iOS and Chrome on Android for mobile layouts.

- Compare the rendered page with all six reference frames at their listed viewport dimensions.
- For each of the six viewports, capture the page after fonts and images have loaded and overlay the screenshot on the corresponding Figma render at the same scale. The overlay covers only the area available in the Figma reference. Also capture and visually inspect all below-the-fold mobile content for layout, spacing, overlap, and clipping; a matching Figma overlay is not required for content outside the available reference. Save comparison images and record review coverage, discrepancies, and their resolution in `docs/visual-review.md`.
- Correct differences in geometry, spacing, typography metrics, colors, asset selection, aspect ratios, and crop/focal position. Minor browser-specific font antialiasing differences are acceptable; incorrect fonts, font sizes, line heights, or resulting layout differences are not excused as antialiasing.
- Evaluate overlays against the explicitly approved grid rounding, image breakouts, and natural content growth in this specification. Document these intentional differences from raw frame geometry rather than treating them as defects or silently changing the requirements. Any additional deviation from Figma requires explicit user approval before it can be accepted; describe the proposed difference and record the approval in `docs/visual-review.md`. This does not require approval for fallback interaction states explicitly authorized in Section 9.
- Check intermediate widths, breakpoint boundaries, short viewports, natural scrolling, and zoomed text.
- Verify the sticky header, minimum-height behavior, content order, font loading, image crops, SVG logo, CSS hamburger, and button states.
- The user will perform manual cross-browser acceptance testing. The implementing AI must not run an automated test suite or a cross-browser test campaign, and must not make completion conditional on performing those user-owned checks.
- The previously agreed screenshot-overlay review remains part of visual implementation verification; it is not a requirement to run functional or cross-browser test suites. Use the available rendering environment for that visual review and state its coverage accurately.
- Provide a short manual checklist in the README for the user to check Chrome, Firefox, Edge, Safari, and mobile browser behavior. Record any AI-observed issues, but do not claim that user-owned manual tests have been completed.

## 12. Acceptance criteria

- Only the supplied main-screen content is implemented.
- The page uses semantic HTML and Tailwind CSS 4 with no application JavaScript.
- Project colors and typography are mapped to named Tailwind theme tokens.
- Reusable CSS favors `@apply` where practical.
- Desktop layout uses a proportional 12-column grid; tablet and mobile use stacked full-width blocks. Image breakouts use matching negative padding margins: right on desktop, left and right on mobile/tablet.
- The minimum supported viewport is 360px. Above 1920px, main and header containers remain centered with a maximum outer width of 1920px including their padding.
- Typography remains constant within each breakpoint range.
- Header remains sticky; header and hero together fill at least the small viewport height (`100svh`). Collapsing the mobile browser address bar does not increase the section height, and content can grow naturally.
- Original imagery, decorative assets, and SVG logo match their design slots and proportions.
- Every hero image uses `object-cover`; its container aspect ratio matches the corresponding Figma reference and remains proportional within the active breakpoint range.
- Hamburger is decorative HTML/CSS artwork with no menu behavior. CTAs, navigation links, and the logo link use `href="#"` without real destinations or application actions; native anchor behavior and keyboard focus are preserved.
- Default link and CTA appearance and interaction states match Figma wherever defined. For missing states, the implementer uses project colors, provides clearly visible keyboard focus, and documents the fallback styles in accordance with Section 9.
- No unintended horizontal scrolling, overlapping content, distorted images, or clipped text occurs.
- Screenshot overlays have been reviewed for the available reference area at all six viewports, and all below-the-fold mobile content has been visually inspected. Discrepancies are fixed, covered by an interpretation already authorized in this specification, or explicitly approved by the user and recorded. Only minor font-antialiasing differences are accepted without correction or approval.
- README documents the build/view workflow, prototype limitations, and a manual browser acceptance checklist for the user. Automated tests and an AI-run cross-browser campaign are not required deliverables; final manual browser testing belongs to the user.
