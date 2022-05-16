# loose-coupling-to-dependency

Kubernetes deployment's pods serve successful HTTP responses when dependent services are unreachable.
Use this to verify that deployment's pods have a loose coupling to dependent services during runtime.

## Example Service Definition

```yaml
name: demo-gateway
parameters:
  teamKey: "BS"
  environmentName: "Online Shop DEV"
  httpEndpoint: "https://k8s-dev.demo.steadybit.io/products"
  k8sDependencyClusterName: "demo-dev"
  k8sDependencyNamespaceName: "steadybit-demo"
tasks:
  - name: "steadybit/definitions/kubernetes/deployments/experiments/loose-coupling-to-dependency"
    version: 0.5.2
    parameters:
      k8sDependencyDeploymentName: "fashion-bestseller"
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
```

## Parameters

| Name                          | Type   | Required | Default        | Description                                          |
|-------------------------------|--------|----------|----------------|------------------------------------------------------|
| `environmentName`             | string | yes      |                | The environment which is used for the experiment     |
| `teamKey`                     | string | yes      |                | The team which is used for the experiment            |
| `k8sClusterName`              | string | no       | (from mapping) | The Kubernetes cluster of the deployment             |
| `k8sNamespaceName`            | string | no       | (from mapping) | The Kubernetes namespace of the deployment           |
| `k8sDeploymentName`           | string | no       | (from mapping) | The Kubernetes deployment to watch the pod count for |
| `k8sDependencyClusterName`    | string | no       |                | The Kubernetes cluster of the deployment             |
| `k8sDependencyNamespaceName`  | string | no       |                | The Kubernetes namespace of the deployment           |
| `k8sDependencyDeploymentName` | string | no       |                | The Kubernetes deployment to make unreachable        |
| `httpEndpoint`                | url    | yes      |                | The HTTP endpoint to check using GET requests        |
| `successRate`                 | number | no       | 100            | The minimum required success rate.                   |