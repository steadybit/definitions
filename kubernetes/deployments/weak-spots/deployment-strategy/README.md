# deployment-strategy

Verifies whether the Kubernetes deployment has a rolling update deployment strategy configured.

## Example Service Definition

```yaml
name: demo-gateway

tasks:
  - name: "steadybit/definitions/kubernetes/deployments/weak-spots/deployment-strategy"
    version: 0.3.0
    forEach:
      iterables: [ container ]
      define:
        containerName: "{{ container.name }}"

mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
```

## Parameters

| Name                | Type   | Required | Default        | Description                                                      |
|---------------------|--------|----------|----------------|------------------------------------------------------------------|
| `k8sClusterName`    | string | no       | (from mapping) | The Kubernetes cluster of the deployment                         |
| `k8sNamespaceName`  | string | no       | (from mapping) | The Kubernetes namespace of the deployment                       |
| `k8sDeploymentName` | string | no       | (from mapping) | The Kubernetes deployment to restart and watch the pod count for |
| `containerName`     | string | yes      |                | The name of the container to investigate                         |