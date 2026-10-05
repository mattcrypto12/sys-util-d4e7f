# sys-util-d4e7

Internal utility scripts.

## Workflows

- `daily-refresh.yml` — the nightly deal-data refresh (06:00 UTC), run as
  three chained ~90-minute jobs that share a Redis offset so a long cycle
  resumes across jobs and across days.
- `_refresh-part.yml` — the reusable job each part calls.
- `keepalive.yml` — weekly; pushes an empty commit once the repo has been
  quiet for 40 days. GitHub disables scheduled workflows after 60 days
  without commits, which is how the nightly silently stopped on 2026-08-31.

If a scheduled workflow ever shows as disabled again, add a workflow file
under a new name (new paths are enabled by default) or re-enable it from the
Actions tab.
