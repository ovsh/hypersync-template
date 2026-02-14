# HyperSync Registry Template

This is a template repository for [HyperSync](https://github.com/AugmentedAI/hypersync) -- a macOS menu-bar app that syncs AI agent configuration to your team.

## Getting Started

1. Click **Use this template** on GitHub to create your team's config repo
2. Edit the files under `global/` to add your team's rules, skills, and agents
3. Commit and push to `main`
4. Share the repo URL with your team -- they'll enter it in HyperSync's setup wizard

## Structure

```
manifest.json                    # Defines what gets synced where
global/
  cursor/
    rules/.cursorrules           # Cursor rules
    skills-cursor/               # Cursor skills
    AGENTS.md                    # Cursor agents
  claude/
    rules/CLAUDE.md              # Claude Code rules
    skills/                      # Claude Code skills
    AGENTS.md                    # Claude Code agents
```

## Manifest

The `manifest.json` file maps source paths in this repo to destinations under `~/` on each team member's machine. Only `~/.cursor/` and `~/.claude/` are allowed as destinations.

```json
{
  "source": "global/cursor/rules",
  "destination": ".cursor/rules",
  "kind": "directory",
  "strategy": "replace"
}
```

- `source`: path inside this repo
- `destination`: path under `~/`
- `kind`: `file` or `directory`
- `strategy`: `replace` (removes old files before copying)

## Adding Content

Add files directly to the appropriate folders. HyperSync will sync them on the next pull.

For example, to add a new Claude skill:
1. Create a file in `global/claude/skills/my-skill.md`
2. Commit and push
3. Team members get it on their next sync (auto-syncs every 60 minutes by default)
