### TBD

Indicators to be added to the specification

| <div style="width:150px">Indicator name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| coverage | element | - | All records are contained in a data store or data source. Coverage relates to the extent and availability of data present but absent from a dataset. |
| accuracy | element | - | The measurement of the veracity of data to its authoritative source: the data is provided but incorrect. Accuracy refers to how precise data is, and it can be assessed by comparing it to the original documents and trusted sources or confirming it against business spec. |
| consistency | element | - | Data should retain consistent content across data stores. Consistency ensures that data values, formats, and definitions in one group match those in another group. |
| uniqueness | element | - | How much data can be duplicated? It supports the idea that no record or attribute is recorded more than once. Uniqueness means each record and attribute should be one-of-a-kind, aiming for a single, unique data entry |
| throughPut | element | - | Throughput is about how fast I can access the data. It can measured in bytes or records by unit of time. |
| retention | element | - | How long are we keeping the records and documents? There is nothing extraordinary here, as with most service-level indicators, it can vary by use case and legal constraints. |
| frequency | element | - |How often is your data updated? Daily? Weekly? Monthly? A linked indicator to this frequency is the time of availability, which applies well to daily batch updates. |
| latency | element | - | Measures the time between the production of the data and its availability for consumption. |
| timeToDetect | element | - | How fast can you detect a problem? How fast do you guarantee the detection of the problem?  |
| timeToNotify | element | - | Once you see a problem, how much time do you need to notify your users?  |
| timeToRepair | element | - | How long do you need to fix the issue once it is detected?  |
| timeliness | element | - | The data must represent current conditions; the data is available and can be used when needed. Timeliness gauges how well data reflects current market/business conditions and its availability when needed |