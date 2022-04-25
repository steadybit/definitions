# kubernetes/deployments/policies/recovery-pod

Challenges for recovery.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/recovery-of-single-container
- steadybit/definitions/kubernetes/deployments/experiments/recovery-of-single-host

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/recovery-pod'
    version: 0.3.0
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop DEV'
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
````