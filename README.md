# Naukleros

Retriever interface for GitOps on Kubernetes. Defines the gRPC service contract
for determining fetch relevance and fetching source content from a repository.

The contract defines two operations:

- **Relevance check** — given a webhook event (repo URL, ref, before/after
  commits) and a tenant's tracking config (revision, path), determine if the
  pipeline should run
- **Fetch** — given a repo URL, revision, path, and credentials, retrieve the
  source content

Implementations are responsible for authentication, transport, and
provider-specific logic (git clone, commit diffing, OCI pull, etc.).

## Why It Exists

Fetching is one of three fundamental GitOps operations (fetch, render,
provision). Naukleros extracts the fetching contract so that:

- Retriever implementations are independently testable and deployable
- The orchestrator ([pharos](https://github.com/katastroma/pharos)) can call
  any retriever that satisfies the contract
- The ecosystem can converge on a shared contract instead of each project
  coupling source fetching into a monolith

## Ecosystem

Naukleros is one of three GitOps service interfaces defined by
[katastroma](https://github.com/katastroma):

- **naukleros** (this) — retriever interface
- [keleustēs](https://github.com/katastroma/keleustes) — renderer interface
- [katartismos](https://github.com/katastroma/katartismos) — provisioner
  interface

[Phortizo](https://github.com/katastroma/phortizo) is katastroma's retriever
implementation.
