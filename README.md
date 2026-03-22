# Naukleros

Shared types for source events and source identities in
[katastroma](https://github.com/katastroma).

A source event describes what changed (a git push, an S3 object update, an OCI
tag push, a filesystem change). A source identity describes what to track within
a source (a ref and path, a bucket prefix, an OCI repo, a folder). Naukleros
implementations match incoming events against registered identities to determine
whether a pipeline run is needed, then fetch the matched source.

New source types are added as variants in SourceEvent and SourceIdentity.
