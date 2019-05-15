---
title: Information and Clinical Governance  
keywords: GDPR, gdpr, confidential, confidentiality, data, access, privacy, protocol,
sidebar: appdesign_sidebar
toc: false
permalink: information-clinical-governance.html
folder: app_design 
---

Do not display more information than is required (ICO, GDPR).  

The app design must make additional non-essential information available by expanding a higher-level component to reveal lower level components - see [Gesture Control](/touch-gesture-control.html) or pop up - see [Pop Ups](/popups.html).

Collect only required information (GOV.UK Design System, ICO, GDPR).  

The app design should update data every 10 minutes to ensure data accuracy (ICO, GDPR).  

The app design must 
* Log notifications
* Provide easy access to audit logs detailing data entries and user activity
* End sessions, with a timeout, after 10 minutes of inactivity
* Store data securely during transit and at rest
* Autosave text entry fields on the app every 30 seconds

The app design should automatically save data entry fields, periodically, to prevent data loss (WCAG 2.1).  
  
The app design must: 
* Highlight the difference between medical information and patient information to users
* Label non-clinical information clearly next to the data field name - for example: 
   * Patient Information (Non-Clinical)
