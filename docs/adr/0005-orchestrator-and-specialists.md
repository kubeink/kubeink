# 0005. An orchestrator with read-only specialist agents

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

A single agent with every tool and all the cluster data would need a very
large context, cost more on every call and hold broad permissions. A mistake
or a prompt injection in one area could affect the whole report.

## Decision

An orchestrator plans each report and delegates to specialist agents, one per
area: nodes and capacity, workloads, storage, control plane and certificates,
autoscaling, and OpenShift where it applies. Each specialist can only use the
read-only tools of its area and returns structured findings. A writer drafts
the report and a verifier checks it.

## Consequences

Each agent works with a small context, specialists run in parallel and can use
smaller, cheaper models, and permissions follow least privilege. The cost is
more coordination: the orchestrator must handle partial failures, and the
interaction between agents needs its own evaluations.
