---
title: Errors  
keywords:
sidebar: appdesign_sidebar
toc: true
permalink: errors.html
folder: app_design 
---

## Principles
Error messages throughout the app must:
* Be relevant, understandable and actionable (Material.io)
* Explain what went wrong and how to fix it, in plain language (GOV.UK Design System, WCAG 2.1)
* Use consistent phrases - see [Messaging](/messaging.html)

Do not use technical language in error messages.

If an error message appears due to incorrect form entry, such as an invalid email address, the error message must explain in clear language what the error is, and provide the correct format for the entry.  

The app design should validate text entry in real-time (with helper text next to the text field) to notify the user before the user tries to move to the next step.  

Pop up error messages must only appear when a user tries to move to the next stage of a process, such as when submitting log in details with an error. This practice minimises interruptions to users when using the app (GOV.UK Design System).

If multiple errors occur simultaneously, the app design must present them in a single error message (GOV.UK Design System). Do not display a series of error messages that pop up one after the other.  

Do not use error messages that inform users they are not eligible or do not have appropriate permissions to do something. Rather, explain why they are not eligible, and what to do next (GOV.UK Design System).  

The app design must configure crash reports to go to developers, for error tracking (GOV.UK Design System). By default, hide detailed error messages intended for developers from users.  

## Layout 
* Provide a short text that fits on one or two lines (iOS Human Interface Guidelines)  
* Appear as a pop up with a heading (minimum bold 20 sp and body text (minimum 14 sp)  
* Use in sentence case - see [Typography](/typography.html)  

### Pop Up Error Message

<img class="img-responsive img-thumbnail" alt="Pop Up Error Message" src="/images/examples/design-standards-ui-errors-example.png">  
