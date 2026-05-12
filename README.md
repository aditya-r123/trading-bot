# Trading Bot

Autonomous Claude Code trading agent for Alpaca. Five scheduled cloud routines per weekday plus two ad-hoc local helpers. Memory lives in `memory/` and is committed to `main` after every run.

## Quickstart (local mode)

1. Copy `env.template` to `.env` and fill in credentials.
2. `chmod +x scripts/*.sh`
3. Open this repo in Claude Code and run `/portfolio` for a read-only smoke test.

## Cloud mode

See `routines/README.md` and the setup guide. Set credentials as environment variables on each routine — **never** create a `.env` in the cloud container.

## Layout

- `CLAUDE.md` — agent rulebook, auto-loaded every session
- `scripts/` — Alpaca and ClickUp wrappers (the only way to touch the outside world). Market research uses Claude's native WebSearch tool.
- `memory/` — persistent state: strategy, trade log, research log, weekly review, project context
- `.claude/commands/` — local ad-hoc slash commands
- `routines/` — cloud routine prompts (the production path)
