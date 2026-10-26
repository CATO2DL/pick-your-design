# Pick Your Design

通过真实参考确定网站视觉方向，再把选择写成可直接执行的 `design-spec.md`。

[English](README.md)

## 看一个实际结果

[Small Hours 读书空间案例](examples/reading-room/README.md) 展示了 **真实网站参考 → 选择大幅摄影与居中文案 → 详细设计规范 → 可运行静态网页** 的关系。需求是虚构的演示项目，视觉选择在验证过程中由真实用户作出；后续颜色修改明确标为测试输入。

![案例网页的实际桌面截图](examples/reading-room/screenshots/desktop.jpg)

查看[参考与选择依据](examples/reading-room/references.md)、[完整规范](examples/reading-room/design-spec.md)和[网页源文件](examples/reading-room/site/index.html)。示例摄影有 CC0 来源记录；不再分发第三方网站截图。

## 安装

需要 **Node.js 22.20.0 或更新版本**、npm/npx、Git，以及能加载 skill 的客户端。在准备使用技能的项目目录运行：

```sh
npx skills add CATO2DL/pick-your-design --skill pick-your-design -a codex
```

这是通过现有 [skills CLI](https://github.com/vercel-labs/skills) 进行项目级安装，没有另造安装器。检查安装摘要，再用 `npx skills list -a codex` 查看结果。Claude Code、全局范围、技能发现和手动安装见[安装说明](docs/installation.md)。

## 开始第一个项目

在 Codex 中打开该项目，粘贴：

```text
使用 $pick-your-design 为一个小型读书空间网站确定视觉方向。
我还说不清喜欢的风格：先展示 6–7 个真实网站参考，图片必须可见，
编号固定、来源清楚，然后等待我选择。利用我已经提供的需求，
只问影响下一步的问题。进一步细化完整文案、页面结构、手机布局
和交互，在本项目保存完整的 design-spec.md。本次只交 Markdown，
不要生图、制作或发布网站。
```

已有图片或已有规范？使用[三个可直接复制的提示词](docs/first-use.md)。

## 接下来会发生什么

1. 看到带编号和来源的真实参考图片。可以回复一个编号、“B 的布局 + E 的颜色”，或只指出喜欢的局部。
2. 可以全不喜欢、返回旧参考、补充自己的图片，或跳过剩余轮次。选中一张图不等于认可其全部属性。
3. 后续通常每轮 4–6 张，只细化最关键的一两个未知维度，再补全内容、功能和具体设计参数。
4. 得到真实的 `design-spec.md` 文件：完整文案、布局、色值、字体、手机行为、素材、假设、修改记录、执行指令及验收标准。另一个 AI 不需要聊天历史也能理解。

只要求 Markdown 就到此结束。获得授权后，宿主可继续制作一个方案；公开发布也需要授权。海报、图片、品牌和幻灯片工作流继续保留，网站是第一个完成验证的案例。

## 所需能力与验证范围

本仓库提供工作流指令，不自带搜索、截图、图片显示或创作服务；安装技能不会增加这些工具。选型默认零生图；若用户全程禁止生图，最终制作也遵守。搜索和模型调用可能产生费用。

| 环境 | 2026-10-26 的验证层级 |
| --- | --- |
| 当前 Codex 桌面会话 | 完成网站流程演练：真实浏览、图片显示、真实用户视觉选择、文件输出和本地网页预览。通过明确读取文件加载技能指令。 |
| Codex CLI 0.163.0-alpha.11 | 安装及已启用的项目技能发现已验证；没有另开模型调用验证完整流程。 |
| Claude Code 安装目标 | 通过 skills CLI 1.7.4 验证安装、查看和卸载。本机没有 Claude Code，客户端加载及完整流程未验证。 |
| 其他客户端 | 未验证。安装器兼容不等于工作流通过。 |

宿主需要搜索/浏览、图片查看与用户可见的图片展示、聊天反馈及 Markdown 文件写入能力。继续做网站还需要文件创作和浏览器预览。[能力明细、版本与证据](docs/validation.md)。

无法搜索时，可以提供自己的参考图片。显示失败时优先使用宿主支持的图片方式，必要时用经过检查的本地参考板，再在聊天回复编号。仍无法显示时必须说明缺口，不能宣称完成视觉选型。[降级路径](docs/first-use.md#when-tools-are-missing)。

## 更新、卸载与常见问题

在同一个项目目录中，只更新这个技能：

```sh
npx skills update pick-your-design -p -y
```

更新前备份对已安装技能的本地修改。只卸载本技能的 Codex 安装：

```sh
npx skills remove pick-your-design -a codex -y
```

**技能没出现？** 检查项目目录和安装列表，必要时重新打开客户端。**安装了却没有图片？** 安装不会提供图片工具。**只想要规范？** 明确说“只交 Markdown”。**参考图能直接商用吗？** 需要单独核对许可。更多见[安装与故障排查](docs/installation.md)。

## 示例、许可与反馈

- [复现第一个网站案例](examples/reading-room/README.md)
- [首次使用提示词与降级路径](docs/first-use.md)
- [主工作流](SKILL.md)与[规范模板](references/design-spec-template.md)
- [验证报告](docs/validation.md)
- 原创文件使用 [MIT 许可](LICENSE)，示例照片另见[素材许可记录](examples/reading-room/site/assets/README.md)
- [提交问题](https://github.com/CATO2DL/pick-your-design/issues)

如果这个工作流对你有帮助，欢迎在 GitHub 点一个 Star。
