# 0004. Reversible pseudonymisation before any model call

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

Cluster data is confidential. Node names, namespaces, registries and error
messages reveal how a platform is built, and many organisations cannot send
them to an external model provider, even under a contract.

## Decision

Before any model call, kubeink replaces every identifier with a stable alias,
such as `NODE_07` or `NS_12`. Free text, such as event messages and logs, is
scrubbed with configurable rules. The mapping between real values and aliases
never leaves the cluster. A pre-flight check cancels any request that still
contains a real value from the mapping. The real names are restored only when
the report is rendered.

## Consequences

Organisations that handle sensitive data can use kubeink with an external
provider. The model loses the hints that real names carry, such as a namespace
called `payments`, so profiles can mark names that are safe to send. The
pseudonymisation layer becomes security-critical code and needs its own tests.
