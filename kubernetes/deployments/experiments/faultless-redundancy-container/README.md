# faultless-redundancy-container

Check whether your redundancy to serve a HTTP endpoint works while a single container becomes temporarily unavailable.
This task requires an exposed HTTP endpoint and at least two pod replicas.

## Example Policy Binding

```yaml
name: demo-gateway
tasks:
  - name: "steadybit/definitions/kubernetes/deployments/experiments/faultless-redundancy-container"
    version: 0.5.5
    forEach:
      iterables: [ container ]
      define:
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