# Steadybit Resilience Policies and Task Definitions

This repository contains all pre-defined resilience policies and tasks to be used in our service definitions.

# Kubernetes

## Deployments

### Policies

- [http-client-fault-tolerance](./kubernetes/deployments/policies/http-client-fault-tolerance/README.md)
- [loose-coupling](./kubernetes/deployments/policies/loose-coupling/README.md)
- [loose-coupling-on-startup](./kubernetes/deployments/policies/loose-coupling-on-startup/README.md)
- [recovery-pod](./kubernetes/deployments/policies/recovery-pod/README.md)
- [redundancy-host](./kubernetes/deployments/policies/redundancy-host/README.md)
- [redundancy-pod](./kubernetes/deployments/policies/redundancy-pod/README.md)
- [rolling-update](./kubernetes/deployments/policies/rolling-update/README.md)

### Experiments

- [faultless-redundancy-container](./kubernetes/deployments/experiments/faultless-redundancy-container/README.md)
- [faultless-redundancy-host](./kubernetes/deployments/experiments/faultless-redundancy-host/README.md)
- [faultless-redundancy-rolling-update](./kubernetes/deployments/experiments/faultless-redundancy-rolling-update/README.md)
- [loose-coupling-to-dependency](./kubernetes/deployments/experiments/loose-coupling-to-dependency/README.md)
- [loose-coupling-to-dependency-during-startup](./kubernetes/deployments/experiments/loose-coupling-to-dependency-during-startup/README.md)
- [recovery-of-single-container](./kubernetes/deployments/experiments/recovery-of-single-container/README.md)
- [recovery-of-single-host](./kubernetes/deployments/experiments/recovery-of-single-host/README.md)

### Weak Spots

- [deployment-strategy](./kubernetes/deployments/weak-spots/deployment-strategy/README.md)
- [readiness-probe](./kubernetes/deployments/weak-spots/readiness-probe/README.md)
- [single-node](./kubernetes/deployments/weak-spots/single-node/README.md)
- [single-replica](./kubernetes/deployments/weak-spots/single-replica/README.md)

