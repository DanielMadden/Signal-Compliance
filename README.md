# Signal Compliance

A GitHub Actions cron job that emits one plausibly meaningful commit per day to satisfy a visible productivity signal.

This project is a small joke with citations. [Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law) warns that measures degrade when they become control targets. [Campbell's Law](https://jmde.com/index.php/jmde_1/article/view/297) describes how high-stakes quantitative indicators become corrupted and distort the processes they claim to monitor. Marilyn Strathern's formulation says it plainly: ["When a measure becomes a target, it ceases to be a good measure."](https://www.nature.com/nature-index/news/measure-for-measure)

## How It Works

A scheduled workflow runs daily at 16:00 UTC, appends a Mountain Time timestamped entry to `heartbeat.txt`, and commits it with an intentionally ambiguous operational message. The file is trimmed to a rolling 365-day window. The commit is skipped if today already has an entry (idempotent).

## Trigger

- **Scheduled**: daily at 16:00 UTC
- **Manual**: via `workflow_dispatch` in the GitHub Actions UI

## Files

- `.github/workflows/daily-green.yml` — the entire project
- `heartbeat.txt` — rolling log of daily commits
