---
title: Pop Ups   
keywords: action, response, confirm, delete, OK, cancel, error, 
sidebar: appdesign_sidebar
toc: true
permalink: popups.html
folder: app_design 
---
## Requirements

Pop ups must: 
* Require the user to act (Material.io)  
* Provide relevant and actionable information (Material.io)  
* Use consistent messaging see [Messaging](/messaging.html)
* Contain a heading (minimum bold 20 sp) and body text (minimum 14 sp)  
* Display one or two action buttons (Material.io) - see [Buttons](/buttons.html)

## Pop Up Message Syntax 

Pop up headings must provide a brief statement (Material.io) of up to four words relating to the pop up - see [Messaging](/messaging.html).

Pop up body text must provide a concise message (iOS Human Interface Guidelines), with a full stop or question mark at the end of the message (Material.io).

For example, provide a 'Are you sure?' pop up with yes/no options prior to submitting, changing or deleting critical data. Use this confirmation for critical data changes only, to avoid overuse (iOS Human Interface Guidelines).

When a pop up appears, use a transparent overlay to darken the background.

### Pop up Message with Action Buttons

<img class="img-responsive img-thumbnail" src="/images/examples/design-standards-user-interaction-popup.png">

Pop ups require a minimum contrast ratio of 3:1 between the pop up colour and colour of the screen behind the pop up (WCAG 2.1) - see [Accessibility](/accessibility.html).

To close a pop up, the user must select an action button (Material.io).

## Pop Up Text Standards

| Style   | Font Type | Font Size (em/rem) | Font Case | Font Emphasis |
|---------|-----------|--------------------|-----------|---------------|
| Heading | Calibri   | 16                 | Title     | Bold          |
| Body    | Calibri   | 14                 | Sentence  | Plain         |
