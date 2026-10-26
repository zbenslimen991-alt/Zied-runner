# Zied-runner

This repository owns orchestration only; the application code is checked out from the private `Zied` repository using `APP_REPO` and `APP_REPO_TOKEN`.

## Required cycle behavior
- Run one full scanner/learning cycle at a time.
- After a successful cycle completes, dispatch the next cycle immediately instead of waiting for the next cron tick.
- Keep a 30-minute schedule as a recovery trigger, with concurrency protection to avoid overlapping portfolio-state writes.
- On failure, log the failure and do not create an uncontrolled restart loop.
- Telegram reporting belongs to the application cycle and should report each completed cycle.

The workflow is intentionally not active in this rebuild commit. It should be enabled only after the fresh-state and external-position handling are validated.
