---
title: Data Entry  
keywords: methods, accessibility, content, layout, governance, fields, touch, speech, mic, 
sidebar: appdesign_sidebar
toc: true
permalink: data-entry.html
folder: app_design 
---

## Principles
The app design must provide multiple methods for entering data (WCAG 2.1), such as: 

* Onscreen keyboard
* Bluetooth keyboard
* Touch
* Speech  
  
Do not collect more than the minimum data required. Limit data collection to what is necessary (ICO, GDPR).   

Avoid asking for a person’s title (GOV.UK Design System).  

The data collection design must:
* Use required fields only when it is necessary to collect the information (iOS Human Interface Guidelines)
* Provide the simplest data entry method, to minimise the need for text entry (WCAG 2.1, iOS Human Interface Guidelines) 
* Present one data field only per row

Avoid displaying more than seven data entry fields on one page. For more than seven data fields, create multiple pages.  

Use pre-set options instead of free text where possible, including:
* Radio buttons
* Tick boxes 
* Pickers

### Text Fields
The data collection design must provide text boxes and fields only when users need to enter free text and no other option is effective. Free text fields must:
* Appear filled and outlined (Material.io)
* Include a label indicating what information is required (iOS Human Interface Guidelines)

The app design must:
* Automatically save text entry fields every 30 seconds
* Use dynamic validation to check input immediately after entry. (iOS Human Interface Guidelines)
* Provide secure text fields (hiding text behind dots) for fields requiring sensitive data, such as password or PIN
* Provide appropriately-sized text fields, depending on the information required from the user (GOV.UK Design System)

|Field contents | Field size|
|------------|------------|
|Email address | up to 254 characters, and valid email address entry (IETF)|
|UK postcode | up to 8 characters and a space (GOV.UK Design System)|
|Patient information | up to 50 characters |
|Health and care notes | up to 2000 characters |
|Password | unlimited characters - no maximum length |

### Data Entry Elements

See [Selection Controls](/selection-controls.html) for full guidance. 

The app design must use:
* Radio buttons to select a single option from a list: avoid pre-selecting radio buttons (GOV.UK Design System, Material.io)
* Drop-down menus or pickers to select from more than 10 pre-set options. 
* Checkboxes when the user can select one or multiple pre-set options from a list (GOV.UK Design System, Material.io)
* Toggle buttons to select between on/off options

For a long list of options such as selecting a country from a pre-set list, provide a clear indication that more options are available 'off screen', such as a downwards arrow icon.   

### Automated Entries

The app design must: 
* Automatically enter known information, such as date, time and location, to minimise user entry (WCAG 2.1, iOS Human Interface Guidelines)
* Provide appropriate default values - such as current time for data entry (iOS Human Interface Guidelines)
* Use dropdown/pickers to scroll through multiple pre-set values (iOS Human Interface Guidelines) 

For date entry, the app design must use a date picker: 
* 3 wheels must be used: date, month, year
* The Date must appear automatically if appropriate, such as with today's date
* Define whether a date picker can set future or past dates

For times, the app design must use a time picker: 
* Time must appear automatically if appropriate
* Define whether the time picker can set future or past times

## Information Governance
If Information Governance requirements state that all data changes must be tracked, then the user should have easy access to audit logs detailing data entries.    

Do not disable copy and paste unless required for clinical governance and data protection purposes (GOV.UK Design System). 

## Keyboards
Set the keyboard to the type of data entry required, to facilitate data entry and minimise errors (WCAG 2.1, iOS Human Interface Guidelines). For example the app design must use:
* Email keyboard for email fields
* Numerical keyboard for PIN input
* Default keyboard for all other fields
