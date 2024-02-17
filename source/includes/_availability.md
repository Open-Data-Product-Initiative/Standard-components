# Availability

The availability of the service/data. Use common SLA apprach to define percentage of guaranteed availability


## Components

> Example of availability indicator usage

```yml

DataQoS:
  availability:
    description: "" 
    monitoring:
      type: OpenSLO
      spec: # inside the spec we use OpenSLO standard, https://github.com/openslo/openslo
        objectives:
          - displayName: Availability
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


