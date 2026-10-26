# Controlled behavior checks

Date: 2026-10-26. These are **test inputs**, not additional user choices or fabricated conversations. They were exercised by the current authoring agent reading the skill. They are not independent model evaluations and do not establish reliability across clients or repeated runs.

## MD-only and no image generation

The complete v1 specification was written and read before `site/index.html` existed. The filesystem checkpoint returned `site/index.html exists = False`. A palette revision was then applied to the MD. Only afterward did the authoring task's separate authorization to create the public example trigger implementation. This demonstrates the phase boundary in this run; it does not claim a separate user session was launched. No image-generation tool was called in reference selection or implementation.

## Existing-spec revision

Test input: change accent/hover/tint to `#235343` / `#173F32` / `#E3ECE4`, preserving everything else. The actual file was rewritten. A comparison normalized only the version and three color replacements and verified the rest of the current body was identical. The full-copy section's before/after SHA-256 values match in [revision-check.json](revision-check.json). Old colors remain only in the change log. The subsequent v2.1 entry records the measured mobile test width separately. The page uses shared CSS tokens, including hover and tinted backgrounds.

## Search unavailable: supplied-reference path

Controlled constraint: perform no web search for this check. Treat the already inspected local [CC0 library photograph](site/assets/library.jpg) as a tester-supplied reference; known provenance comes from the existing asset record, not a fresh search. Test input chooses its warm wooden interior and asks for a Markdown-only one-screen concept. The authoring agent wrote [a standalone fallback specification](checks/no-search/design-spec.md). No HTML or generated image was produced in that check directory. This tests a constrained workflow, not an actual outage or a new human image selection.

## Image display unavailable

Controlled input: “No image display is available, and no local board can be opened. I still want a spec.” The response is: “I cannot show candidates here, so visual selection is incomplete. Supply references through a supported viewer, pause, or explicitly skip selection and proceed with labeled assumptions.” This check stops at that clarification. It does not invent a choice or claim to have completed visual selection. The main case separately verified the real local-board path with all images loaded and chat feedback.

## All references disliked

Controlled state: confirmed requirements are English, one page, no generated imagery, and F's photographic composition; new comparison images are G/H/I.

- Test input “I dislike all of these” is ambiguous. Applied outcome: retain all state, ask whether this rejects G/H/I only or also F, and pause dependent work. Do not infer a new preference.
- Explicit test input “Reject this round's new images, keep F” yields rejected IDs G/H/I, retained anchor F, and unchanged English/one-page/no-generation requirements. No further searching is needed if the test input also says to start.
- Explicit test input “Reject F too” removes the visual anchor while preserving English/one-page/no-generation requirements. It does not reset unrelated facts.

These are documented state transitions performed as a controlled instruction walkthrough. They are **not** a live rejection by the person who selected F, nor an independently executed client dialogue. Broader automated behavioral evaluation remains unverified.

## Page asset failure

A temporary copy of the actual HTML referenced an intentionally nonexistent JPEG. The browser returned image natural width 0, displayed “Illustrative photograph unavailable.”, preserved the solid dark hero and readable copy, and had no horizontal overflow at 400px. The broken image element is hidden on error. This test copy is not part of the production example.
