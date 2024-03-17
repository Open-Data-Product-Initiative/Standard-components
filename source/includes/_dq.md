# Data Quality

The availability of the service/data. Use common SLA apprach to define percentage of guaranteed availability


## Montecarlo 

> Example of Montecarlo extension usage

```yml
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
| **availability** | element | - | Binds together availability indicator description with objectives and monitoring. Follows OpenSLO standard model. |
| description | attribute | string | Short description to be used in displying more detailed information for consumers and operations staff.  |
| monitoring | object | - | Binds together both monitoring and objectives (threshold values) structure |
| type | attribute | string | Defines the standard used in describing the monitoring object contant. Call also be vendor specific such as MonteCarlo and SodaCL. Details in type definition (link) |
| spec | object | - | Inside this object you write the type specified description or objectives and monitoring as code. |
| objectives | array | - | Define the objectives (threshold values) for expected quality of this indicator. |

## SodaCL

> Example of SodaCL extension usage

```yml

objectives:
- displayName: Completeness
  target: 98
spec:
  - for each column:
      name: [member_id, gender, age_band]
      checks:
        - not null:
            fail: when > 2% # Fail if more than 2% of records are null

 
```

| <div style="width:150px">Component name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **availability** | element | - | Binds together availability indicator description with objectives and monitoring. Follows OpenSLO standard model. |
| description | attribute | string | Short description to be used in displying more detailed information for consumers and operations staff.  |
| monitoring | object | - | Binds together both monitoring and objectives (threshold values) structure |
| type | attribute | string | Defines the standard used in describing the monitoring object contant. Call also be vendor specific such as MonteCarlo and SodaCL. Details in type definition (link) |
| spec | object | - | Inside this object you write the type specified description or objectives and monitoring as code. |
| objectives | array | - | Define the objectives (threshold values) for expected quality of this indicator. |