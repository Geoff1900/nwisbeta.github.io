---
title: "Tools and requirements to build GitHub Pages"
keywords: 
search: exclude
tags: 
permalink: README_GitHubPages_tools_requirements.html
summary: An outline of software, publishing tools and skills required to document Health APIs.
---

## Respository for NHS Wales Informatics Service: Software development

[GitHub Organisation repository](https://help.github.com/en/articles/about-organizations): nwisbeta  

nwisbeta is a free repository: it is public, with unlimited membership.

See also [Permission levels for an organization](https://help.github.com/en/articles/permission-levels-for-an-organization).

The GitHub Pages for this repository are at https://github.com/nwisbeta/nwisbeta.github.io 

The resulting website: http://nwisbeta.github.io

The site runs on Jekyll, a Ruby software gem, and uses a [Jekyll documentation theme](https://idratherbewriting.com/documentation-theme-jekyll/) designed by Tom Johnston.


## Software setup required to build and maintain GitHub Pages

* obtain full permissions to download and run software on the local machine
* set up a GitHub personal login, and join organization account (nwisbeta)
* download and install the following tools, using instructions on their sites:
  * Notepad++ https://notepad-plus-plus.org/ as tool to build the site on the laptop
  * Git for Windows https://gitforwindows.org/ to upload content to GitHub. GitBash provides command line interface
  * Jekyll for Windows, using RubyInstaller and Bundler https://jekyllrb.com/docs/installation/windows/

You do not need another copy of the documentation theme, unless you are building a new site from scratch, in a new repository.

## Jekyll

If you have not used Jekyll before, [see the Jekyll website for a ground-up intro](https://jekyllrb.com/tutorials/convert-site-to-jekyll/#what-is-a-jekyll-website).

**TL:dr**: 
* create content: mainly text in kramdown Markdown. Add images or data. Save content in appropriate folders  
* run a local copy of Jekyll on your desktop using the command line interface, to check how the site appears and displays
* after error checks, commit and push the content to the repository

Jekyll creates the HTML versions of the pages, following the instructions in the theme to provide the layout, formatting and navigation. **You do not edit any HTML manually.**

## Documentation theme notes

The nwisbeta.github.io site is set up following the documentation theme instructions. Some features are not yet in use but are available for future iterations.

Most content controls used on the nwisbeta site (for editing headers, footers, top and side navigation) appear in:

* _config.yml
* _data/topnav.yml
* _data/sidebars/api_sidebar.yml (for H-API content)
* _data/sidebars/appdesign_sidebar.yml (for App Design standards)
* _data/sidebars/appdesign_tools_sidebar.yml (for App Design tools: the design phases and checklists)
* _includes/footer.html

From the GitBash window, run Jekyll locally to preview pages in your browser at 127.0.0.1:4000/

You *must* run Jekyll from the root of nwisbeta.github.io directory on your local machine. If you try to run the Jekyll command from another directory, it will generate errors.

The best way to make significant changes to the site is to create a branch in GitHub, and work on the branch locally, before committing the work and submitting a pull request to merge your changes to the master branch. See [About branches](https://help.github.com/en/articles/about-branches) on the GitHub site. 

## Adding new content to the site

This process requires:

* a GitHub account
* basic familiarity with Git commands
* the software tools described in the technical setup, installed on your local machine

1. Clone the nwisbeta site from GitHub, to your local machine.  
   https://github.com/nwisbeta/nwisbeta.github.io.git 

   If you are working in a branch, set up the branch following Git commands or [use the GitHub interface to create a branch](https://help.github.com/en/articles/creating-and-deleting-branches-within-your-repository).  
   
   If you already have a local copy of the site, pull a current version of the repository using Git commands.
      
2. In Notepad++, open the nwisbeta.github.io folder as a workspace.

   From Notepad++ you can edit existing files and save changes locally.

3. Use the GitBash command line interface to add and commit changes, using Git commands.  
 
4. View your changes **before** pushing them to the repository (and making them live) by running Jekyll in the commandline: `bundle exec jekyll serve`.  View the site in your browser at 127.0.0.1:4000/

5. Push content to the repository.

For new entries in the side navigation (like a new API): 

1. In the command line, use `mkdir` under /pages to create a new directory.

2. Create new content within the directory, saved as .md files, using kramdown Markdown. 
   Use a previous .md file as an example for the frontmatter, changing the file paths for the new content. Jekyll requires the frontmatter to create the HTML versions of pages correctly. 

3. In _data/sidebars/api_sidebar.yml, add the new directory as an entry in the side navigation. Pay attention to the syntax and indentation for the entry. Every indent space matters.

4. Save files. Add and commit using Git commands. 

5. Run Jekyll locally to check the pages appear correctly before pushing to the repository.

### For branches: submit a pull request

Pull requests 'pull' new content from a branch into the master copy. GitHub does the hard work of checking to ensure the new content doesn't conflict with the existing copy. For written content, a conflict is something like 'the two copies of this file refer to different sidebar YML files'. 

After pushing content from your local copy to the GitHub server, go to https://github.com/nwisbeta/nwisbeta.github.io, select the branch you're working on, and select 'New pull request'.  Follow the instructions on the page.

See [About pull requests](https://help.github.com/en/articles/about-pull-requests) for details.

## Undoing errors

Git has powerful tools for undoing errors. The two used so far in this project are `Revert`, and checking out an individual commit from a past pull request.

### Revert

Revert undoes a pull request. This feature is useful if, for instance,  you want to apply recent changes in `master` to a branch, but accidentally apply branch changes to `master`.

It doesn't matter if it is a recent request or not, though older pull requests will require more fixes to merge into work again.

The `Revert` button appears at the bottom of the list of commits in a pull request. 

See [Reverting a pull request](https://help.github.com/en/articles/reverting-a-pull-request).

### Checking out a specific commit

Git never truly deletes any content; it holds *all versions of content* forever.  This feature means that past versions of your work are still available in past commits and pull requests.

You can use `checkout` and a commit's hash number (the 7-digit hex number which identifies every commit) to check out specific files from past commits. This feature is useful if you accidentally overwrite content, realise the mistake later, want to resurrect your specific files, but do not want to revert a large pull request with all its committed changes.

1. Find your commit by browsing through the closed pull requests. Each commit has a unique hash. Click the hash to view the changes you want to undo.

2. On your desktop, in a clean branch:

`git checkout <commit hash> /path/to/your/file.md`

You can enter multiple file paths with a single space between each, in a single checkout.

The files will appear in your local repository.

3. Enter `git status` to confirm you've retrieved the correct files. They will appear as added, and ready to commit.

4. Edit files as needed, save, and run locally (on the desktop) to test them. 

5. Commit and push to the repository branch as usual.

## Open source comments and corrections

On the nwis.github.io pages, each page includes an 'Edit Me' button. The button links to a 'reviews_feedback' branch on the nwisbeta.github.io repository.  

Editing files requires a GitHub account.  

See [Commenting on files](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_commenting_on_files.html) in the Jekyll template documentation. 

As the site runs on an open-source repository, any GitHub account holder can also fork a copy of the site, in their *own* accounts. They can add comments or corrections to the text, commit them, and send a pull request. The pull request appears in the nwisbeta repository.

Only collaborators with admin permissions on the nwisbeta repository can approve pull requests (ie publish changes). 

Not yet tested: how GitHub handles edits submitted by collaborators with non-admin permissions.

## Adding Swagger UI display of the HAPI server's OpenAPI spec document

[Peter Evans' Swagger GitHub Pages](https://github.com/peter-evans/swagger-github-pages) provide instructions on how to set up the Swagger UI within your site. 

@velsietis provided some content to run on the UI: 
* used a script to extract an OpenAPI specification from the Pyro server, as a JSON file. This is a demo for what the HAPI server spec would look like, as a full implementation of the FHIR standard. 

* tailored it further to provide the spec only for the resources featured in the HAPI server use cases, rather than the entire FHIR standard. 

@eabrown3 edited the file further using the [Swagger Editor](http://editor.swagger.io/) to include only parameter descriptions that apply to the resources in use.

Following the instructions from Peter Evans, the Swagger UI is available from the 'Getting Started' page.

## References

* https://idratherbewriting.com/documentation-theme-jekyll/index.html (Documentation theme using Jekyll, by Tom Johnston)
* https://jekyllrb.com/docs/installation/windows/ (Install Jekyll, the Ruby gem, on Windows)
* https://kramdown.gettalong.org/quickref.html (Quick reference for kramdown syntax)
* https://help.github.com/categories/github-pages-basics/ (GitHub Page help)
* https://git-scm.com/doc  (Git documentation)
* https://notepad-plus-plus.org/  (Download Notepad++)
* https://chris.beams.io/posts/git-commit/ (How to write a clear, helpful Git commit message)
* https://github.com/peter-evans/swagger-github-pages (How to add the Swagger UI to your GitHub-hosted documentation)