# SLA Extensions

The availability of the service/data. Use common SLA apprach to define percentage of guaranteed availability


## Availability

### Prometheus 

> Example of Prometheus extension usage for availability

```yml
$schema: URL
kind: sla-availability
objective:
    displayName: Availability
    target: 0.98
monitoring:
    good:
        spec: sum(localhost_server_requests{code=~"2xx|3xx",host="*",instance="127.0.0.1:9090"})
    total:
        spec: localhost_server_requests{code="total",host="*",instance="127.0.0.1:9090"}
 
```

### Some other vendor 

> Example of Vendor extension usage for availability

```yml
$schema: URL
kind: sla-availability
objective:
    displayName: Availability
    target: 0.98
monitoring:
    good:
        spec: sum(localhost_server_requests{code=~"2xx|3xx",host="*",instance="127.0.0.1:9090"})
    total:
        spec: localhost_server_requests{code="total",host="*",instance="127.0.0.1:9090"}
 
```

| <div style="width:150px">Component name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **objectives** | element | - | measurement objective |
| description | attribute | string | Short description to be used in displying more detailed information for consumers and operations staff.  |
| monitoring | object | - | Binds together both monitoring and objectives (threshold values) structure |
| type | attribute | string | Defines the standard used in describing the monitoring object contant. Call also be vendor specific such as MonteCarlo and SodaCL. Details in type definition (link) |
| spec | object | - | Inside this object you write the type specified description or objectives and monitoring as code. |
| objectives | array | - | Define the objectives (threshold values) for expected quality of this indicator. |