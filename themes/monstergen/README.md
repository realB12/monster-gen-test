# MonsterGen Hugo Theme

`C:\me\ACTIVE\bsPUB\github.com\realB12\monster-gen-test\themes\MonsterGen\README.md`


the MonsterGen Hugo Theme generates all `*.md` Markdown files within the `/content` folder with all their associated ressources - such as pictures, CSS, PDF-files, etc. - into the `/public` folder.

Whereas above is normal HUGO procedure the MonsterGen Theme is less Hugo opiniated and does certain things slightly differently. 

## Examples
> Some examples of MonsterGen in action!

One of the best ways to see what MonsterGen can do, and learn how to configure a site with it, is to see some real projects. In addition to our provided MonsterGen Example Project, there are several live sites already using the theme. Please add your own examples once you’ve got a production site up and running with Docs. 

## Startpage

### MonsterGen Startpage
MonsterGen generated websites does not have a fix/static Homepage in a classical sense, but must **always be assigned a Startpage** - which can be any `*.md` file in the `/content` folder - either with the hugo command: 

    hugo --startpage "mySubFolder/myStartpage"

or within `config.yaml` 

    monstergen: 
    
      startpage: mySubFolder/myStartpage
    
The Startpage is the "first" page displayed when the user either types
    
* http://myWebSite.com   (the Root)  

* http://myWebSite.com/   (the Root) 

* http://myWebSite.com/home

* http://myWebStie.com/index

*  http://myWebStie.com/index.html

### Fallback Homepage
When either
- no startpage is indicated, 
- the indicated startpage cannot be found
- the startpage is set to "default"

then the normal HUGO Template Lookup Order is used for the evaluation of the homepage to be displayed (It is highly recommended to have one defined: normally )

Refer to the Hugo Docs n 
- on details how HUGO is [handling Homepages in general](https://gohugo.io/templates/homepage/) or 
- or the [Homepage specific Lookup Order](https://gohugo.io/templates/lookup-order/#examples-layout-lookup-for-home-page)





