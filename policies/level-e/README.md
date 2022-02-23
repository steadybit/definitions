# level-e

Challenges for host redundancy.

## Used Tasks

- steadybit/definitions/experiments/faultless-redundancy-container
- steadybit/definitions/weak-spots/k8s-readiness-probe
- steadybit/definitions/weak-spots/k8s-single-replica

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/policies/level-e'
    version: 0.1.2
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