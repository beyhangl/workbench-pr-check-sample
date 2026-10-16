# Fictional PR evaluation sample

This public repository demonstrates the reviewed Workbench SDK and GitHub evaluation Action with fictional task data only. No live acceptance run, passing check, or regression check has completed. Source review and offline tests do not establish live acceptance.

## Trusted sample procedure

Only the repository owner creates and opens `sample/pass` and `sample/regression` pull requests into `develop`. Before opening either PR, independently confirm that its workflow bytes match the reviewed workflow and that its target, baseline, scoring controls and execution estimate are approved. A plain `pull_request` event evaluates the PR's workflow definition: the absence of an explicit checkout does not make that definition immutable or safe for untrusted contributors.

The job accepts only an `opened` event, a same-repository head and base, the repository owner as PR author, actor and triggering actor, and the first run attempt. It neither checks out PR files nor downloads PR executables. Synchronization, reopen and manual rerun must not submit another evaluation. Reconcile an uncertain result with the Action's existing read-only reconciliation path outside this workflow; never rerun to replace it.

The fixed mapping is declared before any outcomes:

| Trusted head branch | Connected AgentCore endpoint qualifier |
| --- | --- |
| `sample/pass` | `AQ_BASE_AGENT_ENDPOINT`, the verified healthy/base endpoint |
| `sample/regression` | `AQ_REGRESSION_AGENT_ENDPOINT`, a verified separate regressed endpoint |

An empty selected qualifier refuses execution; it never falls back to the other endpoint. The workflow deploys nothing. The PR head SHA and protected base SHA are declarations, not deployment or serving-model attestation. A source-only PR edit does not by itself change either agent endpoint.

## Private configuration

Use exactly one configured secret, `AQ_SAMPLE_BINDING`, containing the three string fields `AQ_ENDPOINT`, `AQ_UI_URL` and `AQ_API_KEY`. Keep that JSON, its addresses and credential out of this repository, comments and artifacts. The workflow masks each derived component and hostname before exporting step environment. The built-in `github.token` is a separate runtime publisher token; no additional stored GitHub credential is required.

Owner-verified, privacy-safe configuration variables supply `AQ_AGENT`, `AQ_DATASET`, `AQ_BASELINE_EXPERIMENT`, `AQ_BASE_DEPLOYED_COMMIT`, `AQ_BASE_AGENT_ENDPOINT`, `AQ_REGRESSION_AGENT_ENDPOINT`, `AQ_COMMENT_PUBLISHER_ID`, `AQ_CHECK_APP_ID`, `AQ_CHECK_KEY`, `AQ_BUDGET_USD` and `AQ_TIMEOUT_SECONDS`. Publisher and App IDs must describe the actual token's trusted identities, never the PR author. These variables are requirements, not populated sample values.

The connected target must be a permitted non-production AgentCore runtime. Its immutable baseline must belong to that same agent and dataset, match the current PR base commit and effective base endpoint, use development scope with no pinned row IDs and `include_rejected: false`, and contain complete attempts and scorer results. Baseline and candidate retain the same dataset version, scorer settings and repetitions. The Action verifies these records and the current scorer-only readback before submitting one experiment; it does not generate a qualifying baseline or replace it with a fixture. Endpoint selection does not support arbitrary HTTP agents or inline prompt/model overrides.

The evaluation key needs `agents:read`, `datasets:read`, `scorers:read`, `experiments:read` and `experiments:write`. Repository permissions remain `contents: read`, `pull-requests: write` and `checks: write`. This source grants no account or repository permissions.

A positive per-experiment budget and approved call, duration and cost assumptions are required before execution. That budget is not a verified per-key or cumulative billing cap. Current planning has eight planned development task calls, but usable serving-model identity, inference prices and a complete cost estimate are unresolved; there is no paid-run approval or implicit permission to submit.

The Action is pinned to `1f2091e3e58ba7877a8bb017ca87b347fb5daf3c`. `publish-report-links: false` omits the report link and refuses remaining known address disclosure. Only the three allowlisted aggregate files may be uploaded, with seven-day retention. Never publish private debug files, raw case rows, prompts, answers, credentials or customer records.

## Current acceptance status

The source is prepared for independent review only. No compatible immutable baseline or verified healthy/regressed runtime pair is available for this sample, and no live evaluation or publication has run. Before activation, the owner must verify those bindings, independently inspect both trusted PR heads, and approve the concrete paid execution scope. Keep every first outcome and reconcile uncertainty read-only. Do not create resources, deploy, alter shared systems or weaken scoring to obtain a sample result.
