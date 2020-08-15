# Monster Generator Project :: REQUIREMENTS

---> [Project Summary](../_Monster_Generator.md)

## Project Carter
Use the [Hugo](http://gohugo.io) static Website generator to compile a website from any set of Markdown Monster edited, Markdown formatted `*.md` files in several layer deep directory structures, that reflects the requirements and constraints specified in the [requirements section](#) below. 

## Context

### Markdown at the base
MYRASIS - for all its open source projects - has decided to stick with [Markdown](https://en.wikipedia.org/wiki/Markdown "Wikipedia") formatted project documentation whenever possible, from where more sophisticated end-user/customer artefacts will be compiled in the whatever formats (MS Word, PDF, Powerpoint, ...) are needed.   

So for our company, **Markdown has become THE lingua franca for all kinds of content creation** and has demonstrated over and over again that this approach - with the right skills ans tooling in place, is saving big on gained project setup and delivery speed, cross-organisational compatibility, clarity, reusability, searchability and after all highliy increased internal and external productivity. 

### Markdown Monster Editor
Our tool of choice is [Westwind's Markdown Monster](https://markdownmonster.west-wind.com/) which from our perspective is great when weaving larg scale documentation sets with a lot of pages referring to each other and pages  with pictures, Source-Code Viewers, extended tables, native HTML and other stuff the goes beyond the limitations of pure Markdown-standard.

### Limimtations
Working locally with Markdown Monster - even on remote hosted GitHub Repos - is a breeze. Especially for two things: 

1. **Referring to other docs is by their `*.md` file-names** and relative path to the source-document. So withing Monster, clicking such links will open the linked document in editing mode (which is great), but will fail in the hugo generated HTML-pages (as the links in those generated files are still referring to `*.md` files rather than their *.html counterparts)

2. In the Monster Editor the **Physical file&folder-structure is used as Sidebar Project Navigation** which is not auotmatically generated in the Website.   

3. In Hugo, **ressource files** like pictures, PDFs, CSS-files etc. must either be in a separate `/static` or `/assets` folder and/or the Hugo project must follow the rules for [page-bundles](https://gohugo.io/content-management/page-bundles/) to make sure, that those resources will become part of the generated website and links are working.   
  
Along our projects **various authors have their resoures organized their way** and therefore the Generator must not assume specific locations - like the `/static` or `/assets` folders - for them, and therefore must "copy" whatever is "hyperlinked" in the `*.md` files.

## Scope
Current scope is the **compilation of a static Website for PC-size screens that from a GUI perspectives mimics the Monster Editor in read only mode**:  

This includes collapsable Tree-View-Navigation bars that
a) on the left side reflects the project's file and folder structure 
b) on the right side displayes the table of contents  

Generation of other targets such MS Office Documents or PDFs is out of scope but will be addressed in a next iterations. 

## TestCase
MYRASIS has published a Monster created set of files that with a simple hugo command must be "transformed" into a Website with all links, navigation, file- and fulltext search working. 
Find the GitHub Repository on 

## Requirementslist

### Monster GUI Mimikry
Assuming the Monster-project's root-folder to be the  `/content` folder of a Hugo Project, the `hugo`, and `hugo server` commands must generate the required website in the `/public` folder, which - without additional manual intervention - **mimics the look of the standard Markdown Monster Editor GUI** in read-only mode (the generated Website is static, read-only, no editing required).    
This includes the generation 
  
a) of the project's **file&folder structure** as (Monster-like) collapsible tree view on the left **side of the screen**
  
b) of the **Table of contents on the right side of the screen** (different from Monster).   

Special focus must be on keeping all hyperlink-functionality working in the displayed content and naviation menues - or in short: **when links to other *.md files and ressources such as PDFs, graphics etc.  work in Monster,  it must work with their generated (*.html) counterparts in the Website without further manual interventions**!

![](xPic/MonsterEditorSimple.png)

Find details on Monster-Editor and free Test-version under https://markdownmonster.west-wind.com/

All those aspects are outlined in more detail in the following sections

#### Generated Hyperlinks
All relative hyperlinks in source `*.md`-files - relative and absolute - must "work" in the generated website as well, including source-links to other `*.md` files (that will in the target website be hugo-converted into `*.html` files), external URLs, pictures and other ressources such as `*.pdf` or Microsoft Offices Docs (Excel, Word, etc.) - regardless of their relative position in the source-folders (e.g. one cannot assume that ressources are put into the `/static` folder or that page-bundles are used).

