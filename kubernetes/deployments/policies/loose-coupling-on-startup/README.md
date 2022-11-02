# kubernetes/deployments/policies/loose-coupling-on-startup

Nobody wants to ensure that services are started in a specific order. Verify that no startup coupling to dependent services would enforce a specific startup order.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/loose-coupling-to-dependency-during-startup

## Example Policy Binding

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/loose-coupling-on-startup'
    version: 0.5.6
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop DEV'
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
````