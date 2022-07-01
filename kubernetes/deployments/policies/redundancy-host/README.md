# kubernetes/deployments/policies/redundancy-host

Ensure that your service is properly redundant on host level to avoid a single point of failure of the infrastructure.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/faultless-redundancy-host
- steadybit/definitions/kubernetes/deployments/weak-spots/single-node
- steadybit/definitions/kubernetes/deployments/weak-spots/readiness-probe

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/redundancy-host'
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