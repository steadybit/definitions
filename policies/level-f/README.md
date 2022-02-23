# level-f

Challenges for recovery.

## Used Tasks

- steadybit/definitions/experiments/recovery-of-single-container
- steadybit/definitions/experiments/recovery-of-single-host

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/policies/level-f'
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