---
title: Search 
keywords: text, field, response, display, results, accessibility, 
sidebar: appdesign_sidebar
toc: true
permalink: search.html
folder: app_design 
---

## Principles 
If search functionality is required, it must:
* Allow users to find content by typing text into the search bar (iOS Human Interface Guidelines, Material.io)
* Provide a search bar at the top centre of each page, pinned to the top menu (iOS Human Interface Guidelines)

### Search Bar 
<img src="/images/examples/design-standards-navigation-search-input.png" style="max-width: 2000px">

### Generic Layout Showing Search Feature
<img class="img-responsive img-thumbnail" src="/images/examples/design-standards-navigation-search-search-example.png">

## Input
Search must be a free text field (iOS Human Interface Guidelines, Material.io).  

Voice search option should be available using the devices microphone for search (Material.io).  The microphone icon must indicate and action availability of voice search option.   
 
Users should have the option of changing the microphone icon and voice search functionality to a scanner/camera functionality.  The settings menu must provide the option to change the search icon functionality.  

Search input must remain in the search box, to enable the user to modify the search term, when the search tool presents results.  
  
A clear (X) button must appear in the search box (right) when a user enters a search term . This button must delete the search term in full (iOS Human Interface Guidelines).  

## Result Requirements

Search results:
* must appear directly below the search bar (Material.io, iOS Human Interface Guidelines)  
* must appear as a list (iOS Human Interface Guidelines)  
* must be selectable and must open in a new page  

Provide a back button (top left) after selecting a search result, to enable navigation back to the search results page.  
  
Search results should update in real-time, even as the user types.  As the user types, a list view must display potential search results directly below the search box, or show potential keywords that the user can search for.  

Five most recent search items should appear under the search bar when the user selects the search bar, to provide immediate search options (Material.io).

Five most relevant search items should appear, and update in real-time, under the search bar during the search input, to minimise data entry and provide immediate search results.  
  
Search results must show relevant results only and must hide irrelevant results.  

If the search finds no results, an error message must appear - see [Errors](/errors.html) - or the interface must suggest other search terms or results.  
