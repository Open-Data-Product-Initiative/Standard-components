# Conformity

Data content must align with required standards, syntax (format, type, range), or permissible domain values. Conformity assesses how closely data adheres to standards, whether internal, external, or industry-wide.


## Components

> Example of conformity indicator usage

```yml

DataQoS:
  conformity:
    description: "" 
    monitoring:
      type: SodaCL  
      objectives:
        - displayName: Conformity
          target: 90
      spec:
        - gender: matches("^(Male|Female|Other)$")
        - age_band: matches("^\\d{2}-\\d{2}$")  # Assuming age bands are in the format 20-29, 30-39, etc.
 
```

| <div style="width:150px">Component name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **conformity** | element | - | .... |


