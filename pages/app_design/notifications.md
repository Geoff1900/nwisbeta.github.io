---
title: Notifications 
keywords: reminders, alerts, requests, external, push, email,
sidebar: appdesign_sidebar
toc: true
permalink: notifications.html
folder: app_design 
---

Notifications include messages like Reminders, Alerts, and Requests.  

## Features 
Avoid sending unnecessary notifications, alerts or requests (iOS Human Interface Guidelines).

The app design must:
* Send notifications only if action is required and the user has not yet performed the action
* Allow users to cancel or ignore non-critical notifications

Critical notifications must stop the user from using other parts of the app until they take action (iOS Human Interface Guidelines).  

Check Information Governance requirements to determine if the app must log all notification actions such as cancellation.

## In-app Notifications

Use in-app notifications for notifications, alerts and requests whilst the user has the app open.  

In-app notifications must appear in a pop up - see [Pop Ups](/popups.html).   

Users must be able to cancel or ignore non-critical notifications.   

Critical notifications must stop the user from using other parts of the app until they take action (iOS Human Interface Guidelines).  
  
## External Notifications

Use push notifications for high priority alerts, notifications and requests.  These notifications appear outside the app.

Re-send critical notifications within an appropriate period of time, if the notification requires action, and the user has not responded.

## Reminders

Reminders should be configurable by the user unless critical and easy to change in the settings menu.  

Email notifications can be used for reminders if required.
