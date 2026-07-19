# Safety Model

`yllmconf` must remain interactive, reviewable, and reversible.

## Deterministic controls

The following must not depend on model judgment:

- path authorization
- symlink handling
- file hashing
- metadata preservation
- archive creation
- staged writes
- atomic replacement
- concurrent-change detection
- command execution
- timeout enforcement
- log offsets and journal cursors
- rollback mechanics
- transaction recording
- approval requirements

## Command execution

The model may propose an operational capability based on local evidence. Before execution, deterministic code must verify the executable, arguments, placeholders, path boundaries, and administrator approval.

Model output must never be executed through `sh -c`, shell pipelines, redirects, substitutions, or compound commands.

## Rollback

Rollback is interactive by default and is recorded as a new transaction. Automatic rollback is outside the initial release scope.
