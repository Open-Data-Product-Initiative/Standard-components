# Completeness

Data content must align with required standards, syntax (format, type, range), or permissible domain values. Conformity assesses how closely data adheres to standards, whether internal, external, or industry-wide.


## Components

> Example of completeness indicator usage

```yml

DataQoS:
  completeness:
    description: ""
    monitoring:
      type: SodaCL 
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
| **completeness** | element | - | .... |


