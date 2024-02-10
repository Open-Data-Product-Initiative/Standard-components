# Data QoS 

Data Quality of Service **Object** contains attributes which define the desired and promised quality of the data product from data quality and service quality point of view. 

## Optional attributes and elements

> Example of DataQoS component usage:

```yml

DataQoS:
  availability:
    description: "" # optional description
    unit: level # if type is sla, then SLA levels as options: best effort, 90, 95, 97.5, 99, 99.99
    objective: 95
    monitoring:
      type: xxxx   # data quality check format: existing solutions such as:
      format: yaml # inline, yaml, string, reference. Content under "rules:"
      rules:
        - ....as code....
  coverage:
    description: "" # optional description
    unit: percentage # if type is sla, then SLA levels as options: best effort, 90, 95, 97.5, 99, 99.99
    objective: 100
    monitoring:
      type: SodaCL   # data quality check format: existing solutions such as:
      format: yaml # inline, yaml, string, reference. Content under "rules:"
      rules:
        - ....as code....
  conformity:
    description: "" # optional description
    unit: percentage # if type is sla, then SLA levels as options: best effort, 90, 95, 97.5, 99, 99.99
    objective: 100
    monitoring:
      type: SodaCL   # data quality check format: existing solutions such as:
      format: yaml # inline, yaml, string, reference. Content under "rules:"
      rules:
        - ....as code....
  completeness:
    description: "" # optional description
    unit: percentage # if type is sla, then SLA levels as options: best effort, 90, 95, 97.5, 99, 99.99
    objective: 100
    monitoring:
      type: SodaCL   # data quality check format: existing solutions such as:
      format: yaml # inline, yaml, string, reference. Content under "rules:"
      rules:
        - ....as code....




```

| <div style="width:150px">Element name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| SLA | element | - | Binds the SLA related elements and attributes together |


If you see something missing, described inaccurately or plain wrong, or you want to comment the specification, [raise an issue in Github](https://github.com/Open-Data-Product-Initiative/open-data-product-spec-dev/issues)
