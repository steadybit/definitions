# kubernetes/deployments/policies/recovery-pod

A service needs to be able to recover in case of problems. At a bare minimum, it needs to support restarts when the container or underlying host has an outage.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/recovery-of-single-container
- steadybit/definitions/kubernetes/deployments/experiments/recovery-of-single-host

## Example Policy Binding

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/recovery-pod'
    version: 0.5.4
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop DEV'
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
````