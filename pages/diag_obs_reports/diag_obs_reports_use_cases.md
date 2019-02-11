---
title: Use Case Queries
keywords: 
sidebar: mydoc_sidebar
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

1. Use the `Patient` resource, with parameter `identifier` (the patient's NHS number) to find the first part of a GET request in a URL.  

The example NHS number is 3795624164. In this case, the format of the results is XML.

```` 
GET https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Patient?identifier=3795624164&_format=xml
````

Using the `DiagnosticReport` resource base query, add the `patient.identifier` parameter (the NHS number) with value 3795624164 to the URL.  
In this example, the result format is html/xml.

````
GET  https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/DiagnosticReport?patient.identifier=3795624164&_format=html/xml
````

[Response to DiagnosticReport query with patient identifier parameter in html/xml format](https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/DiagnosticReport?patient.identifier=3795624164&_format=html/xml)

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

### View a patient's test result

The C# code sample below illustrates how to view a patient's test result using a DiagnosticReport id, which will have been retrieved using the previous call.

````c#
DiagnosticReport diagnosticReport = client.Read<DiagnosticReport>("DiagnosticReport/11011"); Console.WriteLine(diagnosticReport.Text.Div);
````

This code writes a text summary of the resource to the console.

````
Laboratory number: 900012453904
Result/Report origin: Organisation: 7A4 - Department: BSC

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

For simplicity, all the observations are included as 'contained' resources within the DiagnosticReport FHIR resource - see the notes on contained resources [URL:https://hl7.org/fhir/STU3/references.html#contained](https://hl7.org/fhir/STU3/references.html#contained). 

This structure for a DiagnosticReport conaining nested `Observations` contained within the report is based on this example from the FHIR specification  [URL: http://hl7.org/fhir/STU3/diagnosticreport-example-ghp.html](http://hl7.org/fhir/STU3/diagnosticreport-example-ghp.html).

### Chart a patient's test result data

The C# code sample below illustrates how to chart a patient's test result data. In this example, we'll retrieve all the sodim results for the patient using the code NA. 

This code is Wales Result Report Service code, and this system is identified by the URI: 

[https://fhir.nhs.uk/Id/nhs-number](https://fhir.nhs.uk/Id/nhs-number)

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

This code writes the patient's sodium result values to the console.  

These values values can be taken along with the result date to a graph for display to the user.

The same search via URL:

````
https://dhew.wales.nhs.uk/hapi-fhir-jpaserver-example/baseDstu3/Observation?patient.identifier=https://fhir.nhs.uk/Id/nhs-number%7C3795624164&code=http://wrrs.wales.nhs.uk%7CNA&_format=html/xml
````

{% include links.html %}