# recovery-of-single-host

Verify that your deployment recovers when a host is shut down.
You can also verify that your deployments are host independent.
The affected deployments' pods should be replaced within ten minutes – ending with the Kubernetes deployment back in the ready state.

## Example Service Definition

```yaml
name: demo-gateway
tasks:
  - name: 'steadybit/definitions/kubernetes/deployments/experiments/recovery-of-single-host'
    version: 0.5.4
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop PROD'
      httpEndpoint: "https://k8s-dev.demo.steadybit.io/products"
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
```

## Parameters

| Name                  | Type   | Required | Default        | Description                                                         |
|-----------------------|--------|----------|----------------|---------------------------------------------------------------------|
| `environmentName`     | string | yes      |                | The environment which is used for the experiment                    |
| `teamKey`             | string | yes      |                | The team which is used for the experiment                           |
| `k8sClusterName`      | string | no       | (from mapping) | The Kubernetes cluster of the deployment                            |
| `k8sNamespaceName`    | string | no       | (from mapping) | The Kubernetes namespace of the deployment                          |
| `k8sDeploymentName`   | string | no       | (from mapping) | The Kubernetes deployment, of which hosts a single one is rebooted. |
| `maximumRecoveryTime` | string | no       | 10m            | The maximum allowed recovery time                                   |