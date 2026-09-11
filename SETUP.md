# Setup — coach-<user> repo

One checklist to go from fork to first coaching session. Budget ~10 minutes. Coaching normally
happens through the hosted Coach Phelps web + iOS app — this repo is that app's data/backing
store. Claude Code also boots as Coach directly in this repo (BYOB) if you want a terminal
session instead; both paths read/write the same files.

---

## 1. Clone your repo

Fork `sibling-shipyard/coach-skeleton` (or use the private repo your operator created), then:

```bash
git clone https://github.com/YOUR_USERNAME/coach-YOUR_NAME.git
cd coach-YOUR_NAME
```

---

## 2. GitHub secrets

**None required.** The Sync workflow runs under the built-in `GITHUB_TOKEN` (granted
`contents: write`), which GitHub provisions automatically for every Actions run. You do **not**
need to create a `PAT_TOKEN` or any other secret to push sync output.

---

## 3. Install the GitHub App

The Coach Phelps web dashboard and iOS app need the **Coach Phelps GitHub App** installed on
your repo.

1. Your operator sends you the app install link (or open the shared dashboard and sign in).
2. Install the app on **this repo only** (or all repos if you prefer).
3. Grant the permissions it requests (read repo contents, trigger workflows).

---

## 4. Open the Coach Phelps app

Sign in on the web dashboard or the iOS app and connect this repo. Coach detects the empty
`user_data/coach/profile.json` and runs the First Session intake automatically the first time
you open chat.

---

## 5. First sync

Trigger the pipeline once so `gen/` is populated:

1. **GitHub → Actions → Sync → Run workflow**, or
2. Locally: `python3 engine/scripts/regenerate_derived.py`, then run the dashboard snapshot and athlete insights generators.

After sync, `gen/dashboard_snapshot.json` and `gen/athlete_insights.json` reflect your ledger and activity history.

---

## Troubleshooting

- **Sync workflow fails:** open **Actions → Sync** and read the failed run's log. The workflow uses the built-in `GITHUB_TOKEN` (no secret to set); if pushes are rejected, confirm the repo's **Settings → Actions → General → Workflow permissions** is set to **Read and write**.
