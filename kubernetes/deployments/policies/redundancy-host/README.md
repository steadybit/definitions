# kubernetes/deployments/redundancy-host

Challenges for host redundancy.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/faultless-redundancy-host
- steadybit/definitions/kubernetes/deployments/weak-spots/single-node

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/redundancy-host'
    version: 0.2.0
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