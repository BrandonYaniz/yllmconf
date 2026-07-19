# Architecture

`yllmconf` is a CLI application organized around an evidence-driven configuration transaction.

## High-level flow

```text
administrator
  -> yllmconf CLI
  -> platform and service discovery
  -> local documentation retrieval
  -> yllmd configuration reasoning
  -> staged proposal
  -> deterministic validation
  -> administrator approval
  -> archived transaction
  -> atomic application
  -> service lifecycle action
  -> bounded service and log verification
  -> result or rollback
```

## Core separation

The LLM interprets intent, documentation, configuration, and evidence. Deterministic code controls files, commands, privileges, transactions, and approvals.

## Platform order

1. FreeBSD rc.d and traditional log files
2. Linux systemd and journald
3. Other Linux service managers
4. macOS launchd
