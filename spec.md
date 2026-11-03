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
- Preserve the actual alignment of each screen. Do not introduce a globally centered max-width wrapper where the design uses an edge-aligned or full-bleed image.
- Avoid horizontal page scrolling, text overlap, distorted assets, and accidental clipping.
- Use 360px as the base reference, with responsive changes at 768, 992, 1280, 1440, and 1920px where the supplied frames require them. Convert breakpoint values consistently to Tailwind theme units.
- Validate intermediate widths and shorter viewport heights, not only the exact Figma frame sizes.

### Desktop: 992px and above

- Use a fluid 12-column grid, following each frame's grid settings and the user's explicit requirement.
- Place the text block on the left and the image on the right.
- Obtain actual spans from the Figma layout grids; do not infer them solely from rounded layer widths.
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
- Reproduce only its closed visual appearance. Opening a menu is outside scope. Do not expose an inert decorative element as a working accessible control or add keyboard focus to it.

## 8. Hero / About VERTI

- Header and hero together occupy at least the available browser viewport height.
- The hero's minimum height equals the viewport height minus the header's actual layout height. Use a layout that accounts for responsive header sizing rather than an unrelated fixed subtraction.
- Allow the hero to grow naturally when its content needs more space. Never clip content to fit a reference frame height.
- Account for mobile browser toolbar changes when determining available viewport height.
- Match each frame's Auto Layout alignment, content order, spacing, and image placement.
- Use the original living-wall photograph. Hero images must always use `object-fit: cover` (Tailwind `object-cover`) and fill their image container without distortion.
- Preserve the image container's aspect ratio exactly as shown in each corresponding Figma reference screen. Define responsive aspect ratios from those containers, not from the source image's intrinsic dimensions; do not apply one shared ratio to all screen variants.
- Between reference widths, retain the aspect ratio assigned to the active breakpoint and allow the container dimensions to scale proportionally. Change the ratio at the appropriate breakpoint when required by the next reference screen.
- Match the crop and focal point separately for each layout using the appropriate `object-position`. Cropping is expected with `cover`; stretching or changing the container ratio to display the entire source image is not allowed.
- Preserve the visible decorative corner marks where present. Do not carry them into screen variants where they are absent or outside the visible composition without checking the source.

## 9. Buttons, eyebrow, and assets

- Use the primary filled, no-icon button variant shown in the main screens, including its inset keyline and responsive size.
- Confirmed reference button sizes are 374 × 62px for Default and 320 × 52px for SM. Treat these as component references, not fixed grid column widths. Respect the actual instance's width mode and prevent overflow at narrower widths.
- Apply the corresponding design-system hover, active, and focus styles using CSS where applicable. Do not add a component showcase or unrelated states to the page.
- Do not invent a destination for “Discover Our Work”. If the design contains no destination, record that the deliverable is a visual prototype and leave navigation implementation outside scope.
- The eyebrow is uppercase with a 72 × 2px underline in the inspected instances. Use a 16px text-to-underline layout gap for the 1440px LG instance and a 4px gap for the 360px SM instance. Inspect the other frames independently rather than applying the contradictory prose descriptions.
- Use original Figma assets and supplied fonts. Download implementation assets locally; temporary Figma connector URLs must not be used as permanent website dependencies.
- Provide meaningful alternative text for informative images, mark decoration appropriately, use a logical heading hierarchy, and retain visible focus for real links or controls.

## 10. Resolved source discrepancies and remaining inspection

- Eyebrow descriptions mention 24px (LG) and 12px (SM) text-to-underline gaps, while inspected screen instances resolve to 16px (LG) and 4px (SM). Follow the actual screen instance for this implementation; document any later correction rather than silently mixing the two sources.
- The header component description mentions a nominal 98px height, while the main screens use smaller responsive instances. Main-screen instances take precedence.
- Measured main-screen header heights are approximately 50px at 360px, 64.5px at 768/992/1280px, and 68.5px at 1440/1920px. These are visual comparison measurements, not instructions to hardcode page geometry; derive header height from the actual logo, padding, and border.
- Some desktop layers extend to or beyond frame edges. Inspect layout grids and clipping deliberately; do not recreate accidental browser overflow or silently impose symmetric margins.
- Metadata confirms all six frame dimensions. Detailed design context and rendered previews were inspected for the 360px and 1440px frames. Exact token values, grid settings, and image crops for the other four frames still require implementation-time inspection.
- These resolutions apply to the implementation specification. The source Figma file has not been modified.

## 11. Browser support and verification

Support current stable Chrome, Firefox, Edge, and Safari at delivery time, including Safari on iOS and Chrome on Android for mobile layouts.

- Compare the rendered page with all six reference frames at their listed viewport dimensions.
- Check intermediate widths, breakpoint boundaries, short viewports, natural scrolling, and zoomed text.
- Verify the sticky header, minimum-height behavior, content order, font loading, image crops, SVG logo, CSS hamburger, and button states.
- Record the browser versions and environments actually tested. Do not claim cross-browser verification that was not performed.

## 12. Acceptance criteria

- Only the supplied main-screen content is implemented.
- The page uses semantic HTML and Tailwind CSS 4 with no application JavaScript.
- Project colors and typography are mapped to named Tailwind theme tokens.
- Reusable CSS favors `@apply` where practical.
- Desktop layout uses a proportional 12-column grid; tablet and mobile use stacked full-width blocks.
- Typography remains constant within each breakpoint range.
- Header remains sticky; header and hero fill at least the viewport without preventing content growth.
- Original imagery, decorative assets, and SVG logo match their design slots and proportions.
- Every hero image uses `object-cover`; its container aspect ratio matches the corresponding Figma reference and remains proportional within the active breakpoint range.
- Hamburger is drawn in HTML/CSS and does not claim unsupported functionality.
- Button styling and applicable CSS states match the design system.
- No unintended horizontal scrolling, overlapping content, distorted images, or clipped text occurs.
- README documents the build/view workflow and any remaining prototype limitations or unverified checks.
