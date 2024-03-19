# Data Quality Extensions

The availability of the service/data. Use common SLA apprach to define percentage of guaranteed availability

## Elements and structure

| <div style="width:150px">Component name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| x-standardized | element | - | Binds together extension. This is used only in the example. This is part of unified method to add extensions to various data economy standards |
| $schema | valid URL | URL | URL to Schema that defines spec element content options. This is provided and maintained by vendor. |
| kind | attribute | string | Defines the core component class this component extends. Options: dataquality, access, pricing, sla, stakeholders,  provider |
| vendor | attribute | string | Name of the vendor |
| spec | element | - | If extension contains EaC approach, this is the element in which vendor system specific "as code" specification is provided. |


## Montecarlo 

Monte Carlo simulation is utilized as a data quality tool to assess the robustness and reliability of datasets through probabilistic modeling. Monte Carlo provides a method to validate data quality measures and assumptions, ensuring the accuracy and integrity of the dataset.

Monte Carlo offers a variety of monitors so that data teams can:

- Instantly deploy broad monitoring of your data pipelines, with no manual configuration. These monitors use metadata whenever possible so that compute costs are minimal.
- Strategically deploy deep quality monitoring on the tables that are more important. These monitors directly query the data, to alert to shifts in the data's profile, failed validations, and more.

Detailed documentation explaining options and structure you can add under "spec" element: https://docs.getmontecarlo.com/docs/monitors-overview  

> Example of Montecarlo extension usage

```yml
x-standardized:
    $schema: URL
    kind: dataquality
    vendor: Montecarlo
    objectives:
        field_health:
            display_name: Field Health
            target: 100
    spec:
        field_health:
        - table: project:dataset.table_name
            timestamp_field: created
        dimension_tracking:
        - table: project:dataset.table_name
            timestamp_field: created
            field: order_status 
```


## SodaCL

> Example of SodaCL extension usage

```yml
x-standardized:
    $schema: URL
    kind: dataquality
    vendor: SodaCL
    spec:
    - for each column:
        name: [member_id, gender, age_band]
        checks:
            - not null:
                fail: when > 2% # Fail if more than 2% of records are null

 
```
