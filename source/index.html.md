---
title: Standardized Extensions for Data Economy Specifications

language_tabs: # must be one of https://git.io/vQNgJ
- yml


toc_footers:
  - License <a href='https://creativecommons.org/licenses/by-sa/4.0/'>CC BY-SA 4.0</a>
  - <br/><a href='https://opendataproducts.org'>Specification home</a>


includes:
- access
- dq
- pricing
- provider
- roles
- sla
- stakeholders
- usecases


search: true

code_clipboard: true

meta:
  - name: description
    content: Standard components with extensions from vendors 
---

# Standardized Core Components and Extensions for Data Economy Specifications

A library of standardized core components and extentions to be used for example in Data Contracts and Data Product Sopecications. Solution vendors are invited to add extensions. 


# Introduction

**Core components** are shared between data economy standards. By default the core components are very limited and compact to keep the overall standards easy to adopt. 

The usecases can be extended by expanding the core components with localized and standardized versioned **extensions**. Extension pattern is universal and same in all core components. The core components can be extended with two distinctive patterns. Internal (locally used) woould use "x-localized" element and inside it is your local extension content. 

> Example of local extension usage:

```yml

x-localized:
 
```

Standardized extensions would be implemented with "x-standardized" element. Standarized extensions are grouped following the classes of core compoments. As an example, core object "Access" related standardized extensions are under "Access Extensions". More examples of those you can find from the core components below. 

> Example of standardized extension usage:

```yml

x-standardized:
 
```

# Core Components


## Access

## Data

## Data Quality

## Pricing

Pricing is the process whereby a business sets the price at which it will sell its products and services. Pricing **OBJECT** consists of mandatory and optional attributes. This element contains pricing plans related data to be used for example in displaying the items in a marketplace or as part of a data contract.   

Mandatory attributes are listed in separate table and marked with **bolded names** and asterix **\***. Next to the mandatory attributes is an example. 

The same logic applies to the optional attributes as well. Optional attributes are listed in own table and an example is given in the right column. 

Supported pricing models include:

1. Recurring time period based (day, week, month, year) plans
2. One time payments plans
3. Pay-as-you-go plans
4. Revenue sharing plans
5. Data volume plan
6. Dynamic pricing (high and low limits for automated pricing)
7. Pay what you want plans
8. Freemium
9. Open data
10. Value-based
11. On Request


**Mandatory attributes and elements**

> Example of Pricing component usage with manadatory elements and attributes:

```yml

pricingPlans:
- name: Premium subscription 1 year
  priceCurrency: EUR
  price: 50.00
  billingDuration: year
  unit: recurring
  maxTransactionQuantity: unlimited
  offering:
    - High Quality Pets data
    - Unlimited transactions
    - Billed annually 
- name: Premium Package Monthly
  priceCurrency: EUR
  price: 5.00
  billingDuration: month
  unit: recurring
  maxTransactionQuantity: unlimited
  offering:
    - High Quality Pets data
    - Unlimited transactions
    - Billed monthly 
 
```

| <div style="width:150px">Element name</div>   | Type  | Options  | Description  |
|---|---|---|---|
| **pricingPlans** | element | - | Binds the pricing plans related elements and attributes together |
| **en** | element | [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) defined 2-letter codes | **REQUIRED** - **NOTE! This is a dynamic element!** This element binds together other product pricing plan attributes and expresses the langugage used. In the example this is "en", which indicates that pricing plan details are in English. If you would like to use French details, then name the element "fr". The naming of this element follows options (language codes) listed in [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) standard. <br/><br/> You can have product pricing plan details in multiple languages simply by adding similar sets like the example - just change the binding element name to matching language code. <br/><br/> The pattern to implement multilanguage support for data products was adopted from de facto UI translation practices. The attributes inside this element are commonly rendered in the UI for the consumer and providing a simple way to implement that was the driving reasoning. See for example  [JSON - Multi Language](https://simplelocalize.io/docs/file-formats/multi-language-json/) |
| **priceCurrency** | string  |  Use standard formats: [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) currency format e.g. "USD"; Ticker symbol for cryptocurrencies e.g. "BTC"  | **REQUIRED** The primary currency used in pricing. Platforms are assumed to use this as primary currency if currency conversions are used to display product pricing in different locations for various currencies. If the *unit* is revenue-sharing, then this attribute value MUST be percentage.  |
| **price** | string  | -  | **REQUIRED** The offer price of a product, or of a price component, or revenue-sharing percentage. <br/><br/> If the *unit* of pricing is revenue-sharing, then this *price* attribute value is percentage value. <br/><br/> Use '.' (Unicode 'FULL STOP' (U+002E)) rather than ',' to indicate a decimal point. Avoid using these symbols as a readability separator. Use values from 0123456789 (Unicode 'DIGIT ZERO' (U+0030) to 'DIGIT NINE' (U+0039)) rather than superficially similiar Unicode symbols. <br/><br/>With *data-volume* the price is for each 1GB of data. |
| **billingDuration** | string  | options: instant, day, week, month, year  | **REQUIRED** Specifies for how long this price (or price component) will be billed. Can be used, for example, to model the contractual duration of a subscription or payment plan. |
| **unit** | string | One of: One-time-payment, Pay-per-use, Recurring, Revenue-sharing, Data-volume , Pay-what-you-want, Freemium, Open-data, Value-based, On-request | **REQUIRED** One-time-payment is for single time purchase purposes, further purchaces are not intended to continue under same agreement. <br/><br/> *Pay-per-use* is intended for continuous usage and price set is for each successful usage action. <br/><br/> *Recurrring* is intended for continuous time period plans. <br/><br/>*Revenue sharing* is a performance-based income model. An effective revenue sharing deal structure is offering your expertise to a business owner to help them grow their business. In return, you get paid a percentage of the revenue as a royalty fee. <br/><br/> *Freemium* is for free access. Use this option also for open data. <br/><br/> *Data-volume* is for data amount based pricing in which customer pays based on the served data amount. The price is always for 1GB of data. <br/><br/> *Pay-what-you-want*  is a pricing system where buyers pay any desired amount for a given commodity, sometimes including zero. In some cases, a minimum (floor) price may be set, and/or a suggested price may be indicated as guidance for the buyer. The buyer can also select an amount higher than the standard price for the commodity. If the floor price is set, use *minPrice* attribute. <br/><br/> *Open-data*  is an explicit pricing plan category for open data. By default open data should be free, but in some cases it can have a price. <br/><br/> *Value-based* is value-based selling unit. Present the outcome of your story with solid data and a measurable impact with help of *offering* attribute. Example: “We can lower the energy bill in heating by $8-13/square meter in a year. Try out simulator to calculate your value!”. Use optional *valueSimulator* attribute to provide link (URL) to value simulator you have created. In order to set base fee for value-based plan, you can for example set monthly (*billingDuration*) plan with base see with help of *minPrice* attribute. <br/><br/> *On-request* is for plans in which customer is given access to data product after contacting provider. Use provider contact information in providing means to contact data product provider for access permissions request.  |
| **maxTransactionQuantity** | Integer |  Integer | **REQUIRED** The maximum transaction quantity for the given billing duration. Use this to define for example monthly (or any other period) request limit to the data product. Note! If you want to set unlimited use, value must be 0 (zero). |
| **offering**  | string | array | **REQUIRED** The element that contains pricing plan content as array of strings. Think of this as the list of what is included in the pricing plan and what you offer in return to the price asked. Use the language defined in the *plan* |


## Provider

## Roles

## SLA 

## Stakeholders


