---
title: Transitions 
keywords: navigation, categories, swipe, components, 
sidebar: appdesign_sidebar
toc: false
permalink: transitions.html
folder: app_design 
---

Transitions refers to users moving between screens, typically by swiping.  

Transitions must allow users to navigate across related categories on a single page by selecting category tabs (Material.io).  

Swipe gestures must allow user access across the related categories, such as moving between patient, ward or consultant lists. 

Transitions must move users from general to more detailed information, and return to general level, such as moving from patient general information to additional patient information, and back.   

Avoid transitions being too fast or too slow (Material.io):
* Transitions should not be faster than 100ms 
* Transitions should not be slower than 300ms 

Transitions must allow the user to reveal more detailed information if by expanding a higher level component to include lower level components and reinforcing that the components are related (Material.io):

The user must be able to minimise lower level components back to the higher category (original state): for example, when viewing additional patient information.

