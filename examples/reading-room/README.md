# Small Hours: from references to a working page

A fictional reading-space website used to exercise Pick Your Design on 2026-10-26. The source and screenshots are real outputs, not mock links or generated demo images.

1. [Initial brief](initial-brief.md): purpose, scope, and fictional content boundaries.
2. [References and decisions](references.md): six real websites in round one, followed by the selected anchor and three new comparisons. A person chose large photography with centered copy.
3. [Complete design-spec.md](design-spec.md): self-contained copy, concrete design parameters, responsive behavior, assets, interaction states, execution instructions, and acceptance criteria.
4. [Revision evidence](revision-check.json): a **test input** changed the accent palette globally; copy and unrelated body requirements stayed identical.
5. [Working page](site/index.html): original HTML/CSS and a licensed photograph. GitHub shows its source; this link is not a hosted website.

![Actual desktop output](screenshots/desktop.jpg)

[Actual mobile screenshot](screenshots/mobile.jpg) · [Photo source and CC0 license](site/assets/README.md) · [Test report](../../docs/validation.md)

Only the photographic scale and centered text were human-confirmed. The name, fictional concept, copy, exact parameters, and palette are labeled design suggestions. The color edit is a controlled test, not a customer request. No private chat logs or third-party website screenshots are included.

## Reproduce the workflow in a new project

Create a new project folder and run the recommended command there:

```sh
npx skills add CATO2DL/pick-your-design --skill pick-your-design -a codex
```

Open that folder in Codex with browsing, image viewing/display, and file writing available. Paste:

```text
Use $pick-your-design. Make a specification for a fictional one-page
English reading-space website. Explain the concept, what to bring, and
basic questions. Do not invent real venue details or booking functions.
Show 6–7 real website references with visible images and stable IDs, then
wait for me. Refine the direction and save ./design-spec.md with full copy,
mobile layout, interactions, assets, and acceptance criteria. Markdown only;
do not generate images, build, or publish the website.
```

Reply with the attributes you actually like. To follow this example's direction, choose large photography with centered copy when you see an appropriate reference. Do not blindly reply “F”: new searches can use different IDs. The agent should save the file in your project, outside the installed skill folder.

Review the proposed parameters. To continue, explicitly say: “Build one local static page from design-spec.md. Use licensed assets, generate no images, preview desktop and mobile, and do not publish.” Without that instruction, the Markdown-only flow stops at the specification.

Search results and AI output can differ from this recorded run. If tools are missing, use the [supported-reference fallback](../../docs/first-use.md#when-tools-are-missing).

## Run the exact saved page

Clone the public example into a new folder:

```sh
git clone https://github.com/CATO2DL/pick-your-design.git
cd pick-your-design
python3 -m http.server 8766 --bind 127.0.0.1 --directory examples/reading-room/site
```

Then open `http://127.0.0.1:8766/` in your browser. Python 3 is needed only for this preview command, not for the skill or CLI installation. The page also uses ordinary relative files and has no build step. If port 8766 is occupied, choose an unused local port. Stop the server with Ctrl-C.

Verified CSS viewport widths were 1280px and 400px. These are browser previews, not tests on physical devices. Screenshots show the actual page; there is no hosted deployment, backend, signup, or generated imagery. [Controlled behavior checks](behavior-checks.md) describe additional limits and tests.
