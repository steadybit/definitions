# kubernetes/deployments/policies/rolling-update

Redundancy is essential when you roll out new versions of your service. This is why you need a rolling update strategy and you should simulate the rollout to check for side effects.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/faultless-redundancy-rolling-update
- steadybit/definitions/kubernetes/deployments/weak-spots/deployment-strategy

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/rolling-update'
    version: 0.5.3
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