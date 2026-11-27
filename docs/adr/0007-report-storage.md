# 0007. Report storage and history

- **Status:** Proposed
- **Date:** 2026-11-27

## Context

A rendered report does not fit in the status of a `ClusterReport`, because
objects in the Kubernetes API have a size limit (ADR 0002). Reports must also
be kept over time, so that each one can be compared with the previous period.

## Decision

Not decided yet. The options are:

- A PersistentVolumeClaim mounted by the agents service. It needs no external
  services, but ties the history to one cluster and one volume.
- S3-compatible object storage. It survives the cluster, works with any
  provider that implements the API, and adds a dependency and its credentials.

Storage is a port (ADR 0006), so both can be offered as adapters. This record
will be accepted once the default adapter is chosen.

## Consequences

To be completed when the decision is accepted.
