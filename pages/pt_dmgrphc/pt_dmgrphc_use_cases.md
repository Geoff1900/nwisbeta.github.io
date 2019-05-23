---
title: "Patient Demographic Data API: Use Case Queries"
tags: [NWIS_API, FHIR, use_case, code_sample]
keywords: patient, code, sample, family, 
sidebar: api_sidebar
toc: true
permalink: pt_dmgrphc_use_cases.html
folder: pt_dmgrphc
---

## Use case on FHIR test server 

FHIR test server as a web interface [https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/) 

FHIR base URL: [https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3)

For each use case, append a query to this base URL.  
Building search queries through the FHIR server UI is a good way of learning how to construct URLs and client code as it provides both, together with the returned results.

### Retrieve patient records by performing a patient demographic search

Select the `Patient` resource.  
Add the search parameters:  
* `family`: a portion of the family name of the patient. Value matches 'Davies'
* `address`: a server defined search that may match any of the string fields in the Address, including line, city, state, country, postalCode, and/or text. Value matches 'Pentre Bach'

````
GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?family=Davies&address=Pentre Bach

````

[Web interface response for `Patient` by family name Davies, `address` in Pentre Bach](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/search?serverId=home&_summary=&resource=Patient&param.0.qualifier=&param.0.0=Davies&param.0.name=family&param.0.type=string&param.1.qualifier=&param.1.0=Pentre+Bach&param.1.name=address&param.1.type=string&sort_by=&sort_direction=&resource-search-limit=&pretty=) provides client code, the request as a URL, the response header, and the result.

[Same response as HTML](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?family=davies&address=pentre%20bach&_format=html/xml)

This C# example shows how to search for patients with surname Davies, who live in Pentre
Bach, and iterate through the search results within a simple console application.

````c#
using System;
using System.Linq;
using Hl7.Fhir.Model;
using Hl7.Fhir.Rest;

namespace FhirTestClient1
 {
    class Program
    {
        static void Main()
        {
           // (1) Create a client object using the base URI of the FHIR API
           var client = new FhirClient("https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3");
           
           // (2) Perform a search for patients using demographic information. Search results are contained
           // within a 'Bundle' object. The searchResult.Total field indicates the number of results returned
           Bundle searchResult = client.Search<Patient>(new[]
               {
                   "family=Davies",
                   "address=Pentre Bach"
               }
            );
            
            // (3) Loop through the search results and print each patient's name and birthdata to the console
            for (int i=0; i < searchResult.Total; i++)
            {
                var myPatient = (Patient) searchResult.Entry[i].Resource;
                
                HumanName name = myPatient.Name.First();
                string familyName = name.Family;
                string givenName = name.Given.First();
                string title = name.Prefix.First();
                
                Console.WriteLine($"{familyName.ToUpper()}, {givenName} ({title});
                Console.WriteLine($"Born: {myPatient.BirthDate}");
            }
        }
    }
 } 
 
````


### Retrieve patient records by patient identifier

After selecting the `Patient` resource, the additional search parameter is

* `identifier`: A patient identifier, typically an NHS number. For this example value is 3795624126

````
GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?identifier=3795624126
````

[Web interface response searching for patient by NHS number](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/search?serverId=home&pretty=false&resource=Patient&param.0.0=&param.0.1=3795624126&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit=) provides client code, the request as a URL, the response header, and the result.

[same response as HTML](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?identifier=3795624126)


C# code sample and console application

````c#
using System;
using System.Linq;
using Hl7.Fhir.Model;
using Hl7.Fhir.Rest;

namespace FhirTestClient1
 {
    class Program
    {
        static void Main()
        {
           // (1) Create a client object using the base URI of the FHIR API
           var client = new FhirClient("https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3");
           
           // (2) Perform a search for patients using the patient's NHS number. 
           // The namespace 'https://fhir.nhs.uk/Id/nhs-number0' indicates an NHS number identifier
           Bundle searchResult = client.Search<Patient>(new[]
               {
                   "identifier=https://fhir.nhs.uk/Id/nhs-number|3795624126",
               }
            );
            
            // (3) Print each patient's name and birthdata to the console
            var myPatient = (Patient) searchResult.Entry[i].Resource;
                
            HumanName name = myPatient.Name.First();
            string familyName = name.Family;
            string givenName = name.Given.First();
            string title = name.Prefix.First();
                
            Console.WriteLine($"{familyName.ToUpper()}, {givenName} ({title});
            Console.WriteLine($"Born: {myPatient.BirthDate}");
            
        }
    }
 } 
 
````

{% include links.html %}