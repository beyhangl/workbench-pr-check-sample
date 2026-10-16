# PR evaluation sample

This repository contains a generic reference-agent prompt and one evaluation workflow. It contains no customer records, task rows, saved answers, credentials or private service addresses. The evaluation data are public weather observations in the product's own test workspace. They are not fictional observations.

## Completed 24-row diagnostic

The separately approved second round completed on 16 October 2026. A fresh protected-base control and both unchanged prompt variants each used 24 confirmed development rows from the same dataset version, one repetition, two unchanged deterministic scorers and the DEFAULT endpoint. All 72 target requests completed serially, with no reported target errors or timeouts. All 72 responses acknowledged their expected prompt digest.

Execution used sample base `917f8e6ccd89758ad26c197251893caabf3708e2` and Action `61150d4dfa291f394eb9323dd1e92d86d6ce9ea2`. The later README update is not the executed base. Existing prompt heads were reused in new PR IDs. The original PR3/4 and their results were preserved unmerged, not rerun or relabelled.

| Position | Leading-total passes | Contains passes | Reported token cost | Owned check |
| --- | --- | --- | --- | --- |
| Protected baseline | 0/24 | 24/24 | $0.008480 | Protected control |
| [Harmless change](https://github.com/beyhangl/workbench-pr-check-sample/pull/6) | 0/24 | 24/24 | $0.008365 | [Neutral](https://github.com/beyhangl/workbench-pr-check-sample/runs/117163400924) |
| [Wrong-total change](https://github.com/beyhangl/workbench-pr-check-sample/pull/7) | 0/24 | 16/24 | $0.008760 | [Failure](https://github.com/beyhangl/workbench-pr-check-sample/runs/117164740582) |

Real comments: [harmless](https://github.com/beyhangl/workbench-pr-check-sample/pull/6#issuecomment-6223396205) and [wrong-total](https://github.com/beyhangl/workbench-pr-check-sample/pull/7#issuecomment-6223448080). The harmless workflow exited 0 with 24 paired ties on each scorer. The wrong-total workflow exited 1 because contains had 8 paired losses, 0 gains and 16 ties. Its upper one-sided confidence bound was about -0.01383. The leading-total scorer had 24 ties at zero passes, so it provided no regression evidence. These task-quality limitations are retained without changing graders or references.

Reported token cost for this round was **$0.025605**. The conservative maximum-observed subtotal was $0.025605316 because progress and terminal totals differ slightly. Including the earlier 24-request round, reported token cost was $0.034618. No model-judge, title or reflection stage, replacement request or automatic rerun was submitted. Hidden turns/retries, runtime charges and actual billing remain unknown. The $0.50 per-experiment meter and $1 observed-cost stop are not guaranteed complete-billing caps.

This demonstrates real comment/check publication, a harmless neutral path and a scored regression failure. It does not establish qualification, release acceptance, a generally strong baseline or independently attested deployment/model identity. No dataset, threshold, prompt or scorer was edited for this round. A separate product follow-up covers development must-pass checks without signed release evidence.

The workflow and protected private binding remain unchanged. Future execution requires its own approved scope, a genuine matching baseline and fresh supported PR-opening events. Do not reopen or rerun these PRs to obtain different results.

<details>
<summary>Original eight-row round and setup instructions, retained as historical evidence</summary>

The following section describes the earlier batch and its then-current acceptance status. Its eight-row bindings and open-delivery wording are historical. The completed 24-row round above supersedes that status. Neither historical batch is relabelled.


This repository contains a generic reference-agent prompt and one evaluation workflow. It has no customer records, task rows, saved answers, credentials or private service addresses. The existing evaluation dataset contains public weather observations in the product's own test workspace. Those records remain outside this repository. They are not described as fictional observations.

The approved 24-request sample completed on 16 October 2026. Both PRs published
comments and neutral evaluation checks. A clear regression producing a failing
check was **not** demonstrated. The retained results below are development
evidence, not qualification or customer acceptance.

## Retained results

The protected base was `c6ccd335bc4912c74512215f409eb11f8af72303`.
The workflow used Action `61150d4dfa291f394eb9323dd1e92d86d6ce9ea2`,
integrated into SDK develop as `6f403c2d3c79a011773475dd2df74be07bd95867`.
All three experiments used the same eight development rows, dataset version,
deterministic graders and DEFAULT endpoint. They each completed eight target
requests with zero reported target errors or timeouts.

| Position | Numeric / contains passes | Reported token cost | Latency p50 / p95 |
| --- | --- | --- | --- |
| Protected baseline | 4/8 / 6/8 | $0.002950 | 5.221 s / 5.507 s |
| [Harmless PR](https://github.com/beyhangl/workbench-pr-check-sample/pull/3) | 8/8 / 8/8 | $0.002947 | 5.368 s / 5.635 s |
| [Wrong-total PR](https://github.com/beyhangl/workbench-pr-check-sample/pull/4) | 4/8 / 6/8 | $0.003116 | 5.272 s / 5.403 s |

The harmless PR published its [comment](https://github.com/beyhangl/workbench-pr-check-sample/pull/3#issuecomment-6220398537)
and [neutral check](https://github.com/beyhangl/workbench-pr-check-sample/runs/117088860074).
It improved four numeric pairs and two contains pairs, with no paired losses.
The wrong-total PR published its [comment](https://github.com/beyhangl/workbench-pr-check-sample/pull/4#issuecomment-6220433345)
and [neutral check](https://github.com/beyhangl/workbench-pr-check-sample/runs/117089706643).
It had two gains and two losses on the numeric grader, and one gain and one loss
on contains. The intended regression instruction did not establish clear
degradation. Override acknowledgement proves the supplied prompt hash, not
semantic obedience to every instruction.

Both workflow jobs succeeded. Both evaluation verdicts remained
`no_clear_difference`, with exit 0 and neutral owned checks. Neither job success
nor a neutral result is a statistical improvement or a quality-regression failure.
The baseline's existing failures prevent the wrong-zero mutation from reaching
the current eight-row regression bound. No scorer, reference, threshold or
baseline was changed to force a different result.

The reported token-cost subtotal was **$0.009013** across 24 target requests.
The conservative maximum-observed accounting ledger was $0.009013022 because
progress values and rounded terminal totals differ slightly. All responses
reported the expected override digest. The runtime reported Nova Lite usage,
but underlying serving identity and complete internal attempts were not
independently attested. Runtime charges, hidden usage and actual billing remain
unknown. No model-judge, title or reflection call was submitted.

This batch is finished. It used exactly the two approved commits without
`[skip ci]`. There were no replacement requests or manual workflow reruns.
Do not reopen, synchronize or rerun these PRs to obtain a preferred outcome.

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

## Approved scope and reproducible invocation

The owner approved and completed scope was eight unchanged rows, one repetition
and three experiments: eight baseline requests, eight harmless-PR requests and
eight regression-PR requests. Total: **24 target requests**, serially, with
**zero model-judge, reflection or title calls** in the reference implementation.
Internal tool/model turns and retries may exceed the target-request count.

A retained eight-row Nova Pro experiment reports a token-cost subtotal of $0.039502. Three such batches give $0.118506. The working estimate is **about $0.15 in observed-token cost**, with the current serving model, token growth, runtime compute and hidden usage unresolved. This is not a billing cap. Allow roughly 5–15 minutes including queueing, polling and publication, rather than interpreting the timeout as expected duration.

That approval covered only this batch and its two deliberate sample-opening
events. Source and documentation commits retain `[skip ci]`. No workflow was
dispatched manually. Stop rules required no retries after repeated errors and
no further execution once observed cost exceeded $1. Observation was
conservative at the first visible execution error. It was not an atomic billing
cap and could not prevent an already in-flight request from completing.

The following is the retained baseline invocation, not permission to submit it
again. It ran from the independently verified protected base checkout with
private credentials. Output stays in an owner-only private file named by
`AQ_PRIVATE_BASE_REPORT`:

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

Real comments and owned neutral checks are retained. The delivery issue remains
open because the required clear-regression/failing-check demonstration is still
missing. No additional run, weaker decision rule, qualification, production
release or customer acceptance is implied by this documentation.

</details>
