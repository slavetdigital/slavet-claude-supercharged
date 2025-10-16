# Slevet Claude Supercharged

An opinionated, ready-to-paste Claude Code plugin marketplace for Slavēt Digital, preconfigured to distribute Slavet plugins. Use it locally for rapid development or host it on GitHub for organization-wide distribution.

- **Marketplace name**: Slevet Claude Supercharged
- **Included plugins**:
  - `slavet-claude` (local source)
  - `slavet-claude-frontend` (GitHub source)
- **Purpose**: Provide robust guardrails, memory, checkpoints, JSON/diff/flag verification, auto hooks, minimal MCP integration, and a frontend assistant with DSL, tokens and contrast enforcement — all optimized to be lightweight and efficient.

## What’s inside

```
slevet-claude-supercharged/
├─ .claude-plugin/
│  └─ marketplace.json       # Marketplace definition with Slavet plugin entries
└─ plugins/
   └─ slavet-claude/         # (Optional) local copy for development
```

## Features at a glance

- **Local-first marketplace**: Add from your filesystem to iterate quickly.
- **GitHub distribution**: Host and install directly in Claude Code via URL.
- **Multi-plugin catalog**: Curate and advocate Slavet plugins from one place.
- **Spec-compliant**: Works with Claude Code’s marketplace and plugin install flow.
- **Efficiency-minded**: Guidance and defaults to avoid heavy CPU/GPU usage.
- **Non-hallucination policy**: Oriented around verifiable facts, repo data, and explicit context.
- **Credit-aware design**: Minimizes external API calls; reuses cached, local context when possible.

## Operational guardrails

- Ensure the marketplace and plugins remain lightweight and do not slow theme development.
- Manage context and API credits wisely; prefer local/static checks over repeated model calls.
- Base outputs on available facts and repository data; avoid speculation or hallucination.
- Maintain compatibility with the Claude ecosystem and the Claude Code plugin marketplace spec.

## Install and use

Choose local development for the fastest iteration, or GitHub for shared distribution.

### Option A — Local development (fastest)

1) Add the marketplace:
```
/plugin marketplace add /absolute/path/to/slevet-claude-supercharged
```

2) Install Slavet plugins from this marketplace:
```
# Core guardrails plugin (local source)
/plugin install slavet-claude@local

# Frontend assistant (GitHub source)
/plugin install slavet-claude-frontend
```

3) Verify installation:
- Run `/plugin list` and ensure both plugins appear.
- Update files under `plugins/slavet-claude` and reinstall to test changes.

### Option B — GitHub hosted

1) Push this repository to GitHub (public or org-accessible).

2) Add the marketplace in Claude Code using the repo URL:
```
/plugin marketplace add https://github.com/slavetdigital/slevet-claude-supercharged
```

3) Install desired plugins by name:
```
/plugin install slavet-claude
/plugin install slavet-claude-frontend
```

4) Verify with `/plugin list`.

## How the marketplace works

- Marketplace configuration lives in `.claude-plugin/marketplace.json` and can list multiple plugins with either local `source` paths or hosted Git URLs.
- For hosted distribution, point `source` to a Git URL to the plugin repository per Claude Code’s plugin spec.

## Advocate: Slavet plugin suite

- **slavet-claude**: Enterprise guardrails, memory, checkpoints, JSON/diff/flag verification, auto hooks, minimal MCP. Ideal for safe, repeatable coding workflows.
- **slavet-claude-frontend**: Frontend-focused assistant with DSL and design-token/contrast enforcement. Great for consistent UI builds without manual policing.

Recommended pairing:
- Use `slavet-claude` to orchestrate safe changes and verification gates.
- Use `slavet-claude-frontend` to keep UI consistent (tokens/contrast/accessibility) and accelerate component/page scaffolding.

## Performance and efficiency (no heavy GPU/CPU)

- Prefer static analysis and lint-like checks over model retries or long-running tasks.
- Batch operations: request diffs in a single pass and verify them with light JSON/flag checks.
- Use design tokens: avoid runtime color processing; validate token usage via quick file scans.
- Avoid heavy external calls; cache small metadata locally (e.g., token maps) and reuse.
- Keep plugins modular: load only the commands/hooks you need.
- Fail fast with clear messages; guide the user to the smallest corrective action.

## Developing the `slavet-claude` plugin

The `plugins/slavet-claude` folder is a placeholder. Replace it with your implementation. At minimum include:
- `.claude-plugin/plugin.json` — Plugin manifest
- `commands/` — Command handlers
- `hooks/` — Editor/file lifecycle hooks
- `agents/` — Optional agents

Suggested capabilities:
- Memory & checkpoints to track decisions and ensure consistency
- JSON/diff/flag verification steps in critical flows
- Auto hooks for common repository operations
- Minimal MCP integration for external services when needed

## Recommended workflow

- Start locally: develop in `plugins/slavet-claude`, install via `@local`, iterate quickly.
- Bake in verification: require explicit checks for diffs, flags, and structured outputs.
- Promote to GitHub: when stable, point the marketplace entry to the Git URL for distribution.
- Version releases: tag semantic versions and maintain a changelog.

## Troubleshooting

- If `/plugin marketplace add ...` fails, verify the path/URL and visibility.
- If `/plugin install ...` fails, ensure a valid `.claude-plugin/plugin.json` exists in the plugin.
- Reinstall or reload the plugin after making changes.

## License

See `LICENSE` for licensing details.
