# Slevet Claude Supercharged

This is a minimal, ready-to-paste **Claude Code plugin marketplace** for **Slavēt Digital**.

## Structure
```
slevet-claude-supercharged/
├─ .claude-plugin/
│  └─ marketplace.json       # Marketplace definition
└─ plugins/
   └─ slavet-claude/         # (Optional) Local copy of the plugin
```

## How to use

### Option A: Local development (no Git hosting yet)
1. Put your plugin folder at `plugins/slavet-claude/` (or adjust `source`).
2. In Claude Code, add this marketplace and install the plugin:
   ```
   /plugin marketplace add /absolute/path/to/slevet-claude-supercharged
   /plugin install slavet-claude@local
   ```

### Option B: Hosted on GitHub
1. Publish your plugin (e.g., `https://github.com/SlavetDigital/slavet-claude`).
2. Change the `source` for `slavet-claude` in `.claude-plugin/marketplace.json` to the Git URL.
3. In Claude Code, add and install:
   ```
   /plugin marketplace add https://github.com/SlavetDigital/slevet-claude-supercharged
   /plugin install slavet-claude
   ```

## Notes
- You can list multiple plugins in `.claude-plugin/marketplace.json`.
- Keep plugins lightweight and spec-compliant: `.claude-plugin/plugin.json`, `commands/`, `hooks/`, `agents/`.
- For org-wide distribution, consider version pinning and semantic releases.
