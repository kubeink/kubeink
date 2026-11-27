# 0006. Ports and adapters

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

kubeink depends on things that vary between users and over time: the model
provider, the sources of cluster data, the output format of the report and the
place where reports are stored. If the core logic called each of them
directly, every new provider or format would mean changing and retesting the
core.

## Decision

Both components follow a ports and adapters architecture. The core defines an
interface, or port, for each external dependency, and each concrete
integration is an adapter that implements it. Model providers, data sources,
output formats and report storage are all adapters.

## Consequences

New integrations are added without touching the core, and the core is tested
with fake adapters, without a cluster or a model. The cost is an extra layer of
interfaces, which must be kept small and stable so that adapters do not break
on every change.
