# Data QoS 

Data Quality of Service **Object** contains attributes which define the desired and promised quality of the data product from data quality and service quality point of view. 

The Object follows Data QoS model created by Jean-Georges Perrin. Data QoS contains 19 indicators, out of which 16 have been defined in ODPS to include "as code" structure. "As code" refers to Everything as Code philosophy. [Everything as Code](https://www.dynatrace.com/news/blog/everything-as-code/) is the practice of treating all parts of the system as code. Each indicator is an object that has both threshold values set by the business and "as code" spec to monitor and verify wanted quality level.  

![Indicator Schema](images/indicator.jpg)

The remaining 3 indicators General availability, End of support, and End of life are information which in Open Data Product Specification belong to document level defining general features of the data product. (Not implemented in this Trial)

In this trial mandatory stucture elements are not defined and everyhing is marked as optional including the DataQoS object. Should it be mandatory and to what extend is a good questions and is another excercise. 

## Optional attributes and elements

> Example of DataQoS component usage:

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
  errorRate:
    description: "" 
    monitoring:
      type: OpenSLO
      objectives:
        - displayName: Total Errors
          target: 0.98
      spec: # inside the spec we use OpenSLO standard, https://github.com/openslo/openslo
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

| <div style="width:150px">Element name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| DataQoS | element | - | Binds the Data QoS related elements and attributes together |
| availability | element | - | The availability of the service/data. Use common SLA apprach to define percentage of guaranteed availability |
| coverage | element | - | All records are contained in a data store or data source. Coverage relates to the extent and availability of data present but absent from a dataset. |
| conformity | element | - | Data content must align with required standards, syntax (format, type, range), or permissible domain values. Conformity assesses how closely data adheres to standards, whether internal, external, or industry-wide. |
| completeness | element | - | Data is required to be populated with a value (aka not null, not nullable). Completeness checks if all necessary data attributes are present in the dataset. |
| accuracy | element | - | The measurement of the veracity of data to its authoritative source: the data is provided but incorrect. Accuracy refers to how precise data is, and it can be assessed by comparing it to the original documents and trusted sources or confirming it against business spec. |
| consistency | element | - | Data should retain consistent content across data stores. Consistency ensures that data values, formats, and definitions in one group match those in another group. |
| uniqueness | element | - | How much data can be duplicated? It supports the idea that no record or attribute is recorded more than once. Uniqueness means each record and attribute should be one-of-a-kind, aiming for a single, unique data entry |
| throughPut | element | - | Throughput is about how fast I can access the data. It can measured in bytes or records by unit of time. |
| errorRate | element | - | Use OpenSLO standard in the object to define rules in the spec. How often will your data have errors, and over what period? What is your tolerance for those errors? |
| retention | element | - | How long are we keeping the records and documents? There is nothing extraordinary here, as with most service-level indicators, it can vary by use case and legal constraints. |
| frequency | element | - |How often is your data updated? Daily? Weekly? Monthly? A linked indicator to this frequency is the time of availability, which applies well to daily batch updates. |
| latency | element | - | Measures the time between the production of the data and its availability for consumption. |
| timeToDetect | element | - | How fast can you detect a problem? How fast do you guarantee the detection of the problem?  |
| timeToNotify | element | - | Once you see a problem, how much time do you need to notify your users?  |
| timeToRepair | element | - | How long do you need to fix the issue once it is detected?  |
| timeliness | element | - | The data must represent current conditions; the data is available and can be used when needed. Timeliness gauges how well data reflects current market/business conditions and its availability when needed |
| description | string | max length 256 chars | Brief description of the indicator |
| unit | string | one of: minute, hour, day, month, percentage | Measurement unit. |
| objective | integer | integer | Minimum threshold level defined by the business based on customer needs. |
| monitoring | element | - | Binds together "as code" description of the DataQos indicator. Every indicator has monitoring part as well. |
| type | string | max length 50 chars | Value indicates the used system or standard. For example DataDog, SodaCL, Montecarlo, and custom. Helps in identifying what to expect in actual spec content  |
| format | string | one of: string, yaml | Value indicates in which format the spec will be given. |
| spec | string | - | The quality spec can be encoded as a string or as inline YAML. |

If you see something missing, described inaccurately or plain wrong, or you want to comment the specification, [raise an issue in Github](https://github.com/Open-Data-Product-Initiative/open-data-product-spec-dev/issues)
