# Error rate

Use OpenSLO standard in the object to define rules in the spec. How often will your data have errors, and over what period? What is your tolerance for those errors?


## Components

> Example of error rate indicator usage

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
| **errorRate** | element | - | .... |


