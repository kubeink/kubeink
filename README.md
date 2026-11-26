# kubeink

**AI-written status reports for Kubernetes and OpenShift clusters, with privacy by design.**

> [!WARNING]
> kubeink is in early development and is not usable yet. Follow the
> [architecture document](docs/design/architecture.md) to see where it is going.

kubeink writes status reports for Kubernetes and OpenShift clusters. A team of
AI agents analyses the state of the cluster and drafts the report, on a
schedule or in response to an event, and a person approves it before it is
delivered.

Cluster data is confidential, so kubeink replaces every real identifier with a
stable alias before any model sees it, and every figure in the report comes
from the cluster, never from the model.

## License

kubeink is licensed under the [Apache License 2.0](LICENSE).
