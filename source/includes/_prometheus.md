# Error rate

Use OpenSLO standard in the object to define rules in the spec. How often will your data have errors, and over what period? What is your tolerance for those errors?


## Components

> Example of error rate indicator usage

```yml

DataQoS:
  errorRate:
    description: "" 
    monitoring:
      type: OpenSLO
      spec: # inside the spec we use OpenSLO standard, https://github.com/openslo/openslo
        objectives:
          - displayName: Total Errors
            target: 0.98
        ratioMetric:
          counter: true
          good:
            metricSource:
              type: Prometheus
              metricSourceRef: prometheus-datasource
              spec:
                query: sum(localhost_server_requests{code=~"2xx|3xx",host="*",instance="127.0.0.1:9090"})
          total:
            metricSource:
              type: Prometheus
              metricSourceRef: prometheus-datasource
              spec:
                query: localhost_server_requests{code="total",host="*",instance="127.0.0.1:9090"}
 
```

| <div style="width:150px">Component name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **errorRate** | element | - | .... |


