# Review Notes

This file captures known review findings for the current Inspect runner. These
items should be resolved before relying on the runner for repeatable benchmark
results or publishing aggregate scores.

## Inspect Runner Findings

### P1: Reused Langflow Session Can Contaminate Repeat Runs

File: `inspect_runner/au_safety_eval.py`

Lines: `241-243`

The session ID is currently based only on the case ID:

```python
session_id = f"au-eval-{case_id}"
```

Rerunning a case such as `AU-FAIR-001` may reuse the same Langflow session,
depending on how Langflow persists conversation state. If previous turns remain
attached to that session, later evaluations can be contaminated by earlier test
runs and produce non-reproducible results.

Recommended fix: add a run-specific suffix, timestamp, UUID, or explicit
Langflow session reset strategy so every evaluation run starts with a clean
conversation context.

### P2: Inspect Message Trace Omits Chatbot Replies

File: `inspect_runner/au_safety_eval.py`

Lines: `259-262`

The solver stores the full transcript in `state.metadata["conversation_log"]`,
but `state.messages` is only updated with student messages. That means Inspect
traces may not show the complete student/chatbot exchange in the primary message
history, making manual audit and safety review harder.

Recommended fix: include chatbot replies in the Inspect message state using the
appropriate assistant message type, while keeping the structured
`conversation_log` metadata for scorer use.

### P3: Scoring Disabled Still Reports A Perfect Score

File: `inspect_runner/au_safety_eval.py`

Lines: `411-425`

When `score_enabled=false`, the passthrough scorer returns `value=1.0` and
`answer="UNSCORED"`. Because the scorer still uses the `accuracy()` metric,
transcript-only runs may appear as successful passing evaluations in aggregate
outputs.

Recommended fix: separate transcript-only mode from scored evaluation reporting,
or adjust the no-op scorer so unscored runs cannot be mistaken for `PASS`
results.

## Operational Impact

The runner is useful for local experimentation and transcript generation, but
the findings above affect reproducibility, auditability, and score
interpretation. Treat current results as exploratory until these are addressed.
