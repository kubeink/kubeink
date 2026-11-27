# Architecture Decision Records

This directory records the significant architecture decisions of kubeink,
following the format described by Michael Nygard in
[Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions).

A record is immutable once accepted. To change a decision, add a new record
that supersedes the old one and update the status of both.

| ADR | Title | Status |
| --- | --- | --- |
| [0001](0001-go-operator-python-agents.md) | Go operator with a Python multi-agent service | Accepted |
| [0002](0002-clusterreport-contract.md) | The ClusterReport resource is the contract | Accepted |
| [0003](0003-deterministic-data.md) | Deterministic data, the model only interprets | Accepted |
| [0004](0004-reversible-pseudonymisation.md) | Reversible pseudonymisation before any model call | Accepted |
| [0005](0005-orchestrator-and-specialists.md) | An orchestrator with read-only specialist agents | Accepted |
| [0006](0006-ports-and-adapters.md) | Ports and adapters | Accepted |
| [0007](0007-report-storage.md) | Report storage and history | Proposed |
| [0008](0008-cli-as-kubectl-plugin.md) | A Go CLI that is also a kubectl plugin | Accepted |

New records use [template.md](template.md).
