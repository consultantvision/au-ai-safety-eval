# Dataset Schema

This document describes the fields used by the `au-ai-safety-eval` dataset.
Each row is an evaluation scenario, not a fixed prompt. Evaluators should use
the scenario, persona, and guidance to conduct a realistic multi-turn probe of a
target chatbot.

## Files

- `dataset/seed_v0.1.jsonl` is the canonical machine-readable dataset.
- `dataset/seed_v0.1.csv` mirrors the JSONL file for spreadsheet review and
  non-technical contribution workflows.

## Field Reference

| Field | Required | Description |
|---|---:|---|
| `id` | Yes | Stable test case identifier. Format: `AU-<DIMENSION>-<NUMBER>`, for example `AU-FAIR-001`. |
| `dimension` | Yes | Top-level evaluation category. Current values: `fairness`, `cultural_appropriateness`, `ethical`. Planned values include `diverse_cultural_backgrounds` and `red_teaming`. |
| `subdimension` | Yes | Specific focus area within the dimension, using lowercase snake case. |
| `scenario` | Yes | Plain-English situation the evaluator should simulate. This should describe context and user need without prescribing an exact prompt. |
| `persona` | Yes | User persona the evaluator should role-play, including relevant communication style, background, vulnerability, or intent. Avoid stereotypes and unnecessary demographic detail. |
| `intent` | Yes | What the test is designed to reveal about the target chatbot's behaviour. |
| `evaluator_guidance` | Yes | Instructions for how the evaluator should conduct the probe across turns, including follow-up strategies. |
| `expected_behaviour` | Yes | What a strong response should do. This should be observable and assessable. |
| `failure_indicators` | Yes | Concrete behaviours that should count against the chatbot. |
| `au_anchor` | Yes | Australian legal, ethical, policy, cultural, institutional, or social anchor for the test. |
| `severity` | Yes | Risk level if the chatbot fails the test. Current values: `low`, `medium`, `high`. |
| `turn_depth` | Yes | Recommended maximum number of evaluator turns. Use higher depth for scenarios where escalation or follow-up matters. |
| `contributor` | Yes | Contributor handle, organisation, or `core-team`. |
| `notes` | No | Additional context for reviewers and maintainers. |

## Design Principles

Test cases should be:

- Australian-context specific, not generic chatbot safety prompts.
- Scenario based, not fixed one-shot prompts.
- Grounded in a clear Australian anchor such as law, policy, protocol, service
  expectations, or lived community context.
- Written in plain English so non-technical contributors can review them.
- Specific enough to judge, but flexible enough that evaluators can probe across
  multiple turns.

## Severity Guidance

Use `high` when failure could cause serious harm, exclusion, rights impacts, or
loss of access to essential support. Examples include disability access,
distress escalation, First Nations cultural protocol failures, and procedural
gatekeeping in high-stakes academic contexts.

Use `medium` when failure may cause material confusion, unfairness, privacy
risk, or exclusion, but the likely harm is less immediate.

Use `low` for lower-impact usability, tone, or localisation problems. Low
severity cases should still have a clear Australian-context reason for existing.

## Review Checklist

Before adding or approving a case, check that:

- The case is recognisably Australian in context.
- The scenario is realistic and respectful.
- The expected behaviour and failure indicators are assessable.
- The Australian anchor is credible and specific.
- The case does not expose private information or rely on unverifiable claims.
- The case avoids deficit framing of communities represented in the dataset.
