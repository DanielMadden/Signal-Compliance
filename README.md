# Signal Compliance

A GitHub Actions cron job that emits one plausibly meaningful commit per day to satisfy a visible productivity signal.

This project is a small joke with citations. <a href="https://en.wikipedia.org/wiki/Goodhart%27s_law" target="_blank" rel="noopener noreferrer">Goodhart's Law</a> warns that measures degrade when they become control targets. <a href="https://en.wikipedia.org/wiki/Campbell%27s_law" target="_blank" rel="noopener noreferrer">Campbell's Law</a> describes how high-stakes quantitative indicators become corrupted and distort the processes they claim to monitor. <a href="https://en.wikipedia.org/wiki/Goodhart%27s_law#Generalization" target="_blank" rel="noopener noreferrer">Marilyn Strathern's formulation</a> says it plainly: "When a measure becomes a target, it ceases to be a good measure."

## How It Works

A scheduled workflow runs daily at 16:00 UTC, appends a Mountain Time timestamped entry to `heartbeat.txt`, and commits it with an intentionally ambiguous operational message. The file is trimmed to a rolling 365-day window. The commit is skipped if today already has an entry (idempotent).

## Trigger

- **Scheduled**: daily at 16:00 UTC
- **Manual**: via `workflow_dispatch` in the GitHub Actions UI

## Files

- `.github/workflows/daily-green.yml` — the entire project
- `heartbeat.txt` — rolling log of daily commits

## Sources

- <a href="https://en.wikipedia.org/wiki/Goodhart%27s_law" target="_blank" rel="noopener noreferrer">Wikipedia, "Goodhart's law"</a>
- <a href="https://en.wikipedia.org/wiki/Campbell%27s_law" target="_blank" rel="noopener noreferrer">Wikipedia, "Campbell's law"</a>
- <a href="https://en.wikipedia.org/wiki/Goodhart%27s_law#Generalization" target="_blank" rel="noopener noreferrer">Wikipedia, "Goodhart's law" generalization section</a>
- <a href="https://jmde.com/index.php/jmde_1/article/view/297" target="_blank" rel="noopener noreferrer">Donald T. Campbell, "Assessing the Impact of Planned Social Change"</a>
- <a href="https://www.nature.com/nature-index/news/measure-for-measure" target="_blank" rel="noopener noreferrer">Nature Index, "Measure for measure"</a>
