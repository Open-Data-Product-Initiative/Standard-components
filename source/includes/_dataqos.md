# Data QoS 

Data Quality of Service **Object** contains attributes which define the desired and promised quality of the data product from data quality and service quality point of view. 

The Object follows Data QoS model created by Jean-Georges Perrin. Data QoS contains 19 indicators, out of which 16 have been defined in ODPS to include "as code" structure. "As code" refers to Everything as Code philosophy. [Everything as Code](https://www.dynatrace.com/news/blog/everything-as-code/) is the practice of treating all parts of the system as code. Each indicator is an object that has both threshold values set by the business and "as code" spec to monitor and verify wanted quality level.  

![Indicator Schema](images/indicator.jpg)

The remaining 3 indicators General availability, End of support, and End of life are information which in Open Data Product Specification belong to document level defining general features of the data product. (Not implemented in this Trial)

In this trial mandatory stucture elements are not defined and everyhing is marked as optional including the DataQoS object. Should it be mandatory and to what extend is a good questions and is another excercise. 

**You choose the indicators from 16 options which matches your needs. No need to use all.**

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
  errorRate:
    description: "" 
    monitoring:
      type: OpenSLO
      spec: # inside the spec we use OpenSLO standard, https://github.com/openslo/openslo
        objectives:
          - displayName: Total Errors
            target: 0.98
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

| <div style="width:150px">Indicator name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **DataQoS** | element | - | Binds the Data QoS related elements and attributes together |


### Additional common unified fields used in 19 indicators

| <div style="width:150px">Common unified fields</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **description** | string | max length 256 chars | Brief description of the indicator |
| **objectives** | array | array | Contains both name and target value. See example. Formatting of objectives is defined in OpenSLO.|
| **monitoring** | element | - | Binds together "as code" description of the DataQos indicator. Every indicator has monitoring part as well. |
| **type** | string | max length 50 chars | Value indicates the used system or standard. For example DataDog, OpenSLO, SodaCL, Montecarlo, and custom. Helps in identifying what to expect in actual spec content  |
| **spec** | string | - | The indicator spec can be encoded as a string or as inline YAML. Formerting of this depends of the *type* selected |

If you see something missing, described inaccurately or plain wrong, or you want to comment the specification, [raise an issue in Github](https://github.com/Open-Data-Product-Initiative/open-data-product-spec-dev/issues)