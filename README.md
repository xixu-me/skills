# Agent Skills

**_[汉语](./README.zh.md)_**

[Agent Skills](https://agentskills.io) maintained by me for practical engineering work.

This repository is continuously updated. I also maintain bundled skills in [`xixu-me/xget`](https://github.com/xixu-me/xget) and [`xixu-me/xdrop`](https://github.com/xixu-me/xdrop).

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

Install the bundled skill sources from `xixu-me/xget` and `xixu-me/xdrop`:

```bash
bunx skills add xixu-me/xget
bunx skills add xixu-me/xdrop
```

or:

```bash
npx skills add xixu-me/xget
npx skills add xixu-me/xdrop
```

## Skills Catalog

The table below lists the skills maintained across this repository and the related bundled-skill repositories.

| Skill                                                                                                | Description                                                                                                                                     | Bundled Assets            |
| ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| [GitHub Actions Docs](./skills/github-actions-docs/SKILL.md)                                         | Official-docs-grounded help for writing, migrating, securing, and troubleshooting GitHub Actions workflows.                                     | `references/`             |
| [OpenClaw Secure Linux Cloud](./skills/openclaw-secure-linux-cloud/SKILL.md)                         | Guidance for securely self-hosting OpenClaw on Linux VPS or cloud servers.                                                                      | `references/`             |
| [Open Source Guide Coach](./skills/opensource-guide-coach/SKILL.md)                                  | Coaching for starting, growing, governing, funding, and sustaining open source projects.                                                        | `references/`             |
| [Running Claude Code via LiteLLM Copilot](./skills/running-claude-code-via-litellm-copilot/SKILL.md) | Help for routing Claude Code through LiteLLM and GitHub Copilot, including setup and troubleshooting.                                           | `references/`             |
| [Secure Linux Web Hosting](./skills/secure-linux-web-hosting/SKILL.md)                               | Practical Linux VPS and web hosting hardening for DNS, SSH, reverse proxies, HTTPS, and safe self-hosting.                                      | `references/`             |
| [Skills CLI](./skills/skills-cli/SKILL.md)                                                           | Help for discovering, installing, listing, backing up, restoring, syncing, and managing Agent Skills.                                           | None                      |
| [Xget](https://github.com/xixu-me/xget/blob/main/skills/xget/SKILL.md)                               | Execution-focused skill for configuring and applying Xget acceleration to URLs, package managers, registries, containers, CI, and AI SDKs, etc. | `references/`, `scripts/` |
| [Xdrop](https://github.com/xixu-me/xdrop/blob/main/skills/xdrop/SKILL.md)                            | Skill for uploading to and downloading from Xdrop through the terminal, including encrypted share-link workflows.                               | `scripts/`                |

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
