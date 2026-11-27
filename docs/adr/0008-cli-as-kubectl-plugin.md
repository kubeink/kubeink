# 0008. A Go CLI that is also a kubectl plugin

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

Users need to start reports, follow their progress and approve them without
writing YAML by hand. Most of them already work with `kubectl`, and tools such
as Argo CD and Kargo ship their own command-line interface.

## Decision

kubeink ships a CLI written in Go, the same language as the controller, so it
reuses the API types directly. The binary is also distributed as
`kubectl-ink`, so it can be run as `kubectl ink`, and it will be published in
the Krew index.

## Consequences

Users get a familiar workflow and the CLI stays in sync with the API, because
both use the same types. The cost is another binary to build, sign and release
for several platforms.
