---
title: Registration
keywords: password, data, display, consent, interface,
sidebar: appdesign_sidebar
toc: true
permalink: registration.html
folder: app_design 
---

## Passwords

If the app allows the user to self-register, the design must:
* Hide password characters behind dots for security (iOS Human Interface Guidelines)  
* Display a lock icon next to password field - see [Icons](/icons.html)  

## Non-essential Information 

The app must collect non-essential information after registration, using a walkthrough to set up the app, or through the user’s profile. The non-essential information may include:  
* NHS number
* Address
* Sex 
* Gender

## Display the App Terms and Conditions  
What terms and conditions appear during registration depends on the information governance policy.  Users must accept terms and conditions during registration.

The registration must:
* Display the mobile app terms and conditions
* Provide terms and conditions as a summary, and in full
   * A summary version is up to ten summary statements
* Provide tick boxes for each summary statement for the user to accept the terms and conditions
* Provide the terms and conditions statements in clear plain language. 

Designers must check the text using a reading age test, appropriate for the target audience. The reading level acceptable for clinical apps can differ from the level for patient apps. 

The app must send registration receipts in the same format as they were agreed on actual registration.

Consider email validation during the registration process. 

Any error message must appear immediately when a validation error occurs during registration, while the user is completing data entry (GOV.UK Design System) - see [Errors](/errors.html). Avoid displaying error messages after the user has submitted the form.

### Obtain Consent if Required

Consent (if appropriate) must follow the same process as for agreeing to terms and conditions. NHS Wales-led Information Governance rules decide whether consent is appropriate, and whether consent is integrated or separate from normal registration.  

Do not combine the process of registration, agreeing to terms and conditions, and providing consent on the same page. Treat these processes as separate, and present them on individual pages.  

### User Credentials Required for Registration

<img class="img-responsive img-thumbnail" alt="User Credentials Required for Registration" src="/images/examples/design-standards-access-registration1.png">

### User Credentials Required for Registration, Second Step

<img class="img-responsive img-thumbnail" alt="User Credentials Required for Registration, Second Step" src="/images/examples/design-standards-access-registration2.png">

### Terms and Conditions as a Summary and in Full, Final Step 

<img class="img-responsive img-thumbnail" alt="Terms and Conditions as a Summary and in Full, Final Step" src="/images/examples/design-standards-access-registration3.png">
