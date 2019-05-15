---
title: Getting Started with HAPI server
keywords: 
tags: [getting_started, FHIR, HAPI]
sidebar: api_sidebar
toc: true
permalink: apiguides_getting_started_hapi.html
folder: apiguides
---

## HAPI-FHIR server

The APIs on the HAPI server use the HL7® Fast Healthcare Interoperability Resources (FHIR®) specification. 

From the HL7® FHIR® [product brief](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=491):

> FHIR is an interoperability standard intended to facilitate the exchange of healthcare information between organizations. It consists of 2 main parts – a content model in the form of ‘resources’, and a specification for the exchange of these resources in the form of real-time RESTful interfaces as well as messaging and Documents.


This development is a test platform. The service must not be used or connected to any live system or service. 

[https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/)
 
{% include note.html content="The data within the service is test data and must not be considered or used for live use. While the API implements the full FHIR specification, it only contains the data for 100 fictitious patient records, and some representative data." %}

The service may be unavailable for maintenance.

## Features

On its FHIR resources, the HAPI server supports:

* multiple Search options
* option to view the resource update History 
* Validate operations
* Create, Read, Update, and Delete (CRUD) operations

From the home page, the HAPI server's interface makes some basic server actions a 1-click option including:

* retrieving the server's conformance statement
* retrieving the updated history across resource types
* posting a bundle and storing them, in a single actions
* showing all tags in use on the server

On its web interface, for every query you can view:

* client code you can copy to execute within your own client
* a copy of the request, with its headers - clicking 
* a copy of the response readers
* the result body, available as raw JSON, raw XML, HTML JSON, or HTML XML

## Endpoints

The HAPI server offers dozens of potential endpoints by enabling developers to build precise search queries and CRUD operations. 

The APIs featured use `GET` queries that can integrate into existing information-retrieval services. 

## Resources

This full implementation of FHIR includes all FHIR resources, though only some contain example data for testing. The resources appear in the interface showing number of entries.

The full implementation includes many parameters that are not needed for NHS Wales, such as the veterinary parameters.

Clicking any populated resource pulls up the resource's search and operations page, with search parameters and includes applicable to that resource.

See [`Observation` resource search page](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/resource?serverId=home&pretty=true&resource=Observation) as example. 

### Resources as a Swagger file
See [list of resources demonstrated in the use cases](/swaggerindex.html) displayed in the Swagger editor.

## Rate limit

No rate limit applied on this server: suitable for testing purposes only.

## Authentication  

No authentication steps required to access the test server.

## Authorisation

No authorisation steps required to access the test server.

## FHIR® libraries

### .NET
For this version of the test server, NWIS used a Microsoft .NET framework and wrote its sample integrations in C#. 

NWIS used the Hl7.Fhir.Specification.STU3 NuGet package, which provides client tools and functionality for working with the FHIR specification.

[Download package](http://ewoutkramer.github.io/fhir-net-api/)

[Read documentation](http://docs.simplifier.net/fhirnetapi/index.html)

To install the NuGet package to your .NET project, enter the following text in the Package Manager Console: 

````cs
PM> Install-Package Hl7.Fhir.Specification.STU3 -Version 0.94.0
````  

### Java 

[Java API for HL7® FHIR clients and servers](https://github.com/jamesagnew/hapi-fhir) 

### JavaScript

[SMART on FHIR® JavaScript client library](https://github.com/smart-on-fhir/client-js)

### Python

[SMART FHIR Client](https://github.com/smart-on-fhir/client-py)

{% include links.html %}