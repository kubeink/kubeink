# 0003. Deterministic data, the model only interprets

- **Status:** Accepted
- **Date:** 2026-11-27

## Context

kubeink reports are delivered to clients and used to make decisions about
their platforms. Language models can produce figures and resource names that
look plausible and are wrong, and a single invented number makes the whole
report untrustworthy.

## Decision

Every figure and every resource name in a report comes from the collectors,
which read the cluster deterministically. The renderer places that data in the
report. The model writes the explanations and recommendations around it, and a
verifier checks that every claim in the text matches the collected data.

## Consequences

Reports can be trusted and tested: the same cluster state always produces the
same data. The model has less freedom, and report templates must define where
each piece of data goes. When no model is configured, kubeink still produces a
data-only report.
