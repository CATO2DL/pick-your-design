# Validation report

Date: **2026-10-26**. This report distinguishes installation, client discovery, current-session workflow execution, and controlled behavior checks. It is not a promise of compatibility with every environment.

## Environment and isolation

- macOS; desktop app bundle version **26.1016.51333**; current Codex desktop session with web search, browser screenshots, inline local-image display, chat feedback, and filesystem tools.
- Codex CLI **0.163.0-alpha.11**. Its app-server was used only for `skills/list`, not a new paid model turn.
- Node **26.9.0**, npm **11.19.1**, skills CLI **1.7.4**. The installed CLI package declares Node **>=22.20.0**.
- Claude Code executable was absent.
- Installation tests ran in separate temporary project directories. npm cache and CLI state were redirected to temporary locations; `DO_NOT_TRACK=1` was set. No existing global skill or client configuration was overwritten. No update-all or remove-all command was used.
- Initial repository worktree was clean. Existing project name and remote were retained. Publishing is limited to this repository's original files, recorded CC0 asset, and screenshots of its own example.

## Capability levels

| Layer | Actual evidence | Status |
| --- | --- | --- |
| Skill discovery by installer | Public repository lists exactly one skill, `pick-your-design`. | Verified |
| Project installation | Named Codex and Claude Code targets installed into independent projects. | Verified |
| Codex client discovery | App-server `skills/list` returned `pick-your-design`, `enabled: true`, `scope: repo`. | Verified discovery; separate model invocation unverified |
| Current desktop workflow | Skill instructions read explicitly; real references searched, inspected, displayed; real feedback received; spec saved; page built and previewed. | Complete website workflow exercised in this session |
| Claude Code runtime | No local executable; no slash-command or model workflow run. | Installation only; runtime unverified |
| Search and browsing | Official live websites opened and visually checked; incomplete candidate excluded. | Verified in current host only |
| Image inspection/display | Two local reference boards with actual screenshots, image-load checks, and chat-visible images. | Verified in current host only |
| Markdown creation | Complete spec and controlled no-search fallback saved as files. | Verified |
| Website creation | Original static page, licensed photograph, desktop/mobile browser checks. | Verified locally; hosted deployment not performed |
| Other media/clients | Instructions retained for posters, images, brands, slides. | No full case validation yet |

The desktop run is an authoring-session workflow test, not proof that a newly installed skill automatically loads and behaves the same way in a fresh client session. Installer success and client discovery alone do not establish that.

## A. Installation commands exercised

All commands below used `CATO2DL/pick-your-design`, skill name `pick-your-design`, and project scope unless stated otherwise.

| Command | Observed result |
| --- | --- |
| `npx skills --help` and `npx skills --version` | Help inspected; version 1.7.4. |
| `npx skills add CATO2DL/pick-your-design --list` | Exactly one skill discovered. |
| `npx skills add CATO2DL/pick-your-design --skill pick-your-design -a codex -y` | Installed; files present in `.agents/skills/pick-your-design/`. |
| `npx skills list -a codex` | Listed the installed project skill and its GitHub source. |
| `npx skills add CATO2DL/pick-your-design --skill pick-your-design -a claude-code -y` | Installed; files present in `.claude/skills/pick-your-design/`. |
| `npx skills list -a claude-code` | Listed the project skill before removal. |
| `npx skills remove pick-your-design -a claude-code -y` | Removed one skill; subsequent scoped list reported no project skills. |
| `npx skills add CATO2DL/pick-your-design` | Worked in a fresh temporary project. The CLI detected an agent terminal and used a noninteractive path; interactive chooser not tested. |
| `npx skills update pick-your-design -p -y` | Initially reported up to date; after publication, updated exactly one skill to the new contents. |
| Manual whole-repository clone into `.agents/skills/pick-your-design` | Worked in a fresh temporary project; `git pull --ff-only` reported up to date. |

The recommended README command omits `-y` so the person can review installer prompts. The same named/client options were exercised with `-y` for isolated tests. Global commands were checked against current help/source but **not executed**. No global installation is claimed as verified.

### Post-publication checks

Release commit `d9fdcf3` was pushed to the existing public repository. A fresh named Codex installation succeeded. The previously installed project was updated with `npx skills update pick-your-design -p -y`, which reported exactly one updated skill. All 24 installed files in both projects matched the published release byte-for-byte. GitHub’s tree hashes also matched the local commit. Anonymous repository, both README files, specification, installation guide, desktop/mobile images, and photograph URLs returned HTTP 200.

