# Transactions

Each applied or rolled-back configuration change is stored as an immutable transaction.

Recommended path:

```text
/var/db/yllmconf/changes/YYYYMMDD-HHMMSSZ/
```

Recommended contents:

```text
manifest.toml
original
proposed
applied
diff.patch
validation.json
service-action.json
service-status.json
logs/
explanation.md
```

Before replacement, the active file hash must be rechecked to prevent overwriting a concurrent administrator or package change.
