# Trigger Policy

Use this reference when deciding whether a commit or push is allowed.

## Explicit Triggers

Treat these as explicit triggers:

- `commit to github`
- `push to github`
- `publish this branch`
- `run Mycodex`
- `run Mycodex github commit agent`
- `use github-triggered-commit`
- `commit these changes`

Ambiguous phrases such as `looks good`, `done`, `ship it`, or `save it` are not enough by themselves. Ask one concise confirmation question if the user intent is unclear.

## Safety Gates

Do not commit or push if:

- The diff contains secrets, credentials, API keys, tokens, private connection strings, or local-only environment values.
- The staged set would include unrelated user changes.
- Required tests or validations fail and the user has not explicitly approved committing anyway.
- The target remote is unclear.
- The requested operation requires history rewrite or destructive cleanup that was not explicitly requested.

## Repository Remote Defaults

For this repository:

- `origin` is the working fork and normal push target.
- `upstream` is the source project and should not receive direct pushes unless explicitly requested.
