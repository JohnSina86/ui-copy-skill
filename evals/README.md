# Evals

Two data files. Neither runs automatically in this repo.

- `evals.json` follows the Anthropic skill-creator schema: `skill_name` and `evals[]`, each with `id`, `prompt`, `expected_output`, `files` and `expectations[]`. Eval 3 carries its markup inline in the prompt. The four evals cover a SaaS hero rewrite, state microcopy for a cafe order flow, a placeholder sweep with no rewrite, and supplied copy that must be preserved with changes proposed separately.
- `trigger-eval.json` is a list of `{query, should_trigger}`. Ten queries should trigger the skill. Ten are **near-miss negatives**: they share words with the skill (write, copy, message, strings, headline) but are a different job, such as an email, a blog post, a README, a translation, an SEO article, a UX audit, a visual restyle, API docs, a cover letter or a requirements document.

## Manual run: functional evals
1. Start a fresh session that has only this skill available.
2. Give it each `prompt` and keep the output. Don't tell it what is expected.
3. Grade every entry in `expectations` as pass or fail against the output. Record a short reason for each failure.
4. For eval 4, the headline must appear unchanged in the delivered strings; a proposal that was applied, or no proposal at all, is a failure.
5. For a baseline, repeat steps 1 to 3 in a session without the skill, and compare.

## Manual run: trigger evals
Take the queries in order. The queries alternate between positives and near-miss negatives, so each part of the split holds both labels. Use the first 12 as the tuning set and the last 8 as a held-out set: look at the held-out results only after you finish editing the description. For each query, note whether the skill loaded. A query is correct when the result equals `should_trigger`. The negatives matter most: the description must not pull this skill into general writing.

## Results recorded so far
The README changelog records each run: date, method, per-eval and per-split results, and what was not measured. The first run (2026-10-13) used subagent contexts rather than top-level sessions, and the trigger queries were sent from an empty project folder; both limits are stated there. The current twenty queries have all been seen during description tuning, so the next round needs new held-out queries before the split is trusted.

## Automated run (not run in this repository's release process)
Anthropic's skill-creator ships `run_eval.py` and `run_loop.py`, which run trigger queries through the `claude` CLI and split the queries themselves. They need `claude -p`. Pass them `trigger-eval.json` as the query set. The v1.0.0 release was prepared without that CLI in the release process, so the trigger set was reviewed by hand and **not** run through the automated tester.
