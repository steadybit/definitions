# faultless-redundancy-rolling-update

Verify whether your deployment serves successful HTTP responses while performing an update. So, is your configured rolling update strategy functional?
This task requires an exposed HTTP endpoint and at least two pod replicas.

## Example Policy Binding

```yaml
name: demo-gateway
tasks:
  - name: "steadybit/definitions/kubernetes/deployments/experiments/faultless-redundancy-rolling-update"
    version: 0.5.6
    parameters:
      teamKey: "BS"
      environmentName: "Online Shop DEV"
      httpEndpoint: "https://k8s-dev.demo.steadybit.io/products"
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
```

## Parameters

| Name                      | Type   | Required | Default        | Description                                                |
|---------------------------|--------|----------|----------------|------------------------------------------------------------|
| `environmentName`         | string | yes      |                | The environment which is used for the experiment           |
| `teamKey`                 | string | yes      |                | The team which is used for the experiment                  |
| `k8sClusterName`          | string | no       | (from mapping) | The Kubernetes cluster of the deployment                   |
| `k8sNamespaceName`        | string | no       | (from mapping) | The Kubernetes namespace of the deployment                 |
| `k8sDeploymentName`       | string | no       | (from mapping) | The Kubernetes deployment to roll over.                    |
| `httpEndpoint`            | url    | yes      |                | The HTTP endpoint to check using GET requests              |
| `successRate`             | number | no       | 95             | The minimum required success rate.                         |
| `expectedRolloutDuration` | string | no       | 3m             | For how long the configured success rate will be verified. |