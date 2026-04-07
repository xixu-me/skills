# Agent Skills

**_[汉语](./README.zh.md)_**

> [!TIP]
> 欢迎加入“Xget 开源与 AI 交流群”，一起交流开源项目、AI 应用、工程实践、效率工具和独立开发；如果你也在做产品、写代码、折腾项目或者对开源和 AI 感兴趣，欢迎[**进群**](https://file.xi-xu.me/QR%20Codes/%E7%BE%A4%E4%BA%8C%E7%BB%B4%E7%A0%81.png)认识更多认真做事、乐于分享的朋友。

[Agent Skills](https://agentskills.io) maintained by me for practical engineering work. This repository is continuously updated.

## How To Use

You can use these skills in two ways:

1. Restore a reviewed baseline with [Skills Vault](https://github.com/xixu-me/skills-vault) and [`xixu-me/skvlt`](https://github.com/xixu-me/skvlt).
2. Add a source repository directly with `bunx skills add` or `npx skills add`.

> [!TIP]
> If you want a ready-to-use manifest of common skills, start with [`xixu-me/skvlt`](https://github.com/xixu-me/skvlt). Its `skvlt.yaml` is maintained as a reviewed baseline for a broader set of commonly used skills.

### Option 1: Use Skills Vault

Back up and restore through Skills Vault:

```bash
git clone https://github.com/xixu-me/skvlt.git
cd skvlt
bunx skvlt restore --all
```

This is the best option if you want a portable baseline that can be reapplied across machines.

### Option 2: Add Repositories Directly

Install this repository as a skill source:

```bash
bunx skills add xixu-me/skills
```

or:

```bash
npx skills add xixu-me/skills
```

## Skills Catalog

The table below lists the skills maintained in this repository.

| Name                                                                                                   | Description                                                                                                                                                      | Bundled Assets            |
| ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| [`develop-userscripts`](./skills/develop-userscripts/SKILL.md)                                         | Build, debug, package, and publish browser userscripts for Tampermonkey and ScriptCat, including ScriptCat background, cron, config, and subscription workflows. | `references/`             |
| [`github-actions-docs`](./skills/github-actions-docs/SKILL.md)                                         | Write, migrate, secure, and troubleshoot GitHub Actions workflows with official docs.                                                                            | `references/`             |
| [`openclaw-secure-linux-cloud`](./skills/openclaw-secure-linux-cloud/SKILL.md)                         | Securely self-host OpenClaw on cloud servers.                                                                                                                    | `references/`             |
| [`opensource-guide-coach`](./skills/opensource-guide-coach/SKILL.md)                                   | Start, grow, govern, fund, and sustain open source projects.                                                                                                     | `references/`             |
| [`readme-i18n`](./skills/readme-i18n/SKILL.md)                                                         | Translate repository READMEs, maintain localized variants, and add a language selector without breaking Markdown mechanics.                                      | `references/`             |
| [`running-claude-code-via-litellm-copilot`](./skills/running-claude-code-via-litellm-copilot/SKILL.md) | Route Claude Code through LiteLLM and GitHub Copilot, including setup and troubleshooting.                                                                       | `references/`             |
| [`secure-linux-web-hosting`](./skills/secure-linux-web-hosting/SKILL.md)                               | Harden cloud servers and web hosting for DNS, SSH, reverse proxies, HTTPS, and safe self-hosting.                                                                | `references/`             |
| [`skills-cli`](./skills/skills-cli/SKILL.md)                                                           | Discover, install, list, back up, restore, sync, and manage Agent Skills.                                                                                        | None                      |
| [`tzst`](./skills/tzst/SKILL.md)                                                                       | Create, extract, list, test, install, and script `tzst` CLI workflows for `.tzst` archives safely.                                                               | `references/`             |
| [`use-my-browser`](./skills/use-my-browser/SKILL.md)                                                   | Use the user's live browser session when work depends on rendered state, logged-in flows, uploads, media, DOM inspection, or browser-only failures.              | `references/`             |
| [`xdrop`](./skills/xdrop/SKILL.md)                                                                     | Upload to and download from Xdrop through the terminal, including encrypted share-link workflows.                                                                | `scripts/`                |
| [`xget`](./skills/xget/SKILL.md)                                                                       | Configure and apply Xget acceleration to URLs, package managers, registries, containers, CI, and AI SDKs.                                                        | `references/`, `scripts/` |

## Repository Layout

Each skill lives in its own folder and follows the Agent Skills specification:

```text
skills/
  <skill-name>/
    SKILL.md
    references/   # optional
    scripts/      # optional
```

Skills are designed for progressive disclosure: agents load the instructions only when the task calls for them, while bundled references and scripts stay with the skill for repeatable execution.

## Notes

- This repository is meant to evolve over time as new workflows appear.
- `xixu-me/skvlt` is the easiest way to restore a reviewed common baseline.
- Direct `bunx` or `npx` installation is better when you only want a specific source repository.

## License

Licensed under MIT License. See [`LICENSE`](./LICENSE).
