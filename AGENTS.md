# AGENTS.md

## Project Overview

This repository maintains a curated set of Agent Skills for practical engineering work.

- Main content lives in [`skills/`](./skills), with one folder per skill.
- Skills are Markdown-first artifacts built around a required `SKILL.md` file plus optional bundled assets.
- The repository is intentionally lightweight: formatting is the only automated check in CI.

Key technologies:

- Markdown for all skill instructions and references
- Node.js + npm for repository tooling
- Prettier for Markdown formatting checks
- GitHub Actions for CI formatting validation and optional formatting fixes

## Repository Layout

Expected structure for each skill:

```text
skills/
  <skill-name>/
    SKILL.md
    references/   # optional supporting docs
    scripts/      # optional executable helpers
```

Top-level files to keep in sync when relevant:

- [`README.md`](./README.md): English repository overview and skill catalog
- [`README.zh.md`](./README.zh.md): Chinese repository overview
- [`.github/workflows/markdown.yml`](./.github/workflows/markdown.yml): Markdown formatting CI
- [`.github/workflows/markdown-fix.yml`](./.github/workflows/markdown-fix.yml): manual workflow to format and commit Markdown changes

## Setup Commands

Install the repository tooling:

```bash
npm ci
```

Check Markdown formatting:

```bash
npm run check:md
```

Format Markdown files in place:

```bash
npm run format:md
```

## Development Workflow

When adding or editing a skill:

1. Work inside the relevant folder under `skills/<skill-name>/`.
2. Keep the core instructions in `SKILL.md`.
3. Put large reference material in `references/` instead of bloating `SKILL.md`.
4. Put reusable helper scripts in `scripts/` when the workflow benefits from execution instead of long pasted commands.
5. Update the repository catalog in [`README.md`](./README.md) when adding, renaming, or removing a skill.
6. Update [`README.zh.md`](./README.zh.md) when the change affects user-facing repository guidance there as well.

This repository follows progressive disclosure: agents should load bundled references and scripts only when a task actually calls for them.

## Testing And Validation

There is no unit test suite in this repository today. The primary validation is Markdown formatting plus a careful review of skill structure and links.

Before finishing a change, run:

```bash
npm run check:md
```

If formatting fails, run:

```bash
npm run format:md
```

Then re-run:

```bash
npm run check:md
```

If you changed workflow or package metadata, make sure those files still align with the commands above:

- [`package.json`](./package.json)
- [`.github/workflows/markdown.yml`](./.github/workflows/markdown.yml)
- [`.github/workflows/markdown-fix.yml`](./.github/workflows/markdown-fix.yml)

## Code Style And Authoring Conventions

- Follow [`.editorconfig`](./.editorconfig): UTF-8, LF line endings, spaces, width 2.
- Markdown formatting is governed by [`.prettierrc.json`](./.prettierrc.json), which preserves prose wrapping.
- Prefer clear, execution-oriented instructions over background exposition.
- Keep `SKILL.md` focused on when to use the skill and how to execute it.
- Avoid duplicating large documentation inside `SKILL.md`; move supporting material into `references/`.
- Keep examples and commands copy-pasteable.
- Use relative repository links for files in this repo.
- When linking to another repo file and the link text is the filename or path itself, format it as [`path/to/file.ext`](./path/to/file.ext). If the link text is descriptive text rather than a filename, keep the descriptive label.
- Format bare URLs shown directly in prose as autolinks, for example `<https://example.com>`.

## CI And Deployment

GitHub Actions runs Markdown formatting checks on pushes and pull requests that touch Markdown or formatting-related config.

- CI workflow: [`.github/workflows/markdown.yml`](./.github/workflows/markdown.yml)
- Manual formatting workflow: [`.github/workflows/markdown-fix.yml`](./.github/workflows/markdown-fix.yml)

There is no application deployment pipeline in this repository.

## Pull Request Guidelines

Before opening or updating a PR:

- Run `npm run check:md`.
- If you added a new skill, verify its folder matches the expected layout.
- Verify README catalog entries and links still resolve.
- Keep changes scoped to the skill or documentation you intended to modify.

## Agent Notes

- Prefer small, targeted edits over broad rewrites across many skills.
- Do not introduce extra tooling unless the repository actually needs it; the current workflow is intentionally minimal.
- If you add scripts to a skill, keep them colocated under that skill's `scripts/` directory.
- If a skill becomes large or complex, keep the instruction surface in `SKILL.md` concise and push details into bundled references.
