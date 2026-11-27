# 0002. The ClusterReport resource is the contract

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

The controller and the agents must exchange work: the controller decides when
a report is due, and the agents produce it. They could talk through an HTTP or
gRPC API, through a message queue, or through a custom resource stored in the
Kubernetes API.

## Decision

The components communicate only through the `ClusterReport` custom resource.
The controller creates it and owns its spec. The agents write their results to
its status, using server-side apply with their own field manager, so each
field has a single owner. There is no direct network API between them.

## Consequences

Every report is visible and auditable with `kubectl`, survives restarts of
either component, and stays pending if the agents fail. Access is governed by
standard RBAC. The trade-off is that objects in the Kubernetes API have a size
limit, so the rendered report itself is stored elsewhere and the status only
records where it is.