Anchors and internal Table of Contents (content referring to specific sections) must work in the website as well (inside the page and when referring to anchors of other pages). Same for the item-links in the folder-navigation tree on the left and the TOC-tree on the right. 

### Monster-like Side-barMenu
**Monster's Sidebar-Nav-Menu must be 1:1 mirrored** in the generated WebPage including `*.pdf` and Microsoft-Office-files with the exceptions of Pictures, Videos and other ressources that are only used in the context of another content-file but - in the website's nav-bars - must not appear as navigational/viewable files.

"Mirroring" here means 
  
1. **visually** (idents, folders and filetype icons, collapsing mechanics)   

2. **functinally** in a sense, that clicking a menu-icon will open the corresponding *.html files in the same and other-formatted files (PDF, XLSC, etc.) in a new Browser tab (or locally installed Viewer or MS-Office-Apps). 

Note here, that all such navigational aids must ge GENERATED from the existing files and must not be manually added or updated!  

### Search
All the generated website must be searchable. Should a 3rd-party tool be required, all such required content for this tool must be auto-generated and loaded into the tool/search-engine. 

### Source-Code viewer
Monster provides specific embedded viewer functionality for displaying code for various language format: html, go, js, css, ...    

Similar viewers need to be included for the generated website. 
### Hugo Shortcode Support
When using Hugo Shortcodes in Monster, they must be reflected in the resulting Website as well.

### Deployable
The such generated Website must be deployable on plain-vanilla Cloud-Infrastructure (currently we are using IBM Cloud and Microsoft Azure hosting). 

Suggstion and tips for a fully integrated CI/CD workflow with a provider of your choice is welcome (might be used for acceptance-testing)

### Environment
Current focus for content development is Windows 10 Pro Workstations and for Production and local testing we are using actual versions of Google Chrome and MS Edge Browsers in English and Swiss-German settings.

### Hugo only implementation
All should be implemented with whatever Hugo provides out of the box and should be agnostic to specific Hugo versions. All should be done with normal configuration options without modifications of the Hugo source Code or installation of third party tools or referring to third party services. 

### Focus on funtionality not style
It would be nice to have to mimic the Monster style, but not required. Switching between light and dark mode would be nice, but not required as well.     
However, the solution must not restrict options that would allow us to further pimp the look with HUGO standard tooling. 
Having full functinality workin the standard Chrome Browser is good enough for a first iteration where easy and ev. commercial "theming" of the solution might be part of a follow up project. 

### Must perfrom
Generation cycles should not delay HUGO's overall performance. For the given [Monster Template Source](#TestCase) the hugo generation must remain - on an average workstation - below 2 seconds. 

### Must remain Open Source owned by us
All the solution must remain open source and will 100% be owned by us. You can use it for your internal projects but all rights concerning public publishing and servicing the solution remains 100% with Baron Solutions Switzerland (might go to govy.swiss or Myrasis in the long run). 

## Relative URLs

For how relative Links are generally treated in the Hugo-Framework --> see the [Relative Links Doc](HugoRelLinks.md)

### Related Properties
* **`canonifyURLs=true`**
* **`relativeURLs=true`**
* **`uglyURLs=true`** 


### Intro
In the current Markdwon documents all relative Link URLs are relative to the document they are written in and are referring to the original `*.md` files - are so called **relative md/md-Links**. 
**Example**:

This is a relative hyperlink as we at BS are normally using it in our Monster-edited Markdown documents: 

`test.md`
        
    go to [this the Dummy Site](../dummy/dummy.md)

### the Challenge 

Use of such in-document relative-links is getting hairy when such files are generated for two reasons: 

1. The output folder-structure and filenames are different 
2. The targets are no longer *.md files but *.html

This brings us to the question, this manual is trying to solve.   

**How can we use the Monster/Hugo Combo most efficiently** that we may keep the realtive md/md links in Monster as is, but still can ensure, they will continue to work once generated with Hugo. 

### Solutions
There are fourh major roads towards the target. 
1. [Hugo configuration](#hugo-configuration)
2. Hugo (re)programming
3. Middleware
4. Monster pimping

#### Hugo Configuration
Hugo - out of the box - provides a ton of configuration features. This is the simplest, most cost effective approach that might still work over time. 
However, the disadvantage here is that this approach is a brittle one,  that requires   

1. **Discipline** from authors to work tightly standardized folder and file structures and naming conventions  

2. **Deep dive Hugo knowledge** when things do not work (without any alerst nor error-messages) and need to be fixed
3. 


## Related Links and Articles

* [Some notes on Relative URLs](https://discourse.gohugo.io/t/canonifyurls-relativeurls-interaction/5448)
