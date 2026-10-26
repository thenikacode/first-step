# Changelog

All notable changes to First Step are listed here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-10-26

First public release.

### Added

- The `first-step` skill: one Markdown file of instructions. You give your agent a rough idea, it asks one question per turn, and it stops when it can name a small first step and a way to check it.
- `agents/openai.yaml`, with the name, short description and default prompt that Codex shows.
- A Claude Code plugin and a marketplace in this repository: `/plugin install first-step --marketplace thenikacode/first-step` in Claude Code 2.1.275 or later.
- Install with the skills CLI (`npx skills add thenikacode/first-step -g`), or copy `skills/first-step` into `~/.agents/skills/` for Codex.
- A real run on a made-up idea, unedited, in `examples/weekly-commit-update.md`.

### Known issues

- It has no memory between chats.
- Answers change from one model to another, and from one run to the next.
- Not tested yet in the Claude app.

[Unreleased]: https://github.com/thenikacode/first-step/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/thenikacode/first-step/releases/tag/v0.1.0
