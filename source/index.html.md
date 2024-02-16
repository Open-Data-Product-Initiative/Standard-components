---
title: Open Data Quality of Service as Code (Open DataQoS as Code) | Open Data Product Initiative

language_tabs: # must be one of https://git.io/vQNgJ
- yml


toc_footers:
  - License <a href='https://creativecommons.org/licenses/by-sa/4.0/'>CC BY-SA 4.0</a>
  - <br/><a href='https://opendataproducts.org'>Specification home</a>


includes:
  - dataqos
  - conformity
  - completeness
  - helloworld
  - terms
  - contributors

search: true

code_clipboard: true

meta:
  - name: description
    content: The Open DataQoS as Code is a vendor-neutral, open-source machine-readable data product quality and service metadata model. It applies Everything as Code philosophy into the data products.  
---

# Open DataQoS as Code

## Experimental development version 

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “NOT RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in BCP 14 [RFC2119] [RFC8174] when, and only when, they appear in all capitals, as shown here.

The specification is shared under <a href='https://creativecommons.org/licenses/by-sa/4.0/'>Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)</a> license. Maintainer and igniter Jarkko Moilanen. 

### Backgroud in a larger research project 

This experimental specification is part of larger PhD research. About the research and news regarding Open DataQoS as Code can be found from <a href="https://medium.com/exploring-the-frontier-of-data-products">Medium publication "Exploring the Frontier of Data Products"</a>. 


**VERSION DETAILS**

**Version source:**

* <a href="https://github.com/Open-Data-Product-Initiative/DataQoS-as-code">https://github.com/Open-Data-Product-Initiative/DataQoS-as-code</a>



**Editors:**

* <a href="https://www.linkedin.com/in/jarkkomoilanen/">Jarkko Moilanen</a>


**Participate:**

* [Raise an issue in Github](https://github.com/Open-Data-Product-Initiative/DataQoS-as-code/issues)

## Introduction

**Data Quality of Service (Data QoS)** is a concept merging Data Quality (DQ) with Service-Level Agreements (SLA) created by Jean-George Perrin. It draws parallels from Quality of Service (QoS) in network engineering, which measures service performance. QoS criteria include packet loss, throughput, and availability. Data QoS addresses the complexity of measuring data attributes as businesses evolve. Inspired by Mandeleev’s periodic table, the author of Data QoS proposes combining Data Quality and SLA elements into a unified framework for better data observation. This approach aims to simplify data management amid growing business needs.

![Data QoS model by Jean-George Perrin](https://raw.githubusercontent.com/Open-Data-Product-Initiative/DataQoS-as-code/main/source/images/dataqos.png)

**Source:** <a href="https://medium.com/profitoptics/what-is-data-qos-and-why-is-it-critical-c524b81e3cc1">What is Data QoS, and why is it critical?"</a>. 


**Open Data Quality of Service as Code (Open Data QoS as Code)** in built upon the above concept and adds Everything as Code philosophy in it by adding "as code" aspect to it in order to enable monitoring. "Everything as Code" (EaC) is a development practice that extends the principles of version control, testing, and deployment, traditionally applied to software development, to all aspects of IT operations and infrastructure. This approach treats manual processes and resources—such as infrastructure provisioning, configuration, network setup, and security policies—as code. By doing so, it enhances repeatability, scalability, and security across the entire IT landscape. EaC allows for the automation of complex systems, making it easier to replicate environments for development, testing, and production purposes. It signifies a shift towards a more systematic, software-defined management of IT resources, aiming to improve efficiency, reduce errors, and increase the speed of deployment and operational task. 

### More information about Open Data QoS as Code

This experimental specification of Open DataQoS as Code is part of larger PhD research. More information about the research and news regarding Open DataQoS as Code can be found from <a href="https://medium.com/exploring-the-frontier-of-data-products">Medium publication "Exploring the Frontier of Data Products"</a>. 

## Specification aims and aspects

**Specification aims:**

* ...

**Note!** 'Open' refers to the openness of the standard. Any kind of connotations to open data (a different thing) are not intentional, intended, or desirable.


If you see something missing, described inaccurately or plain wrong, or you want to comment the specification, [raise an issue in Github](https://github.com/Open-Data-Product-Initiative/DataQoS-as-code/issues)

## Document structure

**LEFT COLUMN: Navigation**

The left column is navigation which enables fluent and easy movement around the specification. 

**MIDDLE COLUMN: Principles and components**

The middle column contains detailed information about the included components and related options. This is the theory part. 

Note! Mandatory elements and attributes are listed separately in the definition tables. This enables user to construct minimum viable specification more easily and fast. https://schema.org provided ready-made definitions are applied when ever possible instead of re-inventing the wheel. 

**RIGHT COLUMN: Examples**

The right column contains YAML formatted examples of how the specification is used. In the future other output formats are added on request basis. YAML can easily be converted to JSON if needed. 

> Example of YAML formatted snippet from the Open Data Product Specification:

```yml
monitoring:
  url: https://monitoring.com
```


<aside class="notice">
The YAML examples are not based on any real data product, but exemplify the usage of Open DataQoS as Code standard. 

</aside>



