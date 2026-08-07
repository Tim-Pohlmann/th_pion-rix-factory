# th_pion-rix-factory

Runs a `rix` job (an autonomous software factory job) against a Tim-Pohlmann repo and opens
pull requests for its changes. Trigger it from the repo's **Actions** tab → **rix** →
*Run workflow*.

## Inputs

| Input | Required | Description |
| --- | --- | --- |
| `prompt` | Exactly one of `prompt` / `prompt-file` | The task for the agent, inline. GitHub caps a `workflow_dispatch` run's combined input payload at 65,535 characters, so use `prompt-file` instead for larger tasks. |
| `prompt-file` | Exactly one of `prompt` / `prompt-file` | Path inside the target repo's default branch to a file whose contents become the task prompt. Read at run time, so it is not limited by the dispatch input payload cap. |
| `repo` | No | Target repo name; the owner is always `Tim-Pohlmann`. Defaults to this repo. |

## Secrets

| Secret | Purpose |
| --- | --- |
| `RIX_READ_TOKEN` | Read access to the target repo (used to clone it and to read `prompt-file`). |
| `RIX_WRITE_TOKEN` | `contents:write` + `pull-requests:write` on the target repo (used to push branches and open PRs). |
