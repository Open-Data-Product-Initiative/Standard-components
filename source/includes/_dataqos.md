# Data QoS 

Data Quality of Service **Object** contains attributes which define the desired and promised quality of the data product from data quality and service quality point of view. 

## Optional attributes and elements

> Example of DataQoS component usage:

```yml

DataQoS:
  availability:
    description: "Availability SLA level of the data product."
    unit: integer 
    objective: 95
    monitoring:
      type: DataDog  
      format: yaml 
      rules:
        - ....as code....
  coverage:
    description: ""
    unit: percentage 
    objective: 100
    monitoring:
      type: SodaCL  
      format: yaml 
      rules:
        - ....as code....
  conformity:
    description: "" 
    unit: percentage 
    objective: 100
    monitoring:
      type: SodaCL  
      format: yaml
      rules:
        - ....as code....
  completeness:
    description: "" 
    unit: percentage 
    objective: 90
    monitoring:
      type: SodaCL   
      format: yaml
      rules:
        - ....as code....
  accuracy:
    description: "" 
    unit: percentage 
    objective: 99
    monitoring:
      type: SodaCL   
      format: yaml
      rules:
        - ....as code....
  consistency:
    description: "" 
    unit: percentage 
    objective: 100
    monitoring:
      type: SodaCL   
      format: yaml
      rules:
        - ....as code....
  uniqueness:
    description: "" 
    unit: percentage 
    objective: 90
    monitoring:
      type: SodaCL   
      format: yaml
      rules:
        - ....as code....
  throughput:
    description: "" 
    unit: percentage 
    objective: 100
    monitoring:
      type: custom   
      format: yaml
      rules:
        - ....as code....
  errorRate:
    description: "" 
    unit: percentage 
    objective: 100
    monitoring:
      type: custom   
      format: yaml
      rules:
        - ....as code....
  retention:
      description: "" 
      unit: percentage 
      objective: 100
      monitoring:
        type: custom   
        format: yaml
        rules:
          - ....as code....
  frequency:
      description: "" 
      unit: percentage 
      objective: 100
      monitoring:
        type: custom   
        format: yaml
        rules:
          - ....as code....
  latency:
      description: "" 
      unit: percentage 
      objective: 100
      monitoring:
        type: custom   
        format: yaml
        rules:
          - ....as code....
  timeToDetect:
      description: "" 
      unit: minute 
      objective: 5
      monitoring:
        type: custom   
        format: yaml
        rules:
          - ....as code....
  timeToNotify:
      description: "" 
      unit: minute 
      objective: 60
      monitoring:
        type: SodaCL   
        format: yaml
        rules:
          - ....as code....
  timeToRepair:
      description: "" 
      unit: minute 
      objective: 120
      monitoring:
        type: SodaCL   
        format: yaml
        rules:
          - ....as code....
   timeliness:
      description: "" 
      unit: minute 
      objective: 120
      monitoring:
        type: SodaCL   
        format: yaml
        rules:
          - ....as code....
```

| <div style="width:150px">Element name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| SLA | element | - | Binds the SLA related elements and attributes together |


If you see something missing, described inaccurately or plain wrong, or you want to comment the specification, [raise an issue in Github](https://github.com/Open-Data-Product-Initiative/open-data-product-spec-dev/issues)
