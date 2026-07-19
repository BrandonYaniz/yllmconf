# Capabilities

Operational commands are represented as structured capabilities instead of arbitrary shell text.

A capability records:

- operation
- executable
- argument array
- placeholders
- source evidence
- confidence
- platform applicability
- administrator approval state

Capability source priority:

1. maintained application profile
2. platform service-manager adapter
3. installed application metadata
4. installed man page or sample documentation
5. LLM-interpreted local documentation
6. administrator-supplied command
