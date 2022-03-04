# kubernetes/deployments/loose-coupling-on-startup

Challenges for loose coupling on startup.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/loose-coupling-to-dependency-during-startup

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/loose-coupling-on-startup'
    version: 0.2.2
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop DEV'
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
````