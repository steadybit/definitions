# downstream-http-client-errors

Simulated downstream HTTP client errors within a service. Useful to validate how a service behaves when a downstream HTTP service faces various issues.

## Example Service Definition

```yaml
tasks:
  - name: 'steadybit/definitions/jvm/spring/experiments/downstream-http-client-errors'
    version: 0.3.0
    parameters:
      teamKey: 'BS'
      environmentName: 'Online Shop PROD'
      application: "gateway"
      httpEndpoint: "https://k8s-dev.demo.steadybit.io/products"
      failureCauses: "[\"ERROR\"]"
      httpMethods: "[\"GET\"]"
      hostAddress: "toys-bestseller.steadybit-demo.svc.cluster.local:8081"
```

## Parameters

| Name                  | Type   | Required | Default        | Description                                                                                                          |
|-----------------------|--------|----------|----------------|----------------------------------------------------------------------------------------------------------------------|
| `environmentName`     | string | yes      |                | The environment which is used for the experiment                                                                     |
| `teamKey`             | string | yes      |                | The team which is used for the experiment                                                                            |
| `application`         | string | yes      |                | The name of the JVM application for which HTTP client errors should be simulated.                                    |
| `httpEndpoint`        | string | yes      |                | A URL polled as part of the experiment. Should point to the JVM referenced through `application`. This URL should result in a downstream HTTP client call. |
| `failureCauses`       | string | yes      |                | Nested JSON `string[]` indicating what type of HTTP client errors should be simulated. Supported values: `[\"ERROR\",\"TIMEOUT\",\"HTTP_500\",\"HTTP_502\",\"HTTP_503\",\"HTTP_504\",\"HTTP_5XX\",\"HTTP_400\",\"HTTP_403\",\"HTTP_404\",\"HTTP_429\",\"HTTP_4XX\"]`. |
| `httpMethods`         | string | yes      |                | Nested JSON `string[]` describing which HTTP client calls should receive simulated errors. |
| `hostAddress`         | string | yes      |                | Host address (including port if a port is defined in code) to describe which HTTP client calls should receive simulated errors.   |
| `urlPath`             | string | no       | "*"            | Optional URL path segment to restrict which HTTP client calls should receive simulated errors..  |