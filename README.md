# Pick Your Design

先看真实参考，再把选择变成可执行的设计规范。

**Pick Your Design** 是一个 AI 工作流技能，适用于网站、海报、品牌、图片和幻灯片。它通过真实参考和逐轮反馈明确方向，再细化内容与功能，实际保存可交给另一个 AI 执行的 `design-spec.md`。用户已授权创作时，继续使用宿主能力完成作品；只要求 MD 时，到文件交付即结束。

这不是独立应用，也不自带搜索、截图、图片显示、文件服务或创作服务。安装只提供工作流指令，这些能力由宿主提供。选型阶段默认零生图，不调用会后台自动生图的 image-picker；搜索、浏览和模型调用仍可能产生费用。

## 工作方式

1. 搜索并实际查看真实图片、网页截图、官方展示图或用户参考。
2. 第一轮实际显示 6–7 个有视觉差异的参考，附稳定编号、简短区别和来源；不足则少展示。
3. 等待真实反馈。支持单选、多选、混搭属性、只喜欢局部、全部拒绝、返回旧图、补充参考及跳过剩余轮次。
4. 后续默认每轮 4–6 个，保留已选锚点，针对 1–2 个未知维度重新搜索，通常 2–3 轮收敛。
5. 细化文案、功能和设计参数，保存详细 `design-spec.md`。数字标明用户确认或设计建议；缺失事实不编造。
6. 按已有授权继续制作，默认一个方案。只交 MD 不自动制作或发布；禁止全程生图时全程遵守。

规范覆盖需求与范围、参考取舍、视觉效果、具体参数、完整文案、网站响应式布局、交互状态、图片构图与光线、素材许可、未决问题、修改记录、生成执行指令和验收清单。不适用章节说明原因；关键事实缺失时标明草案与阻碍，不把空大纲当成成品。

局部修改保留其他要求，全局修改同步相关样式与内容；正文只保存最新有效规范，旧要求进入修改记录。

## 安装到本地 Codex

需要 Git，以及支持本地技能的 Codex 环境。以下使用官方文档列出的用户技能目录 `~/.agents/skills`，适用于 macOS/Linux shell；不是面向所有客户端的通用安装器。官方依据：[Build skills — Where Codex loads local skills](https://learn.chatgpt.com/docs/build-skills)，核对日期：2026-10-26。

在终端运行：

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/CATO2DL/choose-visual-direction.git "$HOME/.agents/skills/pick-your-design"
```

目录已存在时先检查其内容；不要删除或覆盖已有技能。Git 会拒绝克隆到已有的非空目录。安装后确认 `~/.agents/skills/pick-your-design/SKILL.md` 存在，再在 Codex 中输入 `$pick-your-design` 调用；若技能未出现，重启 Codex。

也可以下载此仓库，将包含 `SKILL.md` 的仓库根目录完整放入宿主支持的技能目录，并命名为 `pick-your-design`。其他宿主的目录、加载方式和工具能力应以其文档为准；本仓库不声称已验证其他客户端兼容性，也不是插件商店安装包。

仓库名是 `choose-visual-direction`，技能标识为 `pick-your-design`，显示名为 **Pick Your Design**。

## 调用示例

只生成规范：

```text
使用 $pick-your-design 为我的摄影作品集网站确定方向。
先展示真实参考让我选择，再细化页面、完整文案和交互。
最终保存 design-spec.md，本次只要 MD，不制作或发布网站。
```

规范后继续创作：

```text
使用 $pick-your-design 帮我做一张读书会海报。
选型阶段不要生图，先让我看真实参考并逐轮选择。
补齐文案和尺寸后保存 design-spec.md，再按规范制作一个方案。
最终创作可以生图，但不要公开发布。
```

混搭与修改：

```text
我喜欢 B 的布局和 E 的颜色，不喜欢 B 的照片。
下一轮只比较摄影方向，每轮给我六七个参考。
```

```text
使用 $pick-your-design 修改现有 design-spec.md：只调整按钮圆角，
其他要求保留；同步验收清单，旧值放修改记录。本次只更新 MD。
```

## 工具依赖与限制

- 需要宿主能搜索/浏览真实来源、让 AI 查看图片、向用户显示图片、接收反馈，以及写出文件。生成作品还需要对应的创作能力；本仓库不包含后端或运行时依赖。
- 图片必须真的显示。链接列表不是视觉选型；图片不可见时须说明限制。自定义界面不能回传点击时，用户在聊天中回复编号。
- 异步卡片排序不稳定时不能按位置建立固定编号。旧编号始终指向原图，新参考使用新编号。
- 选中参考不等于认可所有属性。未经用户确认的推断不能伪装成偏好；用户反馈只能来自用户。
- 参考不自动拥有商用或再分发许可。最终使用前核对许可和署名，不照搬独特品牌标志，不绕过访问限制。
- `design-spec.md` 是每次任务生成的项目文件，不是仓库附带的通用成品；它保存在用户项目中，不写入技能安装目录。若宿主不能保存文件，应如实报告，不能声称已完成。
- 不上传私人参考、原始聊天或凭据；本技能不自动发布任何用户作品。

## 文件

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | 触发说明、行为约束及主工作流 |
| [references/workflow.md](references/workflow.md) | 最小跨轮状态、展示适配与交互示例 |
| [references/design-spec-template.md](references/design-spec-template.md) | 详细生成规范的编写结构与完成标准 |
| [agents/openai.yaml](agents/openai.yaml) | 显示名称、简介与默认调用示例 |
| [LICENSE](LICENSE) | MIT 许可 |

## English

**Pick Your Design** is an AI workflow skill for websites, posters, brands, images, and slide decks. It searches real visual references, displays them for genuine user choices, refines content and functionality, and saves an actionable `design-spec.md` that another AI can execute without chat history. It continues to create the work only within the user's authorization. A Markdown-only request ends with the specification file.

Visual exploration uses zero image generation by default. The first round aims for 6–7 distinct references; later rounds usually show 4–6, including a selected anchor and a modest alternative. Users may combine attributes, reject a round, revisit references, add their own, or skip further rounds. Numeric design parameters identify user-confirmed values versus design proposals. Facts are never invented, and revisions keep only the latest requirements active.

This repository supplies instructions, not an application or bundled services. Search, browsing, screenshots, image inspection/display, file writing, and creation tools must come from the host. Tool and model usage may incur costs. Reference images require separate license checks before reuse; MIT does not license third-party images.

For local Codex, run the Git commands above to clone into `~/.agents/skills/pick-your-design`, then invoke `$pick-your-design`. Do not overwrite an existing skill directory; restart Codex if discovery does not update. See the linked official documentation for discovery locations. Other hosts require their own documented installation method; no cross-client compatibility is claimed.

Example: “Use $pick-your-design to explore real references for my portfolio website, refine the copy and behavior, and save a complete design-spec.md. Deliver Markdown only; do not build or publish the website.”

## License

[MIT](LICENSE) applies to this repository's original skill files. Third-party references and assets retain their own licenses.
