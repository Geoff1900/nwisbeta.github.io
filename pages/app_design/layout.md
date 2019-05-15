---
title: Layout
keywords: interface, design, navigation, search, access, display, default,
sidebar: appdesign_sidebar
toc: true
permalink: layout.html
folder: app_design 
---

## Principles

The app design must:

* Use a consistent layout across similar pages and components (WCAG 2.1, Material.io, iOS Human Interface Guidelines), including locations for menu item locations and button locations
* Provide navigation menus at the top and bottom of each page - see [Menus](/menus.html)
* Display the search bar at the top centre of each page - see [Search](/search.html), where a search facility is present
* Use a consistent layout for titles, headings, subtitles, body text - see [Typography](/typography.html)  

Consider and refer to layout standards, standard access points - see [Menus](/menus.html) and standard features - see [Standard Features](/standard-features.html). Default positions for features include:  
* Profile (top left)
* Settings (top right) 
* Home (bottom centre)

<div class="col-sm-12">
	<div class="row">
		<div class="col-md-6 col-lg-6" style="padding: 00px 10px 20px 10px;">
			<h3>Generic App Layout</h3>
			<img class="img-responsive img-thumbnail" src="/images/examples/design-standards-generic-layout.png">
		</div>
				
		<div class="col-md-6 col-lg-6" style="padding: 00px 10px 20px 10px;">
			<h3>Log In Page</h3>
			<img class="img-responsive img-thumbnail" src="/images/examples/design-standards-layout-login.png">
		</div>
	
	</div>
</div>			

 
## Columns for layout

The app design must use a central column, for those pages that do not display data, such as results. Pages with a list of items must have a single column with left text alignment.  The design should centre the most important data as a heading, where appropriate. 

When the app design uses columns to display information:
* Do not use more than two columns, on a page with portrait orientation  
* Information type, such as a field name, must appear in the left column  
* Relevant information, such as the field contents, must appear in bold in the right column  
* data fields must appear with only one data field on each row

Avoid a layout that requires a lot of scrolling. 

Do not display too much information on one page (WCAG 2.1, ICO, GDPR). The layout must:
* Display the most important information without scrolling (WCAG 2.1)  
* Avoid displaying more than ten data fields on a single page - see [Data Entry](/data-entry.html) 

If the interface requires more than ten data fields, use multiple pages.

The app design should use margins and spacing where possible (iOS Human Interface Guidelines, Material.io, UWP).

<div class="col-sm-12">
		<div class="row">

		<div class="col-md-6 col-lg-6" style="padding: 00px 10px 20px 10px;">
			<h3>Patient Information</h3>
			<img class="img-responsive img-thumbnail" src="/images/examples/design-standards-layout-patient-info.png">
		</div>
				
		<div class="col-md-6 col-lg-6" style="padding: 00px 10px 20px 10px;">
			<h3>Settings Menu</h3>
			<img class="img-responsive img-thumbnail" src="/images/examples/design-standards-layout-settings.png">
		</div>
	</div>	
