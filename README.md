# yllmconf

`yllmconf` is a local-first, interactive configuration management CLI for creating, modifying, validating, applying, and verifying service configuration changes.

The project is designed for FreeBSD first, with Linux support built into the architecture and macOS support planned as a secondary target. It uses local documentation, installed man pages, package metadata, sample configuration files, imported reference material, and `yllmd` to help administrators understand and safely change service configurations.

## Core principles

- CLI only, no daemon.
- FreeBSD is the primary platform.
- Linux is a first-class supported platform.
- TOML is used for `yllmconf` configuration.
- Configuration changes are interactive and non-destructive.
- Existing files are archived before replacement.
- Files are staged and validated before application.
- Service reloads, restarts, and starts require explicit approval.
- Service state and relevant logs are checked after operational changes.
- Rollback is available and recorded as a new transaction.
- The LLM interprets intent, documentation, configuration, and evidence.
- Deterministic code controls files, commands, privileges, transactions, and approvals.

## Initial service priorities

The architecture is intended to adapt to unfamiliar services when sufficient local documentation and evidence are available. Initial profiles and testing will prioritize:

1. NSD
2. nginx
3. PHP and PHP-FPM
4. FreeBSD `rc.conf`
5. FreeBSD `pf.conf`
6. PostgreSQL
7. MariaDB
8. Postfix
9. Dovecot
10. SpamAssassin

The first complete service workflows should focus on NSD, nginx, and `rc.conf`.

## Planned workflow

```text
inspect
  -> discover local documentation
  -> build a proposed configuration
  -> validate the staged configuration
  -> show the administrator the diff
  -> archive the active configuration
  -> apply the approved change atomically
  -> reload, restart, or start the service
  -> check service state and monitor relevant logs
  -> report success, warnings, uncertainty, or failure
  -> offer rollback when appropriate
```

## Local documentation

`yllmconf` will discover local references such as:

- man pages
- installed package documentation
- package messages and file lists
- sample configuration files
- service scripts
- comments in active configuration files
- administrator-imported reference material

Administrators will be able to import additional documentation into a managed local library. The first release will not search the web or download documentation automatically.

## Safety model

The LLM may propose configuration changes, explain system state, interpret logs, and identify operational capabilities from local documentation. It does not receive unrestricted shell access.

Commands are executed directly with validated argument arrays. The project must never execute model output through `sh -c` or an equivalent shell wrapper.

See [docs/safety-model.md](docs/safety-model.md) for the full design.

## Development status

This repository currently contains the initial project skeleton and planning documents. Implementation work should follow the phases recorded in the private `.codex` directory.

## Build

```sh
go build ./cmd/yllmconf
```

## Test

```sh
go test ./...
```

## Versioning

Versions use date-based identifiers:

```text
YYYY.MM.DD-Beta
YYYY.MM.DD-Release
YYYY.MM.DD.NN-Beta
YYYY.MM.DD.NN-Release
```

Examples:

```text
2026.07.18-Beta
2026.07.18.02-Beta
2026.07.21-Release
```

## License

BSD 3-Clause License.
