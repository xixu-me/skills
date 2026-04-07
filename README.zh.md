# Agent Skills

**_[English](./README.md)_**

> [!TIP]
> 欢迎加入“Xget 开源与 AI 交流群”，一起交流开源项目、AI 应用、工程实践、效率工具和独立开发；如果你也在做产品、写代码、折腾项目或者对开源和 AI 感兴趣，欢迎[**进群**](https://file.xi-xu.me/QR%20Codes/%E7%BE%A4%E4%BA%8C%E7%BB%B4%E7%A0%81.png)认识更多认真做事、乐于分享的朋友。

由我维护的、用于实际工程工作的 [Agent Skills](https://agentskills.io)。该存储库会持续更新。

## 如何使用

你可以通过两种方式使用这些 skills：

1. 使用 [Skills Vault](https://github.com/xixu-me/skills-vault) 和 [`xixu-me/skvlt`](https://github.com/xixu-me/skvlt) 恢复一套经过审阅的基线配置。
2. 直接用 `bunx skills add` 或 `npx skills add` 添加源存储库。

> [!TIP]
> 如果你想直接使用一份现成的常用 skills 清单，建议从 [`xixu-me/skvlt`](https://github.com/xixu-me/skvlt) 开始。它的 `skvlt.yaml` 维护了一套覆盖更广、经过审阅的常用基线。

### 方案 1：使用 Skills Vault

通过 Skills Vault 备份和恢复：

```bash
git clone https://github.com/xixu-me/skvlt.git
cd skvlt
bunx skvlt restore --all
```

如果你希望在多台机器之间复用一套可移植基线，这是最合适的方式。

### 方案 2：直接添加存储库

将该存储库作为 skill source 安装：

```bash
bunx skills add xixu-me/skills
```

或者：

```bash
npx skills add xixu-me/skills
```

## Skills 目录

下表列出了此存储库中维护的 skills。

| 名称                                                                                                   | 说明                                                                                                                       | 附带资源                  |
| ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| [`develop-userscripts`](./skills/develop-userscripts/SKILL.md)                                         | 为 Tampermonkey 和 ScriptCat 编写、调试、打包并发布浏览器 userscripts，包括 ScriptCat 的后台、定时、用户配置和订阅工作流。 | `references/`             |
| [`github-actions-docs`](./skills/github-actions-docs/SKILL.md)                                         | 基于官方文档编写、迁移、加固并排查 GitHub Actions workflows。                                                              | `references/`             |
| [`openclaw-secure-linux-cloud`](./skills/openclaw-secure-linux-cloud/SKILL.md)                         | 在云服务器上安全地自托管 OpenClaw。                                                                                        | `references/`             |
| [`opensource-guide-coach`](./skills/opensource-guide-coach/SKILL.md)                                   | 启动、发展、治理、资助并长期维护开源项目。                                                                                 | `references/`             |
| [`readme-i18n`](./skills/readme-i18n/SKILL.md)                                                         | 翻译存储库 README、维护多语言 README 变体，并在不破坏 Markdown 结构的前提下添加语言切换器。                                | `references/`             |
| [`running-claude-code-via-litellm-copilot`](./skills/running-claude-code-via-litellm-copilot/SKILL.md) | 通过 LiteLLM 和 GitHub Copilot 路由 Claude Code，并完成安装配置与排障。                                                    | `references/`             |
| [`secure-linux-web-hosting`](./skills/secure-linux-web-hosting/SKILL.md)                               | 加固云服务器与网站托管的 DNS、SSH、反向代理、HTTPS 和安全自托管配置。                                                      | `references/`             |
| [`skills-cli`](./skills/skills-cli/SKILL.md)                                                           | 发现、安装、列出、备份、恢复、同步并管理 Agent Skills。                                                                    | 无                        |
| [`tzst`](./skills/tzst/SKILL.md)                                                                       | 安全地创建、解压、列出、校验、安装并脚该化 `tzst` CLI 的 `.tzst` 档案工作流。                                              | `references/`             |
| [`use-my-browser`](./skills/use-my-browser/README.zh.md)                                               | 操作用户当前的浏览器会话、承接 DevTools 上下文，并在公共网页工具、实时浏览器会话和干净浏览器上下文之间路由网页任务。       | `references/`             |
| [`xdrop`](./skills/xdrop/SKILL.md)                                                                     | 通过终端上传到和下载自 Xdrop，并处理加密分享链接工作流。                                                                   | `scripts/`                |
| [`xget`](./skills/xget/SKILL.md)                                                                       | 将 Xget 加速能力应用到 URL、包管理器、存储库、容器、CI 和 AI SDK 等场景。                                                  | `references/`, `scripts/` |

## 存储库结构

每个 skill 都位于独立目录中，并遵循 Agent Skills 规范：

```text
skills/
  <skill-name>/
    SKILL.md
    references/   # 可选
    scripts/      # 可选
```

这些 skills 采用渐进式披露设计：只有当任务真正需要时，智能体才会加载对应说明；而配套的 references 和 scripts 会跟随 skill 一起保留，以便重复执行。

## 说明

- 该存储库会随着新工作流的出现持续演进。
- `xixu-me/skvlt` 是恢复一套经过审阅的常用基线最简单的方式。
- 如果你只想使用某个特定源存储库，直接通过 `bunx` 或 `npx` 安装会更合适。

## 许可证

基于 MIT 许可证发布。详见 [`LICENSE`](./LICENSE)。
