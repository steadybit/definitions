# faultless-redundancy-host

Kubernetes deployment serves successful HTTP responses when a host is shut down.
Use this to verify that deployment's pods are spread across hosts.
It is recommended to check first for the weak spots `k8s-single-node`, `k8s-readiness-probe`. This task requires an exposed HTTP endpoint and at least two pod
replicas. A configurable HTTP call success rate is expected throughout.

## Example Service Definition

```yaml
name: demo-gateway
tasks:
  - name: "steadybit/definitions/kubernetes/deployments/experiments/faultless-redundancy-host"
    version: 0.3.1
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

| Name                | Type   | Required | Default        | Description                                                         |
|---------------------|--------|----------|----------------|---------------------------------------------------------------------|
| `environmentName`   | string | yes      |                | The environment which is used for the experiment                    |
| `teamKey`           | string | yes      |                | The team which is used for the experiment                           |
| `k8sClusterName`    | string | no       | (from mapping) | The Kubernetes cluster of the deployment                            |
| `k8sNamespaceName`  | string | no       | (from mapping) | The Kubernetes namespace of the deployment                          |
| `k8sDeploymentName` | string | no       | (from mapping) | The Kubernetes deployment, of which hosts a single one is rebooted. |
| `httpEndpoint`      | url    | yes      |                | The HTTP endpoint to check using GET requests                       |
| `successRate`       | number | no       | 95             | The minimum required success rate.                                  |