# coach-skeleton

Private fork template for `coach-<user>` repos. Carved from `coach-phelps-hq`. This repo is a
data/backing store for the hosted Coach Phelps web + iOS app — Coach Phelps's persona and
coaching logic live once in HQ (`coach-phelps-hq`), not duplicated here; there is no local/BYO
coaching mode.

## What's in this repo

| Band | Paths |
|---|---|
| **init** | `user_data/coach/*`, `user_data/activities/hist/` |
| **post-init** | `user_data/ledger/*`, `user_data/activities/workout_plans/sessions/` |
| **gen** | `gen/aggregate.json`, `gen/quest_log.md`, `gen/sync_status.json`, `gen/widget_snapshots.json` |
| **engine** | Runtime scripts, core, and shared naming/query logic — carved from HQ; coach must not edit |

Dashboard: shared site reads `gen/aggregate.json`. iOS app pushes `user_data/activities/hist/` directly.

Pin: `.coach-engine-version` · Operator: `coach-phelps-hq/platform/scripts/carve-skeleton.mjs`
