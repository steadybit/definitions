# kubernetes/deployments/policies/loose-coupling

Loose coupling to dependent services while processing requests is a dream come true. Check that your services can still respond successfully when dependencies are unavailable.

## Used Tasks

- steadybit/definitions/kubernetes/deployments/experiments/loose-coupling-to-dependency

## Example Policy Binding

````yaml
id: ca086ce3-15af-4b5a-9fda-456d03ad82c0
name: demo-gateway
policies:
  - name: 'steadybit/definitions/kubernetes/deployments/policies/loose-coupling'
    version: 0.5.4
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