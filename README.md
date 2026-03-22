# Naukleros

Retriever interface for [katastroma](https://github.com/katastroma). Defines the
service contract for matching source events against registered identities and
fetching source content.

## Operations

- **Match** — given a source event, find the matching source identity. Returns
  the identity if matched, empty if not.
- **Fetch** — given a source identity, retrieve the source content.
