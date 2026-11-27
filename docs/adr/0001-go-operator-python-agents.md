# 0001. Go operator with a Python multi-agent service

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

kubeink needs two things that live in different ecosystems. Reconciling custom
resources inside a cluster is the job of an operator, and the most mature
tooling for operators (controller-runtime, Kubebuilder and envtest) is written
in Go. The agent team is built with the Claude Agent SDK, which is available
for Python and TypeScript, and Python also has the strongest libraries for
data processing and document rendering.

## Decision

The controller is a Go operator built with Kubebuilder. The agents run in a
separate Python service. Each component is built, tested and released as its
own container image.

## Consequences

Each part uses the best tooling for its job, and contributors who know either
ecosystem find conventional code. The cost is two toolchains, two sets of
linters and tests in CI, and a contract between the components that must stay
explicit, which ADR 0002 defines.
