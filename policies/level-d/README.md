# level-d

Challenges for redundancy during updates.

## Used Tasks

- steadybit/definitions/experiments/faultless-redundancy-rolling-update
- steadybit/definitions/weak-spots/k8s-deployment-strategy

- == Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/policies/level-d'
    version: 0.1.0
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop DEV'
      httpEndpoint: "https://k8s-dev.demo.steadybit.io/products"
mapping:
  kubernetes:
    cluster: demo-dev
    namespace: steadybit-demo
    deployment: gateway
````