# Pricing Extensions

Pricing components


## 

**Optional attributes and elements**

> Example of Pricing component usage with some of the optional elements and attributes:

```yml

pricingPlans:
    - name: Premium subscription 1 year
    priceCurrency: EUR
    price: 10.00
    x-standardized:
        minPrice: 5.00
        maxPrice: 15.000
        additionalPrice: 0.02
    - name: Premium Package
    priceCurrency: EUR
    price: 10.00
    x-standardized:
        maxPrice: 20.00
        valueAddedTaxIncluded: False

```

| <div style="width:150px">Element name</div>   | Type  | Options  | Description  |
|---|---|---|---|
|  minPrice | string  | -  | The lowest price if the price is a range. If dynamic pricing is used with this product, this is the lowest price allowed. In dynamic pricing businesses are able to change prices based on algorithms that take into account competitor pricing, supply and demand, and other external factors in the market. Use '.' (Unicode 'FULL STOP' (U+002E)) rather than ',' to indicate a decimal point. Avoid using these symbols as a readability separator. Use values from 0123456789 (Unicode 'DIGIT ZERO' (U+0030) to 'DIGIT NINE' (U+0039)) rather than superficially similiar Unicode symbols. |
|  maxPrice | string  | -  | The highest price if the price is a range. If dynamic pricing is used with this product, this is the highest price allowed. Use '.' (Unicode 'FULL STOP' (U+002E)) rather than ',' to indicate a decimal point. Avoid using these symbols as a readability separator. Use values from 0123456789 (Unicode 'DIGIT ZERO' (U+0030) to 'DIGIT NINE' (U+0039)) rather than superficially similiar Unicode symbols. |
| valueAddedTaxIncluded  | boolean  | true/false  | Specifies whether the applicable value-added tax (VAT) is included in the price specification or not.  |
| valueAddedTaxPercentage  | Integer  | Number percentage value, range 0-100 | Use '.' (Unicode 'FULL STOP' (U+002E)) rather than ',' to indicate a decimal point. Avoid using these symbols as a readability separator. Use values from 0123456789 (Unicode 'DIGIT ZERO' (U+0030) to 'DIGIT NINE' (U+0039)) rather than superficially similiar Unicode symbols.   |
| validFrom  | DateTime  |  A combination of date and time in [ISO 8601](https://www.ionos.com/digitalguide/websites/web-development/iso-8601/) format yyyy-MM-dd'T'HH:mm:ss.SSSZ. | The date when the item becomes valid. |
| validTo  | DateTime  | A combination of date and time in [ISO 8601](https://www.ionos.com/digitalguide/websites/web-development/iso-8601/) format yyyy-MM-dd'T'HH:mm:ss.SSSZ.  | The date after when the item is not valid. |
| additionalPrice  | string  | -  | This is used to define fees for usage which exceeds the defined max transaction quantity. This value is for each additional transaction. Use '.' (Unicode 'FULL STOP' (U+002E)) rather than ',' to indicate a decimal point. Avoid using these symbols as a readability separator. Use values from 0123456789 (Unicode 'DIGIT ZERO' (U+0030) to 'DIGIT NINE' (U+0039)) rather than superficially similiar Unicode symbols. |
|  maxDataQuantity | Integer  | -  | The maximum amount of data transferred during the billing duration. Unit is GB. |
|  valueSimulator  | url | valid url | Intended to be used with *value-based* pricing plan. Provide url to value simulator in which customer can see the value in various cases. In the simulator customer might be able to input own variables to match their exact case and see the gained value. |
