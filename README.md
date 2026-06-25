# Skillful

A collection of skills for coding assistants, focused on security and code review.
Skills are authored once in an agent-neutral format and installed into whichever
assistant you use.

## Supported agents

- Claude (Claude Code)
- OpenAI Codex
- Kiro

## Install the CLI

```bash
pip install -e .
```

This exposes the `skillful` command.

## Usage

```bash
# See what's available
skillful list

# Install a skill for Claude into the current project
skillful install security-review --agent claude

# Install every compatible skill globally for Codex
skillful install --all --agent codex --scope global

# Remove a skill
skillful uninstall security-review --agent claude
```

`--scope project` (default) writes into the current directory; `--scope global`
writes into your home directory. Where exactly each agent looks is documented in
[docs/adapters.md](docs/adapters.md).

## Authoring skills

Each skill is a directory under `skills/` containing a `meta.yaml` and a
`skill.md`. See [docs/authoring-skills.md](docs/authoring-skills.md).
