# PR evaluation sample

This repository contains a generic reference-agent prompt and one evaluation workflow. It has no customer records, task rows, saved answers, credentials or private service addresses. The existing evaluation dataset contains public weather observations in the product's own test workspace. Those records remain outside this repository. They are not described as fictional observations.

No live sample acceptance has run. Offline review does not establish live acceptance.

## What the two PRs test

The same non-production reference AgentCore runtime and DEFAULT endpoint serve every experiment. No second endpoint, model deployment or cloud resource is needed. Per-run system-prompt overrides use the existing agent contract. The backend refuses a response that does not confirm the exact requested prompt hash.

`prompts/reference-system.txt` contains the public reference-agent instructions plus two explicit rules: use `monthly_summary` for whole-month totals and put the numeric total before any station ID or date. This is a new prompt-override baseline. It is not a claim about the runtime's default prompt or deployed source.

| Branch | Prompt change | Intended check |
| --- | --- | --- |
| `sample/pass` | Add a harmless clarity instruction | No regression, exit 0. A tie produces a neutral owned check. |
| `sample/regression` | Deliberately report zero for monthly precipitation, ignoring the observed total | Regression, exit 1 and a failing owned check, if the retained evidence supports it. |

All eight unchanged references are nonzero. Graders and reference values stay fixed. Merely summing daily rainfall is not intrinsically wrong, so that is not the chosen mutation. Outcomes are measured, never fabricated. No change, rerun or replacement follows an inconclusive result.

## Protected inputs and publication

Only the repository owner opens the two named branches into `develop`. Before either opening, independently verify that its workflow is identical to the reviewed source. A `pull_request` workflow definition comes from the PR. No checkout does not make an untrusted workflow safe.

The job accepts only same-repository owner-created opening events, the owner as actor and triggering actor, and attempt one. It reads only the fixed prompt path from the exact PR base and head commits using GitHub's data API. It verifies the returned blob bytes and stores private data files. It records only validated commit, blob and prompt hashes in the step summary. It never checks out or runs PR project code. Synchronization, reopen and manual rerun cannot submit another experiment.

The Action must support both `system-prompt-file` and `base-system-prompt-file`. It snapshots both inputs before preflight. The persisted baseline prompt must match the base file, and the candidate must retain the head prompt. Both use DEFAULT. Prompt hashes are attribution, not deployment or underlying served-model attestation. No active model override is permitted for this prompt-only comparison.

A genuine baseline must bind to the actual protected sample base commit. Historical runs without that binding cannot be reused or relabelled. Keep the base branch unchanged until both sample checks finish. Never merge the harmless PR between checks.

The baseline and candidates use the same dataset version, eight development rows, one repetition, two deterministic scorers and rejected-row policy. No held-out or customer data is used. For the planned wrong-zero mutation, the current exact comparison requires at least seven paired losses, no paired gains and only ties among the remaining rows to establish regression. A weaker baseline may leave the deliberate regression inconclusive. That is retained, not repaired by tuning or weakening a scorer.

## Private configuration

The only configured secret is `AQ_SAMPLE_BINDING`, with `AQ_ENDPOINT`, `AQ_UI_URL` and `AQ_API_KEY`. Never publish these values. The workflow masks derived values before exporting its step environment. The built-in repository token is separate.

Non-secret variables supply the connected agent, dataset, baseline experiment, actual base commit, trusted comment publisher and check App IDs, check key, budget and timeout. The evaluation key needs `agents:read`, `datasets:read`, `scorers:read`, `experiments:read` and `experiments:write`. All five have already been verified. Repository permissions are limited to contents read, pull requests write and checks write.

The workflow pins the reviewed Action to a full commit SHA. That source must be published before activation. It omits private report links and uploads only its three allowlisted aggregate files for seven days. Raw prompt payloads, task rows, answers and private debug files are not uploaded or included in comments. The generic prompt file above is intentionally public source.

## Execution approval, not yet granted

The prepared scope is eight unchanged rows, one repetition and three experiments: eight baseline requests, eight harmless-PR requests and eight regression-PR requests. Total: **24 target requests**, serially, with **zero model-judge, reflection or title calls** in the reference implementation. Internal tool/model turns and retries may exceed the target-request count.

A retained eight-row Nova Pro experiment reports a token-cost subtotal of $0.039502. Three such batches give $0.118506. The working estimate is **about $0.15 in observed-token cost**, with the current serving model, token growth, runtime compute and hidden usage unresolved. This is not a billing cap. Allow roughly 5–15 minutes including queueing, polling and publication, rather than interpreting the timeout as expected duration.

Before any baseline or sample run, the owner must approve the exact rows, calls, duration, cost assumptions and the two deliberate sample-opening events. Source commits retain `[skip ci]`. The paid-run approval must explicitly cover activation of those public sample events. No workflow is dispatched manually.

The existing CLI can create the baseline after that approval. Run it from the independently verified protected base checkout, using private credentials supplied by the approved mechanism. Keep its output in an owner-only private file named by `AQ_PRIVATE_BASE_REPORT`:

```bash
aq eval run --target "$AQ_AGENT" --dataset "$AQ_DATASET" \
  --dataset-version 2 --row-scope development \
  --scorer "$AQ_NUMBER_SCORER" --scorer "$AQ_CONTAINS_SCORER" \
  --repeats 1 --concurrency 1 --agent-endpoint DEFAULT \
  --commit "$AQ_SAMPLE_BASE_SHA" \
  --system-prompt-file prompts/reference-system.txt \
  --budget 0.50 --timeout 600 --report-file /dev/null --json > "$AQ_PRIVATE_BASE_REPORT"
```

`AQ_SAMPLE_BASE_SHA` must come from this repository's verified base commit. The two scorer IDs and dataset membership are recorded in the private execution preparation. The $0.50 per-experiment metered budget is separate from the $0.15 total planning estimate. It is neither a key-level nor cumulative billing guarantee. Inspect the first retained baseline before opening either sample PR. Stop on uncertain completion, failed override attribution or materially unexpected usage. Reconcile read-only without another submission.

The issue stays open until real comments and owned checks are retained. No qualification, production release or customer acceptance is claimed.
