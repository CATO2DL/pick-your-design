# Installation and maintenance

[English quick start](../README.md) · [中文快速开始](../README.zh-CN.md)

Tested on 2026-10-26 with skills CLI **1.7.4**, Node **26.9.0**, npm **11.19.1**, Git, and macOS. That CLI's published package declares **Node >=22.20.0**. Install a supported Node release and ensure `node --version`, `npm --version`, and `git --version` work. The commands below use the existing skills package from npm; no package from this repository needs publishing. Network access to npm and GitHub is needed for installation.

## Recommended: install in one project

Open a terminal in the project you will work on:

```sh
npx skills add CATO2DL/pick-your-design --skill pick-your-design -a codex
npx skills list -a codex
```

The first npm invocation may ask to download the skills CLI. Review that package and the installation summary. Project installation makes the skill available to that project; it does not install search or image tools. In this test the Codex files landed in `.agents/skills/pick-your-design/`.

Open the same project in Codex. Its explicit invocation is `$pick-your-design`, followed by your request. We verified Codex's repository-skill discovery through its app-server; a separately launched Codex model turn was not tested. See the [validation report](validation.md).

## Other verified installation entry points

Discover the skill without installing it:

```sh
npx skills add CATO2DL/pick-your-design --list
```

Use the normal installer entry point:

```sh
npx skills add CATO2DL/pick-your-design
```

The CLI can offer interactive choices. In our agent-run terminal it detected the environment and completed noninteractively; we did not test the interactive chooser. Use the explicit client option to avoid ambiguity.

Install for Claude Code in a project:

```sh
npx skills add CATO2DL/pick-your-design --skill pick-your-design -a claude-code
npx skills list -a claude-code
```

Installation was verified at `.claude/skills/pick-your-design/`. Claude Code itself is not installed on the test machine. Its documented explicit invocation is `/pick-your-design`; this has **not** been executed here. Do not infer end-to-end compatibility from installation alone.

## Global scope (documented, not executed in our tests)

To make it available across your own projects, use `-g`:

```sh
npx skills add CATO2DL/pick-your-design --skill pick-your-design -a codex -g
npx skills list -g -a codex
npx skills update pick-your-design -g -y
npx skills remove pick-your-design -g -a codex -y
```

Project scope is the default. Global scope writes to user-level locations and can affect multiple projects. We deliberately tested only temporary project installations, not your global configuration. Avoid installing both scopes unless you understand which version your client loads.

## Update or remove only this skill

From the installed project:

```sh
npx skills update pick-your-design -p -y
npx skills remove pick-your-design -a codex -y
```

For a Claude Code project, use `-a claude-code` in the removal command. Back up local edits first. The named update is project-scoped; it does not request updates to all your skills. `-y` skips confirmation, so check the name and current directory before running it.

## Manual fallback

For Codex, from your project root, clone the **whole repository** into a new, empty skill directory:

```sh
mkdir -p .agents/skills
git clone https://github.com/CATO2DL/pick-your-design.git .agents/skills/pick-your-design
```

Git refuses an existing nonempty destination. Do not copy only `SKILL.md`: its relative links need `references/` and the other files. Reopen the project if the client has cached its skill list. This is a manual checkout, not a skills-CLI-managed installation; do not assume CLI update/remove will maintain it. To update an unmodified checkout, run `git -C .agents/skills/pick-your-design pull --ff-only`; inspect local changes before doing so. To uninstall manually, remove only that checkout after backing up any edits.

For Claude Code the documented project location is `.claude/skills/pick-your-design/`; the same whole-directory layout applies, but this manual target was not tested here.

## Troubleshooting

- **Wrong directory or missing skill:** inspect the installation summary, run the scoped listing, and open that same project in the client. A name in a CLI list is not proof that a model loaded it.
- **Node error:** compare `node --version` with the CLI requirement above. A future CLI version may change its minimum; check its current package metadata.
- **No pictures:** follow the [capability fallback](first-use.md#when-tools-are-missing). Installing this skill adds instructions, not browsing services.
- **Proxy/login/network failure:** use your normal GitHub/npm setup; do not paste credentials into chat. A local copy of the complete repository can be installed manually.
- **Updates overwrite local edits:** keep project output outside the installed skill folder and back up intentional edits before updating.

## Sources

Commands and requirements were checked against [skills README](https://github.com/vercel-labs/skills), [commands](https://github.com/vercel-labs/skills/blob/main/docs/commands.md), [creating skills](https://github.com/vercel-labs/skills/blob/main/docs/creating-skills.md), and the installed 1.7.4 package. The inspected source revision was `a80e4c9d12d607631249d4d7d059f835d4b2f13a`. Client guidance: [OpenAI skills documentation](https://learn.chatgpt.com/docs/build-skills) and [Claude Code skills documentation](https://code.claude.com/docs/en/skills). Client behavior and CLI versions can change.
