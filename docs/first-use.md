# Your first design specification

[English](../README.md) · [中文](../README.zh-CN.md)

Install in your working project, then open that project in a client that can load skills. In Codex use `$pick-your-design`. Claude Code documents `/pick-your-design`, but its runtime has not been tested here. For another client, use its documented invocation; do not assume either syntax works everywhere.

## 1. Start without a style in mind

```text
Use $pick-your-design for a small reading-space website. I cannot describe
my preferred style yet. Show 6–7 actual website references with visible
images, stable IDs, and source links, then wait for me. Start from the
requirements I have already given you; ask only what affects the next step.
Refine the selected direction, full copy, mobile layout, and interactions.
Save a self-contained design-spec.md. Markdown only: no image generation,
website creation, or publishing.
```

```text
使用 $pick-your-design 为一个小型读书空间网站确定方向。我说不清想要的风格，
先展示 6–7 个真实网站参考：图片实际可见、编号固定、来源清楚，等我选择。
利用我已提供的需求，只问影响下一步的问题。逐步明确完整文案、手机布局和交互，
保存可独立交接的 design-spec.md。只要 MD，不生图、不制作或发布网站。
```

## 2. Start with your own references

Attach images that you are allowed to share, then paste:

```text
Use $pick-your-design. Inspect the reference images I attached for my
website. Describe what you can actually see, then ask which attributes I
want to keep; do not treat every attribute as approved. Use my existing
requirements and help fill the remaining content and functionality gaps.
Save a complete design-spec.md with portable asset paths and source/usage
notes. Deliver Markdown only and do not generate images.
```

```text
使用 $pick-your-design。查看我附上的网站参考图片，描述实际可见特征，
只追问我想保留哪些属性，不把整张图的所有属性都视为认可。利用已有需求，
补齐内容和功能，保存完整 design-spec.md，使用可交接的素材路径和来源/使用说明。
只交付 MD，全程不生图。
```

## 3. Revise an existing specification

Place the file in your project, then paste:

```text
Use $pick-your-design to read ./design-spec.md. Change the global accent
to #235343, its hover state to #173F32, and its tinted surface to #E3ECE4.
Change the hero heading to “A little room for big ideas.” Preserve every
other piece of copy, layout, function, and requirement. Synchronize affected
component states and acceptance criteria. Keep only the current rules in
the main specification and move replaced rules into its change log. Save
the file; do not build or publish anything and do not generate images.
```

```text
使用 $pick-your-design 读取 ./design-spec.md。全局强调色改为 #235343，
悬停色改为 #173F32，浅色背景改为 #E3ECE4；首屏标题改为
“A little room for big ideas.”。保留其他所有文案、布局、功能及要求。
同步相关组件状态和验收标准，正文只保留最新要求，旧要求写入修改记录。
保存文件即可，不制作、不发布、不生图。
```

## What to reply after seeing references

“F's large photograph and centered copy” is more useful than silently approving every property of F. You can also say “B's layout with E's colors,” “none of these,” “return to A,” or “start now.” If you reject a later round, specify whether you mean only its new images or the earlier direction too. The skill should ask if that scope is ambiguous.

The normal first round has 6–7 distinct references, later rounds 4–6. A later round keeps an earlier anchor and explores one or two uncertain dimensions. Fewer images are acceptable if real suitable references cannot be found. The process usually converges in 2–3 rounds; you can stop sooner.

## When tools are missing

No additional paid service is required by this repository. First check what your current host already provides.

| Missing capability | Usable next step | Honest boundary |
| --- | --- | --- |
| Web search/browsing | Attach your own reference images and any known source/permission information. The host must inspect them. | No claim that an online search was performed. |
| Inline image display | Try the client's supported viewer. If local files and browser preview are available, create a small local HTML reference board with real images and fixed IDs. Open it and verify every image loaded. | No fake submit controls. Reply with IDs in chat if clicks cannot return feedback. |
| All reliable image display | State the gap. Ask the user to provide images through a supported channel, pause, or explicitly skip visual selection and draft with labeled assumptions. | A text list is not visual selection; do not quietly synthesize candidate images. |
| File writing | Explain that saving is blocked and provide the content for the user to save, if useful. | Do not claim a `design-spec.md` file was created. |
| Website creation/preview | Deliver the requested specification and portable sources. | Do not mark a website as built or tested. |

A local board is a per-project fallback, not a service installed by this skill. Keep private or unlicensed reference screenshots out of public repositories. Record stable source pages and textual design decisions in the handoff instead. The [example](../examples/reading-room/README.md) uses a licensed, local photograph for the actual page.

## After the specification

Read unresolved questions and proposed values. A complete spec can still contain clearly labeled design suggestions, but must not invent business facts. Ask for a change or authorize creation when ready. “Markdown only” means stop at the file. A ban on image generation applies throughout the task when stated that way.