Uninstall finding: `npx skills remove pick-your-design -a codex -y` reported success but retained the shared directory and lock entry because another detected client could use the same canonical path. The next listing still showed the skill. We then tested `npx skills remove pick-your-design -y`: only this named skill was removed from project client installations, its directory was gone, and the next Codex listing was empty. README instructions were corrected to this verified command. No remove-all command was used.

## B. Actual website case

See [initial brief](../examples/reading-room/initial-brief.md), [reference decisions](../examples/reading-room/references.md), and [specification](../examples/reading-room/design-spec.md).

- First round: six distinct real website views, A–F. Images were actually inspected and displayed, not inferred from titles. All six board images loaded. An incomplete candidate was excluded instead of filling the count with a broken view.
- A person selected F. A second round displayed the unchanged F anchor and G–I, four images total. New IDs were not reused. All four loaded.
- The person specifically chose **large photography and centered copy**. Other attributes remained design suggestions; no further questionnaire was imposed.
- The complete spec was saved before website source creation. A controlled palette revision followed, then the task's existing authorization was used to build the example.
- Public output contains original code, one CC0 photograph, and own-page screenshots. Selection screenshots, private chat logs, and credentials are absent.

### Browser results

| Check | Observed result |
| --- | --- |
| Desktop CSS viewport 1280 × 900 | Scroll width 1280; hero height 600; local image natural width 3026; no horizontal overflow. |
| Mobile CSS viewport 400 × 843 | Scroll width 400; hero height 520; h1 40px; About collapses to one column. |
| Additional mobile CSS viewport 480 × 1000 | Scroll width 480; Bring grid `36px 392px`; Questions single column `440px`; complete page visually inspected. |
| Hero CTA | Click changed fragment to `#about`; section top within 1px of viewport top. |
| Mobile navigation | Click changed fragment to `#bring`; section top within 1px of viewport top. |
| FAQ | Pointer opened disclosure; Enter closed it; focused SUMMARY had a solid outline. |
| Missing photograph | Temporary missing-file variant: image width 0, error message visible, failed image hidden, dark hero and readable copy retained. |
| Assets and document structure | Exact copy checked against HTML, navigation targets exist, relative asset present, one h1, system fonts, no backend. |

Preview zoom affected the relationship between requested tool dimensions and CSS pixels. Measurements above come from the rendered DOM, not requested dimensions. Screenshots were captured to the content bounds. The 400px [mobile first view](../examples/reading-room/screenshots/mobile.jpg) and 480px [full mobile page](../examples/reading-room/screenshots/mobile-full.jpg) are different measured widths. Physical-device and multi-browser testing were not performed.

Calculated contrast ratios: body on paper **12.61:1**; muted text on paper **5.52:1**; muted text on tinted section **5.18:1**; button label **8.58:1**, hover **11.43:1**; link on paper **7.74:1**. The light hero text over a white image region under the specified black scrim is **6.53:1**. These calculations support text contrast; they are not a full accessibility audit.

## C–E. Revision and behavior boundaries

- **C — actual palette edit:** [revision evidence](../examples/reading-room/revision-check.json) records equal full-copy hashes and a normalized-body comparison. Only version/palette changed in the tested revision; old colors are historical. A later logged change corrects the mobile acceptance width to the measured 400px.
- **D — missing tools:** an actual [Markdown-only fallback spec](../examples/reading-room/checks/no-search/design-spec.md) was written from an already inspected tester-supplied local reference, without new search. Image-display absence was a controlled instruction walkthrough ending in clarification, not a real outage. The local-board fallback was exercised in B.
- **E — MD only / generation ban / rejection:** the actual save-before-build checkpoint and zero image-generation calls cover this run. “All disliked” scenarios were controlled state-transition walkthroughs, explicitly marked test inputs. They were not real user feedback or fresh client sessions.

See [behavior checks](../examples/reading-room/behavior-checks.md) for inputs, responses, and limits. No independent paid model evaluations were launched to inflate compatibility claims.

## Repository checks and remaining limits

Markdown parsed, YAML/frontmatter validated, relative links and image paths checked, bilingual quick-start commands compared, and project text scanned for private paths or credential patterns. These checks supplement functional evidence above; they do not replace it.

The skill does not include search, screenshot, image display, or creation services. Costs depend on the host. Websites and CLI behavior can change. User-supplied references still need rights/access checks. Full workflows outside this local desktop environment, independent fresh-session activation, global installs, physical devices, and hosted publication remain unverified.

External-link check: 18 of 19 referenced public URLs returned HTTP 200. Aesop returned HTTP 403 to the plain HTTP checker; its page had already been viewed successfully in the browser during selection. No access restriction was bypassed, and automated fetch access is not promised.
