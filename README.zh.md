# Agent Skills

**_[English](./README.md)_**

由我维护的、用于实际工程工作的 [Agent Skills](https://agentskills.io)。

本存储库会持续更新。我也在 [`xixu-me/xget`](https://github.com/xixu-me/xget) 和 [`xixu-me/xdrop`](https://github.com/xixu-me/xdrop) 中维护了它们附带的 skills。

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

将本存储库作为 skill source 安装：

```bash
bunx skills add xixu-me/skills
```

或者：

```bash
npx skills add xixu-me/skills
```

安装 `xixu-me/xget` 和 `xixu-me/xdrop` 中打包的 skill sources：

```bash
bunx skills add xixu-me/xget
bunx skills add xixu-me/xdrop
```

或者：

```bash
npx skills add xixu-me/xget
npx skills add xixu-me/xdrop
```

## Skills 目录

下表列出了此存储库及相关附带 skills 的存储库中维护的 skills。

| 名称                                                                                                 | 说明                                                                                            | 附带资源                  |
| ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------- |
| [github-actions-docs](./skills/github-actions-docs/SKILL.md)                                         | 基于官方文档，帮助编写、迁移、加固和排查 GitHub Actions workflows。                             | `references/`             |
| [openclaw-secure-linux-cloud](./skills/openclaw-secure-linux-cloud/SKILL.md)                         | 为在 Linux VPS 或云服务器上安全自托管 OpenClaw 提供指导。                                       | `references/`             |
| [opensource-guide-coach](./skills/opensource-guide-coach/SKILL.md)                                   | 为开源项目的启动、增长、治理、资助与长期维护提供辅导。                                          | `references/`             |
| [running-claude-code-via-litellm-copilot](./skills/running-claude-code-via-litellm-copilot/SKILL.md) | 帮助通过 LiteLLM 和 GitHub Copilot 路由 Claude Code，包括安装配置与排障。                       | `references/`             |
| [secure-linux-web-hosting](./skills/secure-linux-web-hosting/SKILL.md)                               | 提供 DNS、SSH、反向代理、HTTPS 和安全自托管相关的 Linux VPS / Web Hosting 实践指南。            | `references/`             |
| [skills-cli](./skills/skills-cli/SKILL.md)                                                           | 帮助发现、安装、列出、备份、恢复、同步和管理 Agent Skills。                                     | 无                        |
| [xget](https://github.com/xixu-me/xget/blob/main/skills/xget/SKILL.md)                               | 面向执行的 skill，用于将 Xget 加速能力应用到 URL、包管理器、存储库、容器、CI 和 AI SDK 等场景。 | `references/`, `scripts/` |
| [xdrop](https://github.com/xixu-me/xdrop/blob/main/skills/xdrop/SKILL.md)                            | 通过终端上传到和下载自 Xdrop 的 skill，也覆盖加密分享链接工作流。                               | `scripts/`                |

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

- 本存储库会随着新工作流的出现持续演进。
- `xixu-me/skvlt` 是恢复一套经过审阅的常用基线最简单的方式。
- 如果你只想使用某个特定源存储库，直接通过 `bunx` 或 `npx` 安装会更合适。

## 许可证

基于 MIT 许可证发布。详见 [`LICENSE`](./LICENSE)。
