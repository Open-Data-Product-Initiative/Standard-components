# Data QoS 

Data Quality of Service **Object** contains attributes which define the desired and promised quality of the data product from data quality and service quality point of view. 

The Object follows Data QoS model created by Jean-Georges Perrin. Data QoS contains 19 indicators, out of which 16 have been defined in ODPS to include "as code" structure. "As code" refers to Everything as Code philosophy. [Everything as Code](https://www.dynatrace.com/news/blog/everything-as-code/) is the practice of treating all parts of the system as code. Each indicator is an object that has both threshold values set by the business and "as code" rules to monitor and verify wanted quality level.  

![Indicator Schema](images/indicator.jpg)

The remaining 3 indicators General availability, End of support, and End of life are information which in Open Data Product Specification belong to document level defining general features of the data product. (Not implemented in this Trial)

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
    objective: 0.1
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
      unit: hour 
      objective: 1
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
        type: custom   
        format: yaml
        rules:
          - ....as code....
  timeToRepair:
      description: "" 
      unit: minute 
      objective: 120
      monitoring:
        type: custom   
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
| DataQoS | element | - | Binds the Data QoS related elements and attributes together |
| availability | element | - | The availability of the service/data. |
| coverage | element | - | The availability of the service/data. |
| description | string | max length 256 chars | Brief description of the indicator |
| unit | string | one of: minute, hour, day, month, percentage | Measurement unit. |
| objective | integer | integer | Minimum threshold level defined by the business based on customer needs. |
| monitoring | element | - | Binds together "as code" description of the DataQos indicator. Every indicator has monitoring part as well. |
| type | string | max length 50 chars | Value indicates the used system or standard. For example DataDog, SodaCL, Montecarlo, and custom. Helps in identifying what to expect in actual rules content  |
| format | string | one of: string, yaml | Value indicates in which format the rules will be given. |
| rules | string | - | The quality rules can be encoded as a string or as inline YAML. |

If you see something missing, described inaccurately or plain wrong, or you want to comment the specification, [raise an issue in Github](https://github.com/Open-Data-Product-Initiative/open-data-product-spec-dev/issues)
