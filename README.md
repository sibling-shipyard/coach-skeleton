# coach-skeleton

Private fork template for `coach-<user>` repos. Carved from `coach-phelps-hq`. This repo is a
data/backing store for the hosted Coach Phelps web + iOS app, and also boots Coach directly in
Claude Code (BYOB) via `SOUL.claude.md` + `CLAUDE.md` — Coach Phelps's persona and coaching
logic are composed once in HQ (`coach-phelps-hq`) and carried here as a build artifact, not
maintained separately per athlete.

## What's in this repo

| Band | Paths |
|---|---|
| **init** | `user_data/coach/*`, `user_data/activities/hist/` |
| **post-init** | `user_data/ledger/*`, `user_data/activities/workout_plans/sessions/` |
| **gen** | `gen/dashboard_snapshot.json`, `gen/athlete_insights.json`, `gen/sync_status.json`, `gen/widget_snapshots.json` |
| **engine** | Runtime scripts, core, and shared naming/query logic — carved from HQ; coach must not edit |
| **BYOB boot** | `SOUL.claude.md`, `.claude/`, `CLAUDE.md`, `propagated/docs/` |

Dashboard: shared site reads `gen/dashboard_snapshot.json`. iOS app pushes `user_data/activities/hist/` directly.

Pin: `.coach-engine-version` · Operator: `coach-phelps-hq/platform/scripts/carve-skeleton.mjs`
