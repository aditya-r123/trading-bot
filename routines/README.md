# Cloud Routines

These are the production prompts. Each one is pasted **verbatim** into a Claude Code cloud routine. Do not paraphrase — the env-var check block and the commit-and-push step are load-bearing.

## Schedules (America/Chicago)

| File | Cron | When |
|------|------|------|
| `pre-market.md`    | `0 6 * * 1-5`  | 6:00 AM weekdays |
| `market-open.md`   | `30 8 * * 1-5` | 8:30 AM weekdays (market open CT) |
| `midday.md`        | `0 12 * * 1-5` | noon weekdays |
| `daily-summary.md` | `0 15 * * 1-5` | 3:00 PM weekdays (market close CT) |
| `weekly-review.md` | `0 16 * * 5`   | 4:00 PM Fridays only |

## One-time prerequisites

1. Install the Claude GitHub App on this repo (least-privilege, repo-only).
2. Toggle **Allow unrestricted branch pushes** ON in each routine's environment.
3. Add credentials as **environment variables on the routine**, not as a `.env` file:
   - `ALPACA_API_KEY`, `ALPACA_SECRET_KEY` (required)
   - `ALPACA_ENDPOINT`, `ALPACA_DATA_ENDPOINT` (optional)
   - `CLICKUP_API_KEY`, `CLICKUP_WORKSPACE_ID`, `CLICKUP_CHANNEL_ID` (required for notifications)

Market research uses Claude's native WebSearch tool — no extra API key needed.

**NEVER create a `.env` file in a cloud routine.** The wrappers read directly from process env.
