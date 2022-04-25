# loose-coupling-to-dependency-during-startup

Kubernetes deployment's pods can become ready when dependent services are unreachable.
Use this verify that deployment's pods have a loose coupling to dependent services during startup.

## Example Service Definition

```yaml
name: demo-gateway
parameters:
  teamKey: "BS"
  environmentName: "Online Shop DEV"
  k8sDependencyClusterName: "demo-dev"
  k8sDependencyNamespaceName: "steadybit-demo"
tasks:
  - name: "steadybit/definitions/kubernetes/deployments/experiments/loose-coupling-to-dependency-during-startup"
    version: 0.3.2
    parameters:
      k8sDependencyDeploymentName: "fashion-bestseller"
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
```

## Parameters

| Name                          | Type   | Required | Default        | Description                                                      |
|-------------------------------|--------|----------|----------------|------------------------------------------------------------------|
| `environmentName`             | string | yes      |                | The environment which is used for the experiment                 |
| `teamKey`                     | string | yes      |                | The team which is used for the experiment                        |
| `k8sClusterName`              | string | no       | (from mapping) | The Kubernetes cluster of the deployment                         |
| `k8sNamespaceName`            | string | no       | (from mapping) | The Kubernetes namespace of the deployment                       |
| `k8sDeploymentName`           | string | no       | (from mapping) | The Kubernetes deployment to restart and watch the pod count for |
| `k8sDependencyClusterName`    | string | no       |                | The Kubernetes cluster of the deployment                         |
| `k8sDependencyNamespaceName`  | string | no       |                | The Kubernetes namespace of the deployment                       |
| `k8sDependencyDeploymentName` | string | no       |                | The Kubernetes deployment to make unreachable                    |