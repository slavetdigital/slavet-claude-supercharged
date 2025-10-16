# Slevet Claude Supercharged

An opinionated, ready-to-paste Claude Code plugin marketplace for Slavēt Digital, preconfigured to distribute the `slavet-claude` plugin. Use it locally for rapid development or host it on GitHub for organization-wide distribution.

- **Marketplace name**: Slevet Claude Supercharged
- **Included plugin (local source)**: `slavet-claude`
- **Purpose**: Provide guardrails, memory, checkpoints, JSON/diff/flag verification, auto hooks, and minimal MCP integration for robust workflows.

## What’s inside

```
slevet-claude-supercharged/
├─ .claude-plugin/
│  └─ marketplace.json       # Marketplace definition with the slavet-claude entry
└─ plugins/
   └─ slavet-claude/         # (Optional) Local copy of the plugin for development
```

## Features at a glance

- **Local-first marketplace**: Add from your filesystem to iterate quickly.
- **GitHub distribution**: Host and install directly in Claude Code via URL.
- **Plugin development loop**: Swap between local folder source and Git source easily.
- **Spec-compliant**: Works with Claude Code’s marketplace and plugin install flow.

## Install and use

Choose local development for the fastest iteration, or GitHub for shared distribution.

### Option A — Local development (fastest)

1) Add the marketplace:
```
/plugin marketplace add /absolute/path/to/slevet-claude-supercharged
```

2) Install the included plugin from this marketplace locally:
```
/plugin install slavet-claude@local
```

3) Verify installation:
- Run `/plugin list` and ensure `slavet-claude` appears.
- Update files under `plugins/slavet-claude` and reinstall to test changes.

### Option B — GitHub hosted

1) Push this repository to GitHub (public or org-accessible).

2) Add the marketplace in Claude Code using the repo URL:
```
/plugin marketplace add https://github.com/slavetdigital/slevet-claude-supercharged
```

3) Install the plugin by name:
```
/plugin install slavet-claude
```

4) Verify with `/plugin list`.

## How the marketplace works

- Marketplace configuration lives in `.claude-plugin/marketplace.json`:
```
{
  "name": "Slevet Claude Supercharged",
  "owner": { "name": "Slavēt Digital", "url": "https://www.slavetdigital.com" },
  "plugins": [
    {
      "name": "slavet-claude",
      "description": "Lightweight enterprise guardrails, memory, checkpoints, JSON/diff/flag verification, with auto hooks and minimal MCP.",
      "source": "./plugins/slavet-claude"
    }
  ]
}
```

- For hosted distribution, replace the `source` path with a Git URL to the plugin repository per Claude Code’s plugin spec.

## Developing the `slavet-claude` plugin

The `plugins/slavet-claude` folder is a placeholder. Replace it with your actual plugin implementation. At minimum include:
- `.claude-plugin/plugin.json` — Plugin manifest
- `commands/` — Command handlers
- `hooks/` — Editor/file lifecycle hooks
- `agents/` — Optional agents

Suggested capabilities for robust guardrails and automation:
- Memory & checkpoints to track decisions and ensure consistency
- JSON/diff/flag verification steps in critical flows
- Auto hooks for common repository operations
- Minimal MCP integration for external services when needed

## Recommended workflow

- Start locally: develop in `plugins/slavet-claude`, install via `@local`, iterate quickly.
- Bake in verification: require explicit checks for diffs, flags, and structured outputs.
- Promote to GitHub: when stable, switch the marketplace entry to a Git URL for distribution.
- Version releases: tag semantic versions and maintain a changelog.

## Troubleshooting

- If `/plugin marketplace add ...` fails, verify the path/URL and visibility.
- If `/plugin install ...` fails, ensure a valid `.claude-plugin/plugin.json` exists in the plugin.
- Reinstall or reload the plugin after making changes.

## License

See `LICENSE` for licensing details.
