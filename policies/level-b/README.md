# level-b

Challenges for loose coupling on startup.

## Used Tasks

- steadybit/definitions/experiments/loose-coupling-to-dependency-during-startup

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/policies/level-b'
    version: 0.1.0
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop DEV'
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
````