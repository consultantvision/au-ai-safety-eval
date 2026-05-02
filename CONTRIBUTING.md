# Contributing

Thank you for helping improve `au-ai-safety-eval`. The goal is to build a
practical, community-maintained dataset for evaluating AI chatbots in Australian
contexts that are often invisible to global benchmarks.

You do not need to be technical to contribute. A strong contribution can be a
plain-English scenario, a correction to cultural or legal framing, or feedback
on whether an existing test case feels realistic.

## Ways to Contribute

- Propose a new test case through a GitHub Issue.
- Submit a Pull Request that adds or updates rows in `dataset/`.
- Review existing cases for accuracy, respectfulness, and usefulness.
- Suggest Australian legal, policy, service, or community anchors.
- Identify gaps in representation, especially for First Nations, CALD,
  disability, regional, mature-age, and other lived-experience contexts.

## Adding a Test Case

1. Read `DATASET_SCHEMA.md`.
2. Draft the case in plain English.
3. Include a clear Australian anchor.
4. Open an issue using the `new-test-case` template, or submit a Pull Request
   that updates both `dataset/seed_v0.1.jsonl` and `dataset/seed_v0.1.csv`.

Each test case should describe a scenario and intent, not a fixed prompt. The
evaluator should have enough context to role-play the user and probe the target
chatbot across turns.

## Review Expectations

Maintainers and reviewers should check:

- Australian relevance and grounding.
- Respectful representation of the people or communities in scope.
- Clear expected behaviour and failure indicators.
- Avoidance of stereotypes, private information, or claims that cannot be
  checked.
- Alignment between JSONL and CSV versions of the dataset.

For First Nations, CALD, disability, mental health, legal, or other specialised
contexts, lived-experience and domain-informed review is strongly preferred.

## Pull Request Checklist

- [ ] I have read `DATASET_SCHEMA.md`.
- [ ] I updated the JSONL dataset if adding or changing a case.
- [ ] I updated the CSV mirror if adding or changing a case.
- [ ] The case is scenario based, not a fixed prompt.
- [ ] The Australian anchor is specific and credible.
- [ ] The expected behaviour and failure indicators are assessable.
- [ ] I have avoided private, confidential, or identifying information.

## Tone and Community Standards

Contributions should be constructive, respectful, and grounded in the purpose of
making chatbot failures visible and testable. Direct critique is welcome;
personal attacks or dismissive treatment of communities represented in the
dataset are not.

## Reporting Problems

If a case is inaccurate, culturally unsafe, legally outdated, or poorly framed,
open an issue using the `dataset-feedback` template. Please include the case ID,
the concern, and any suggested correction or source that would help reviewers.
