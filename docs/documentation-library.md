# Documentation Library

`yllmconf` uses local documentation as evidence for configuration reasoning.

## Automatic sources

- man pages
- package documentation
- package messages and file lists
- sample configuration files
- service scripts
- active configuration comments

## User imports

Administrators can import additional reference material into a managed local library.

Planned command:

```sh
yllmconf docs add <application> <file>
```

Imported documents retain their original file, hash, metadata, normalized text, and source classification. Imported content is treated as untrusted reference material and cannot override system policy.
