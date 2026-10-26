# Small Hours — design specification

Status: executable fictional demonstration, version 2.2. Read this file without requiring any conversation history. All copy below is proposed concept copy, not factual information about an operating venue.

## 1. Purpose, audience, scope, and authority

Create an English, single-page website explaining a fictional shared reading space to adults who enjoy quiet reading. Deliver static semantic HTML, CSS, a local licensed photograph, and minimal JavaScript only for image failure handling. No framework, backend, accounts, forms, analytics, paid services, external font requests, or generated images. Use `site/index.html`, `site/styles.css`, and `site/assets/library.jpg`, relative to this specification. Public example source is authorized by the repository-improvement task; no live venue or hosted service is being launched.

The workflow first delivered this Markdown specification. Continuing to the local website is separately authorized in this repository task. For a user who requests Markdown only, stop after saving the specification.

## 2. Evidence, choices, and exclusions

**Human-confirmed direction:** large photography with centered copy, chosen from reference F, [Aesop](https://www.aesop.com/), after two rounds of real reference viewing. The observed frame had broad photographic coverage with pale centered text. Only those two compositional attributes are confirmed. The public [reference record](references.md) identifies all nine source sites and the comparison rationale.

**Design suggestions:** Small Hours name, fictional audience/content, warm neutral base, serif headings, exact type sizes, section structure, photograph selection, spacing, breakpoints, and every numeric parameter below. Numbers are not measurements copied from F and are not user-confirmed. No business facts have been supplied.

**Exclude:** Aesop's branding, logos, product assets, marketing text, exact styling; signup or booking claims; real address, prices, schedule, contact details, testimonials, and statistics. Avoid decorative card grids for the main narrative. Use a broad photographic hero, a typographic introduction, a simple numbered list, and native disclosure questions.

## 3. Visual effect and design parameters

The page should feel quiet through generous space, restrained contrast, readable serif headlines, and a single interior photograph. Concrete rules below define that effect; descriptive words alone do not override them.

All values in the following tables are **design suggestions** unless labeled otherwise.

| Token | Value | Application | Status |
| --- | --- | --- | --- |
| `--paper` | `#F5F0E7` | Page background and header | Design suggestion |
| `--surface` | `#FFFCF6` | Light content surfaces | Design suggestion |
| `--ink` | `#242C29` | Primary text | Design suggestion |
| `--muted` | `#58635C` | Supporting text | Design suggestion |
| `--line` | `#D5D9CE` | Dividers, not a sole indicator of a control | Design suggestion |
| `--accent` | `#235343` | Solid button background, text links, focus outline | Design suggestion |
| `--accent-hover` | `#173F32` | Hover/active button background and link hover | Design suggestion |
| `--accent-tint` | `#E3ECE4` | Bring section background | Design suggestion |
| Hero text | `#FFFCF6` | All over-image text | Design suggestion |
| Hero scrim | `rgba(0,0,0,0.64)` | Uniform overlay above image, below text | Design suggestion |

**Design suggestions:** Use Georgia, 'Times New Roman', serif for display headings and wordmark; Arial, Helvetica, sans-serif for body, buttons, and navigation. No downloaded fonts. Desktop hero title 64px/1.05, section title 40px/1.15, body 18px/1.6, nav/buttons 15px/1.4, eyebrow 12px/1.4 with 0.16em letter spacing. Headings use normal font weight; controls use bold. Body copy measure at most 64 characters; hero title max-width 820px, subtitle max-width 580px. Avoid all-caps paragraphs.

**Design suggestions:** Content max-width 1120px. Horizontal page gutter 40px above 1000px, 24px from 701–1000px, 20px at 700px and below. Section vertical padding 88px desktop, 64px tablet, 48px mobile. Grid gap 48px desktop, 32px tablet, 24px mobile. No content below 320px viewport width is promised, but there must be no horizontal overflow at 400px or 1280px.

**Design suggestions:** Primary button: background accent, surface text, minimum height 48px, padding 14px 24px, 4px radius, hover accent-hover. Secondary hero link: surface text, visible underline, minimum 44px hit area. Keyboard focus: 3px accent outline with 4px offset on light surfaces; hero controls use a surface-colored outline. Do not rely solely on color to indicate links. Standard text contrast must meet WCAG AA 4.5:1; large text 3:1. Light dividers are decorative.

## 4. Page structure and complete copy

There is one route, `index.html`; navigation uses same-page anchors. Document title: **Small Hours — A reading-space concept**. Meta description: **A fictional reading-space concept for quiet pages and shared attention.** Language: `en`.

The exact visible text is specified below. Do not generate additional claims or placeholder paragraphs.

### Header

**Design suggestions:** Cream background, no sticky positioning. Maximum-width horizontal row, min-height 88px, wordmark at left and navigation at right. Wordmark text **Small Hours**, link `#top`, accessible name **Small Hours, back to top**. Navigation labels and targets: **The idea** → `#about`; **What to bring** → `#bring`; **Questions** → `#questions`. A skip link first in DOM says **Skip to content**, targets `#main`, visually hidden until keyboard focus.

### Hero — top of main

**Design suggestions:** Full available width below header; minimum height 600px desktop and 520px mobile; centered content; vertical padding 88px desktop/64px mobile. The photograph fills the area with object-fit cover, object-position 50% 45%. Overlay is 0.64 black. The photograph is decorative relative to the textual purpose; use `alt=""` and show a visible credit later. It is illustrative, not a photo of a real Small Hours venue.

Eyebrow: **A READING-SPACE CONCEPT**

Heading h1: **A little room for big ideas.**

Paragraph: **Bring a book. Find a comfortable corner. Make a little space for reading, together.**

Primary anchor: **Explore the idea** → `#about`.

Secondary anchor: **What should I bring?** → `#bring`.

### About — `#about`

**Design suggestions:** Two columns at widths above 700px: short heading column 0.85fr and prose 1.15fr. At mobile stack heading before prose.

Eyebrow: **THE IDEA**

Heading h2: **A pause, shared.**

Paragraph 1: **Small Hours imagines a place where reading is enough. No assigned chapters, no required introductions — just a book you want to spend time with.**

Paragraph 2: **Come for a few quiet pages. Stay curious about what everyone else is reading. Conversation is welcome; silence is welcome too.**

### Bring — `#bring`

**Design suggestions:** Full-width tinted section. Heading above a semantic ordered list; each item is a separate horizontal row with a two-digit number, short title, and description. Thin dividers between rows. On desktop use columns 56px / 0.7fr / 1.3fr; on mobile use 36px / 1fr with the description below the title in column 2.

Eyebrow: **KEEP IT SIMPLE**

Heading h2: **Three things to bring.**

01 / h3 **A book of your choice** / **Something new, a familiar favorite, or the one you keep meaning to finish.**

02 / h3 **A little time** / **Leave a small opening in your day for a chapter, a page, or a sentence.**

03 / h3 **Your own pace** / **Read slowly, take a note, or simply sit with an idea. There is no reading target.**

### Questions — `#questions`

**Design suggestions:** Maximum-width two-column layout above 700px, heading left and two native `details` elements right. Both start closed. `summary` is the keyboard-operable control with a visible plus indicator that becomes a minus when open. Answers expand in document flow, with no animation or modal.

Eyebrow: **A FEW DETAILS**

Heading h2: **Before you turn the page.**

Question 1: **Is this a real venue I can book?**

Answer 1: **Not yet. Small Hours is a fictional website example. It does not offer bookings, memberships, or a physical address.**

Question 2: **Do I need to read the same book as everyone else?**

Answer 2: **In this concept, everyone brings their own book. There is no shared reading list or preparation.**

### Footer

Thin top border, stacked or wrapping rows. Text: **Small Hours — a fictional reading-space concept.**

Credit line: **Illustrative photograph: Carnegie Free Library, by Cbaile19 / Father Pitt. CC0.** Link the work name to the source page from section 7 and **CC0** to its license. Do not imply the photographed library sponsors this project. Final note: **No bookings, accounts, or personal data collection.**

## 5. Responsive behavior

**Design suggestions:** Above 1000px use desktop values. At 701–1000px: hero h1 48px, section h2 36px, gutters 24px, section padding 64px. At 700px and below: h1 40px, h2 32px, body 17px; header stacks wordmark above a wrapping navigation row with 16px gap and 20px vertical padding. Hero actions stack and center, each at least 44px tall. About and Questions collapse to one column. Bring rows follow section 4's mobile grid. Footer wraps. Keep the photograph cropped rather than squeezed; preserve centered copy. Do not hide important text on mobile. No hamburger menu is necessary for three short anchors.

## 6. Interactions, accessibility, and states

- Anchor activation changes the URL fragment and moves to the matching section. Keep native browser behavior, no scroll-jacking or forced smooth scrolling.
- Buttons are links because they navigate. There are no fake submit, booking, or login controls.
- FAQ disclosures support click, Enter, and Space through native `details`/`summary`; opening one does not close the other.
- Hover, active, and focus styles use the shared palette tokens. Focus remains visible; skip-link appears on focus. No motion is required; respect reduced-motion automatically by not animating.
- Photo loads from a relative local path. Its absence must leave a solid ink background under the scrim and all hero text readable. On an image error, show **Illustrative photograph unavailable.** as a small visible hero note. Hide that note during normal successful loading. No generated-image fallback.
- Semantic header/nav/main/section/footer, one h1, sequential h2/h3, `lang=en`, meaningful link names. No essential information conveyed only by the decorative photo.
- Loading/data/empty/authentication states: not applicable to this static concept. Do not invent remote data or add services to demonstrate them.

## 7. Assets, source, and conditions

Use `site/assets/library.jpg`, a real interior photograph of Carnegie Free Library, Carnegie, Pennsylvania, by Cbaile19 (Father Pitt). It is not an image of Small Hours. Source: [Wikimedia Commons file page](https://commons.wikimedia.org/wiki/File:Interior,_Carnegie_Free_Library,_Carnegie,_2025-05-14.jpg). License: [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/), verified 2026-10-26. Full provenance and stable inspected revision are in [asset notes](site/assets/README.md). Keep the original file; CSS crop and overlay do not modify the source bitmap. Credit voluntarily as above.

This interior is warmly lit with wood surfaces and a fireplace; use the existing photographed light. Do not fabricate sunlight, replace people, recolor the image, or generate variants. The portrait-oriented source is deliberately cropped for the broad hero. If an approved asset is missing, use the specified solid-color failure state and report the missing file. Do not substitute an unlicensed reference screenshot. Logo assets, illustrations, social icons, and external fonts are not required.

## 8. Unresolved questions and assumptions

This concept is fully implementable as a labeled demonstration. A real launch would require owner-approved name/copy, actual operating details, business/legal requirements, and permission for any new assets. Those facts are absent, so the corresponding features are out of scope. No invented data fills the gap. The chosen photo, accent and neutral palette, typeface, and pixel values remain design suggestions until a real project owner approves them. No user research or conversion result is claimed.

## 9. Execution instructions for another AI

1. Read this file, the reference decisions, and asset notes. Use the current body as the source of truth; superseded values in the change log are historical only.
2. Implement `site/index.html` and `site/styles.css` using the exact copy and tokens above. Keep dependencies at zero. Use the existing local CC0 JPEG and original HTML/CSS, not reference-site code or branding.
3. If the request is Markdown only, do not execute step 2: return this saved specification. Otherwise confirm that creation authorization exists in the current request, then build one page. Never infer hosting or publication authorization from a request to build.
4. Preview locally. Inspect actual desktop and mobile widths, image load, overflow, navigation, keyboard focus, FAQ state, and missing-image state. Save screenshots only of your own output, with the asset license attached.
5. Correct defects, keep this specification synchronized, and report actual checks and remaining limitations. Do not report format linting as end-to-end product validation.

## 10. Acceptance checklist

Implementation checks completed in this authoring session; evidence and limits are recorded in the [validation report](../../docs/validation.md). Browser checks are not a full accessibility or device certification.

- [x] Real file exists and can be executed without chat history; no unexplained reference IDs, local machine paths, or temporary links.
- [x] Large photographic hero and centered copy match the confirmed composition.
- [x] Exact section order and all copy in section 4 are present; no invented commercial facts or functional forms.
- [x] Shared accent, hover, and tint tokens match section 3 throughout components and interaction states.
- [x] Local image source and license are documented; missing-image fallback remains usable.
- [x] At 1280px and 400px viewport widths, no horizontal overflow; navigation, text, and actions remain visible.
- [x] Anchors navigate to real IDs; FAQ works by pointer and keyboard; focus is visible.
- [x] Measured text/background token pairs pass the stated contrast targets; hero scrim has sufficient contrast even over a bright photo region.
- [x] No image-generation, backend, analytics, account, or paid API dependency introduced.
- [x] Desktop/mobile screenshots depict the actual implementation. Unperformed checks are reported honestly.

## 11. Change log

- v1, 2026-10-26: first complete specification saved before website implementation. Real visual feedback confirms only large photography plus centered copy. Other parameters and fictional copy are design suggestions.
- v2, 2026-10-26, **test input**: change global accent from `#8B3E2F` to `#235343`, hover from `#6E2E24` to `#173F32`, tint from `#F0E2DB` to `#E3ECE4`; preserve all other text, layout, behavior, and asset requirements. This revision is a controlled test, not a new human preference. Token-referencing controls and acceptance rules inherit the updated values.
- v2.1, 2026-10-26: responsive acceptance width changed from 390px to the actually available 400px CSS viewport; the browser preview clamps its minimum width. No copy, palette, or layout rule changed.
- v2.2, 2026-10-26: made parameter provenance explicit beside each parameter group, added completed acceptance status with evidence, and retained all visual rules and copy.
