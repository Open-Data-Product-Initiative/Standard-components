# Data Quality Extensions

The availability of the service/data. Use common SLA apprach to define percentage of guaranteed availability

## Elements and structure

| <div style="width:150px">Component name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| extension | element | - | Binds together extension. This is used only in the example. This is part of unified method to add extensions to various data economy standards |
| $schema | valid URL | URL | URL to Schema that defines spec element content options. This is provided and maintained by vendor. |
| kind | attribute | string | Defines the class in which extension belongs to. Options: dataquality, access, pricing, sla, stakeholders,  provider |
| vendor | attribute | string | Name of the vendor |
| spec | element | - | If extension contains EaC approach, this is the element in which vendor system specific "as code" specification is provided. |


## Montecarlo 

> Example of Montecarlo extension usage

```yml
extension:
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
extension:
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