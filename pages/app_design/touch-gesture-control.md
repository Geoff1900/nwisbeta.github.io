---
title: Touch Gesture Controls
keywords: menus, select, tap, scroll, swipe, pan, pinch, zoom, resize, elements, components, behaviour,
sidebar: appdesign_sidebar
toc: true
permalink: touch-gesture-control.html
folder: app_design 
---

Gestures must help users to navigate, take actions and manipulate content (Material.io).   

Gestures must be as easy as possible to carry out. Consider screen reader interaction modes - see [Accessibility](/accessibility.html) (WCAG 2.1). 
 
The app design must use standard and familiar gestures (iOS Human Interface Guidelines) including:
* Tap
* Scroll
* Swipe
* Pan
* Hold and drag   
* Pinch

## Single Tap 

Single tap gestures must allow navigation, perform actions, and make selection choices within the app (Material.io, iOS Human Interface Guidelines). 

App design must reveal the following functionality through a single tap gesture:

* Buttons, Menu items and Data fields: provides item selection
* Top or Botton menu items: provides navigation
* Bottom menu item: scrolls to top of page and refreshes data (if appropriate) 
* Top of screen: scrolls to top of page
* Action button: performs the action, such as log out 
* Text box: allows data entry
* Tick boxes: selects a Tick box
* Higher level components, such as top level patient information: reveals lower level components, such as patient contact details
 
## Scroll
Scroll gestures must allow navigation through continuous information (Material.io, iOS Human Interface Guidelines), including:  
* Lists and notifications
* Body text
* Lists of menu items, such as settings

Scroll gestures must only scroll through one view at a time – do not nest one scroll view within another, on one page (iOS Human Interface Guidelines).    

## Swipe 
Swipe gestures must allow navigation, and actions within the app, (Material.io, iOS Human Interface Guidelines) including:  
* Go back to previous page, using swipe right
* Transition across related categories on a single page - a sibling transition
* Reveal or complete action e.g. delete or acknowledge
* Move through a tutorial
* Swipe down to refresh
* 'Paging' through multiple tutorial pages
* Acknowledge a notification or alert
* Reveal delete button  

If a back button provides navigation to a previous page, the back swipe gesture must allow navigation to a previous pages, as an alternative method.
  
## Pan 
Pan gestures must allow users to move elements in any direction: for example, moving in any direction through map (Material.io)  

## Hold and Drag
The app design can use hold and drag gestures if required (Material.io, iOS Human Interface Guidelines): for example, hold and drag items on to-do list to change order.    

## Pinch
The app design can use Pinch gestures if required, to allow the user to zoom: for example, to zoom in on photo.  

## Icons
Icons can communicate the gesture available (Material.io), such as a refresh icon appearing when swiping down on a page, which remains visible until the refresh action is complete.
