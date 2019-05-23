---
title: Use Case Queries
tags: [NWIS_API, FHIR, use_case, code_sample]
keywords: demographic, diagnostic, sample, code, result, 
sidebar: api_sidebar
toc: true
permalink: diag_obs_reports_use_cases.html
folder: diag_obs_reports
---

## Use case on FHIR test server 

FHIR test server as a web interface [https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/) 

FHIR base URL: [https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3)

For each use case, append a query to this base URL.  
Building search queries through the FHIR server UI is a good way of learning how to construct URLs and client code as it provides both, together with the returned results.

The queries for finding patient records using demographic data or NHS number are covered in the [Patient Demographic Data API](pt_dmgrphc_landing_page).

### Retrieve a list of patient's test results

This query is a two-step process: obtain the `Patient` parameter `id`, which is distinct from the `Patient`'s `identifier` (their NHS number). In this example, the `id` is a number assigned by their (fictional) hospital. Then use the `id` in a `DiagnosticReport` query.

1. Use the `Patient` resource, with parameter `identifier` (the patient's NHS number) to find the the patient's `id`, as it appears in the XML/HTML response.  

   The example NHS number is 3795624164. 

   ```` 
   GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?identifier=3795624164
   ````

   [Web interface response for search for patient with NHS number](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/search?serverId=home&resource=Patient&param.0.0=&param.0.1=3795624164&param.0.name=identifier&param.0.type=token&sort_by=&sort_direction=&resource-search-limit)

   [Same result as HTML](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?identifier=3795624164)

   Sample of the HTML result: the `Patient` parameter `id` is 43
   ````html
   {
  "resourceType": "Bundle",
  "id": "c93a13fc-3a1a-4df8-a9dd-9dbc05473026",
  "type": "searchset",
  "total": 1,
  "link": [
    {
      "relation": "self",
      "url": "https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?identifier=3795624164"
    }
  ],
  "entry": [
    {
      "fullUrl": "https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient/43",
      "resource": {
        "resourceType": "Patient",
        "id": "43",
        "meta": {
          "versionId": "1",
          "lastUpdated": "2018-03-15T14:57:23.164+00:00"

   ````

2. Select the `DiagnosticReport` resource.  
Add the `patient` parameter, and enter the `id` from  previous query: 43.  


   ````
GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/DiagnosticReport?patient=43
   ````

   [Web interface response to DiagnosticReport query with patient id parameter 43](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/search?serverId=home&resource=DiagnosticReport&param.0.0=&param.0.1=43&param.0.name=patient&param.0.type=reference&sort_by=&sort_direction=&resource-search-limit
)  

   The list of results are ordered by `DiagnosticReport` id.  
   You can select and view an individual report from the web interface.  
   
   [Same response as HTML](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/DiagnosticReport?patient=43)



The C# code sample shows how to build a query, within a console application. [See Getting Started for package installation instructions](/apiguides_getting_started).

````c#
using System;
using Hl7.Fhir.Model;
using Hl7.Fhir.Rest;

namespace DHEW_DemoFhirConsole
{
    class Program
    {
        static void Main(string[] args)
        {            
            FhirClient client = new FhirClient("https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3");

            var patientId = "3795624164";
            var nhsNoSystemIdentifier = "https://fhir.nhs.uk/Id/nhs-number";

            // find a patient record based on NHS number
            Bundle reports = client.Search<DiagnosticReport>(new string[]
            {
                $"patient.identifier={nhsNoSystemIdentifier}|{patientId}"
            });

            Console.WriteLine($"There are {reports.Total} diagnostic reports for the patient");
        }
    }
}
````

### View a patient's single test result

Select the `DiagnosticReport` resource.  
Add parameter `_id` and enter the resource ID. Example value: 11011.  

````
GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/DiagnosticReport?_id=11011
````

[Web interface response for DiagnosticReport with single _id value](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/search?serverId=home&resource=DiagnosticReport&param.0.0=&param.0.1=11011&param.0.name=_id&param.0.type=token&sort_by=&sort_direction=&resource-search-limit)

[Same result in HTML](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/DiagnosticReport?_id=11011)


The C# code sample below illustrates how to build this query using the `DiagnosticReport` parameter `_id`.

````c#
DiagnosticReport diagnosticReport = client.Read<DiagnosticReport>("DiagnosticReport/11011"); Console.WriteLine(diagnosticReport.Text.Div);
````

This code writes a text summary of the resource to the console.

````
Laboratory number: 900012453904
Result/Report origin: Organization: 7A4 - Department: BSC

Urea and Electrolytes [Plasma] (Authorised[A])
Sodium                        140                   mmol/L          133-146
Potassium (Plasma)            4.0                   mmol/L          3.5-5.0
Urea                          4.0                   mmol/L          2.5-7.8
Creatinine                    175                   umol/L          58-110          H

eGFR and electrolytes (Plasma) (Authorised[A])
Sodium                        140                   mmol/L          133-146
Potassium (Plasma)            4.0                   mmol/L          3.5-5.0
Creatinine                    175                   umol/L          58-110          H
Estimated GFR                 38                    ml/min/1.73m2

Creatinine [Plasma] (Authorised[A])
Creatinine                    175                   umol/L          58-110          H

Estimated GFR (Plasma) (Authorised[A])
Creatinine                    175                   umol/L          58-110          H
Estimated GFR                 38                    ml/min/1.73m2
This is an estimate of GFR and is not valid in situations of rapidly changing serum creatinine. See www.renal.org for further information on this and other limitations of its use.

Urea and Electrolytes [Plasma]: Authorised by CAV: Rachel Brixey-McCann on 22/10/2018 at 12:40
eGFR and electrolytes (Plasma): Authorised by CAV: Rachel Brixey-McCann on 22/10/2018 at 12:40
Creatinine [Plasma]: Authorised by CAV: Rachel Brixey-McCann on 22/10/2018 at 12:40
Estimated GFR (Plasma): Authorised by CAV: Rachel Brixey-McCann on 22/10/2018 at 12:39
````

The report contains four results:

* Urea and Electrolytes
* eGFR and electrolytes (Plasma)
* Creatinine [Plasma] 
* Estimated GFR (Plasma) 

These results are expressed as FHIR `Observation` resources, which in turn reference other FHIR `Observation` resouces that represent the test result items such as Sodium, Potassium, Urea, and Creatinine. These 'nested' resources contain the actual result values e.g. 'Sodium     140     mmol/L'.   

The diagnosticReport.Results field contains references to the four 'top level' results.  

For simplicity, all the observations are included as 'contained' resources within the `DiagnosticReport` FHIR resource. [See the notes from H17 on contained resources](https://hl7.org/fhir/STU3/references.html#contained). 

This structure for a `DiagnosticReport` containing nested `Observations` follows [this example from the FHIR specification](http://hl7.org/fhir/STU3/diagnosticreport-example-ghp.html).

### Retrieve a series of a single test, to build a chart

This use case has two steps.

1. Retrieve all the sodium results for a patient, using Wales Results Reports Service (WRRS) code NA.  

   Select the resource `Observation`.  
   Add the parameters `patient` with resource id 43, and parameter `code` as NA.  
   
   ````
   GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Observation?patient=43&code=NA
   ````
   
   [Web interface response for query of Observation with two parameters](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/search?serverId=home&resource=Observation&param.0.0=&param.0.1=43&param.0.name=patient&param.0.type=reference&param.1.0=&param.1.1=NA&param.1.name=code&param.1.type=token&sort_by=&sort_direction=&resource-search-limit)
   
   The list of results are ordered by `Observation` id.  

   [Same result as HTML](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Observation?patient=43&code=NA)
   
   
   The C# code sample below illustrates how to display a patient's test result data, using their NHS number, and the WRRS observation code.

   The WRRS system is identified by the URI: [http://wrrs.wales.nhs.uk](http://wrrs.wales.nhs.uk)

   ````c#  
   var observationCode = "NA";  

   var wrrsSystemIdentifier = "http://wrrs.wales.nhs.uk";  

   Bundle sodiumObservations = client.Search<Observation>(new string[]  
   {
    $"patient.identifier={nhsNoSystemIdentifier}|{patientId}",  
    $"code={wrrsSystemIdentifier}|{observationCode}"  
	
   });

   foreach (var entry in sodiumObservations.Entry)
      {
       Observation sodiumObservation = entry.Resource as Observation;
       Console.WriteLine(((Quantity)sodiumObservation?.Value)?.ValueElement.Value);
   }
   ````


   The same search via URL:

   ````
https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Observation?patient.identifier=https://fhir.nhs.uk/Id/nhs-number%7C3795624164&code=http://wrrs.wales.nhs.uk%7CNA&_format=html/xml
   ````

   This code writes the patient's sodium result values to the console.  

2. Take these values along with the result dates to a graph for display to the user.


{% include links.html %}
