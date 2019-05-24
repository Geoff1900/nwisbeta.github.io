---
title: Data Display   
keywords: governance, layout, fields, clinical,
sidebar: appdesign_sidebar
toc: true
permalink: data-display.html
folder: app_design 
---

The app design must:

* Display data consistently
* Use consistent values
* Use SI units as default, like metres, kilograms, litres - see [Typography](/typography.html) 

## Patient Information Formatting

For clinical apps, the app design must:
* Provide three pieces of identifiable information to identify a patient, such as patient name (first and last name), NHS number, DOB (age)  
* Display the patient's last name in uppercase (all capitals) to clearly distinguish it from the first name (NHS Common User Interface) 
  * Example: SMITH, John (M) 943 476 5919 03/04/56 (62yrs) (NHS Common User Interface)

Clinical apps must accommodate long names and addresses. For example:
* If the patient has a long first name, the last name, first name initial, title, NHS number and DOB must appear as a default
  * Example: TREETAWTCHAIW…, L (M) 943 476 5919 03/04/56 (62yrs)  
* If the patient has a long last name, then cut off last name with an ellipsis (…) at the text limit, prioritising first name initial, title, NHS number and DOB.  
  * Example: TREETAWTCHAIW…, L (Sir) 943 476 5919 03/04/56 (62yrs)
* If the patient has a long address, use ellipsis (…) to cut off at the text limit
  * Example:
    Llanfairpwll Health Centre
    Siglan TerraceFfordd Penmynydd
    Llanfairpwllgwyn…
    LL61 5YZ

Avoid collecting titles - see [Data Entry](/data-entry.html).  If collected, display the patient's title, in brackets to distinguish it from the last name and first name (NHS Common User Interface). 

Do not display more information than is required (ICO, GDPR).

The app design must ensure additional non-essential information is accessible by expanding a higher level component to reveal lower level components - see [Gesture Control](/touch-gesture-control.html) and [Pop Ups](/popups.html).

### Clinical App with Patient Information

<img class="img-responsive img-thumbnail" alt="" alt="Clinical App with Patient Information" src="/images/examples/design-standards-ui-patient-info.png">

## Patient Results
Only show recent or relevant patient results to avoid display of inaccurate/misleading information (GDPR, ICO).
  
The app design must show results only on the appropriate screen size. If the device screen cannot accommodate results, provide an error message telling the user to use another device to view the results. See [Messaging and Standard Messages](/messaging.html).
