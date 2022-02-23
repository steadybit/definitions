# faultless-redundancy-container

Kubernetes deployment HTTP endpoint serves successful HTTP responses while a single container becomes temporarily unreachable.
Use this to verify a redundant deployment with readiness checks.
It is recommended to check first for the weak spots `k8s-single-replica`, `k8s-readiness-probe`.
This task requires an exposed HTTP endpoint and at least two pod replicas.
A configurable HTTP call success rate is expected throughout.

## Example Service Definition

```yaml
name: demo-gateway
tasks:
  - name: "steadybit/definitions/tasks/faultless-redundancy-container"
    version: 0.1.0
    forEach:
      iterables: [ container ]
      define:
        parameters:
          teamKey: "BS"
          environmentName: "Online Shop DEV"
          httpEndpoint: "https://k8s-dev.demo.steadybit.io/products"
          containerName: "{{container.name}}"
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
```

## Parameters

| Name                | Type   | Required | Default        | Description                                      |
|---------------------|--------|----------|----------------|--------------------------------------------------|
| `environmentName`   | string | yes      |                | The environment which is used for the experiment |
| `teamKey`           | string | yes      |                | The team which is used for the experiment        |
| `k8sClusterName`    | string | no       | (from mapping) | The Kubernetes cluster of the container          |
| `k8sNamespaceName`  | string | no       | (from mapping) | The Kubernetes namespace of the container        |
| `k8sDeploymentName` | string | no       | (from mapping) | The Kubernetes deployment of the container       |
| `containerName`     | string | yes      |                | The name of the container to kill                |
| `httpEndpoint`      | url    | yes      |                | The HTTP endpoint to check using GET requests    |
| `successRate`       | number | no       | 95             | The minimum required success rate.               |