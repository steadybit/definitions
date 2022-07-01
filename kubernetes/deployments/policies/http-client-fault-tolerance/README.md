# kubernetes/deployments/policies/http-client-fault-tolerance

Validate how your service behaves when a downstream HTTP service faces issues.

## Used Tasks

- steadybit/definitions/jvm/spring/experiments/downstream-http-client-errors

## Example Service Definition

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/http-client-fault-tolerance'
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