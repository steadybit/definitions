# recovery-of-single-container

The Kubernetes deployment recovers when a container is killed.
Use this to verify that restarts are possible.
The affected pod should be replaced within a given time – ending with the Kubernetes deployment back in the ready state.

## Example Service Definition

```yaml
name: demo-gateway
tasks:
  - name: "steadybit/definitions/kubernetes/deployments/experiments/recovery-of-single-container"
    version: 0.5.3
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

| Name                  | Type   | Required | Default        | Description                                      |
|-----------------------|--------|----------|----------------|--------------------------------------------------|
| `environmentName`     | string | yes      |                | The environment which is used for the experiment |
| `teamKey`             | string | yes      |                | The team which is used for the experiment        |
| `k8sClusterName`      | string | no       | (from mapping) | The Kubernetes cluster of the container          |
| `k8sNamespaceName`    | string | no       | (from mapping) | The Kubernetes namespace of the container        |
| `k8sDeploymentName`   | string | no       | (from mapping) | The Kubernetes deployment of the container       |
| `containerName`       | string | yes      |                | The name of the container to kill                |
| `maximumRecoveryTime` | string | no       | 2m             | The maximum allowed recovery time                |

