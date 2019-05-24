---
title: Log in and Log out
keywords: login, logout, password, access, credentials, authentication, pin, timeout,
sidebar: appdesign_sidebar
toc: true
permalink: log-in-log-out.html
folder: app_design 
---

## Log In

The log in page must include:

* Central alignment
* NHS Wales logo, at top centre of the screen
* NWIS colour splash at bottom right of the screen
* The app name as a title, centred on the screen 
* The log in button
* Log in credential fields required for access  
* A single method of log in, with alternative methods to fall back on (iOS Human Interface Guidelines)

### Access Using Username or Email Address, and Password Authentication

<img class="img-responsive img-thumbnail" alt="Log In Using Username or Email Address, and Password Authentication" src="/images/examples/design-standards-access-login-app-name.png" caption="Generic app log in page enabling users to gain access to the app through authentication with their username/email address and password">

  
* Relevant icons must appear next to log in credential fields (see Tools > Icons)
* The appropriate default keyboard must enable data entry (iOS Human Interface Guidelines)
* Use dots to hide password characters, for password security (iOS Human Interface Guidelines)
* Biometric (fingerprint/facial recognition) log in should be supported, though not relied on, as a method of log in, as not all devices support this option (iOS Human Interface Guidelines)

The log in page must display a forgotten details message and a link for password reset. See [Messaging and Standard Messages](/messages.html) for sample messages wordings.

### Access Through an External Authentication Service

<img class="img-responsive img-thumbnail" alt="Log In Through an External Authentication Service" src="/images/examples/design-standards-access-login-forgotten.png">

## Log In After Session Timeout

The log in after session timeout page must include:

* NHS Wales logo at top middle of the screen 
* NWIS colour splash  at bottom right of the screen
* App name 
* Request for PIN or email and password, or biometric (fingerprint/facial ID) authenticated entry
* Dots to hide password characters, for password security (iOS Human Interface Guidelines) 
* Forgotten details message and link, if this reset method is available - see [Messaging and Standard Messages](/messages.html) for sample message wordings

### Failed Log Ins or PIN Entry

After a failed log in or PIN entry attempt, the application must log out the user, and return to the original log in page.

### Access After Timeout, with PIN Request for Re-authentication  

<img class="img-responsive img-thumbnail" alt="Log In After Timeout, with PIN Request" src="/images/examples/design-standards-access-login-pinexample.png">


## Log Out

The log out feature must:

* Have a button in settings (Material.io)  
* End session  
* Take the user to the log in page after selecting log out

