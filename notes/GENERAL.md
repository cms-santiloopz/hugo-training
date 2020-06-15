# Notes

* Create new site  
```
$ hugo new site <sitename>
```

* Create new page  
```
$ hugo new {route/}<pagename>
```

* Serve site in localhost  
```
$ hugo serve <-D>
```
-D to see drafts pages

* Front matter
Metadata that Hugo generates for each site. It can be written in `yaml`, `toml` or `json`
```
---
title: "Landing"
date: 2020-06-09T01:28:02+02:00
draft: true
---
```
Front matter can be also made custom, with filds of your own that add some custom information of your own interest.

* How does Hugo organize content
It distinguished between two types of content: `single pages` and `list pages`.

* List pages
By default, Hugo creates list pages for root content folder and folders within the first level of depth in this folder, if you have nested pages you need to create an `index` file for it to have a list site.
```
hugo new dir1/dir2/<_index class="md"></_index>
```

* Archetypes
An archetype is basically a front matter template ready to be replicated and populate it's paramameter values with real data.

If you create an archetype whose name matches a directory, all pages created within that directory will have the front matter inherited from that archetype.

* Shortcodes  
Predefined chunks of HTML that you can add to your pages with a markdown, well, shortcode.  
The syntax is as follows:  
```
	{{ < shortcode-name param1 param2 > }}
```
 You can find more information on shortcodes in the [following page](https://gohugo.io/content-management/shortcodes/).

* Taxonomies
At the end of the day are frontend matter that add metadata on our content.
```yaml
tags: ['whatever']
categories: ['cagegory1']
```

When you create tags, on list pages you can list them to display a list of all the pages that contain that tag.

* Custom Taxonomies
We can create our arbitrary taxonomies.
```yaml
moods: ['happy', 'upbeat']
```
Since moods is not a default taxonomy in Hugo, the system isn't creating us a list page for moods as it does for categories and tags.

To register the new taxonomy, we must go to config.toml and write:
```toml
[taxonomies]
	tag = "tags"
	categoriy = "categories"
	mood = "moods"
```

* Layouts
They are the html skeleton of our Hugo site, when you use a layout, all the pages that extend from that layout will use their structure.

* How to override theme layouts?
In layouts folder, you create a now folder named `_default`

* Variables
To access the content of an md content file, we use `{{.Content}}` in out templates.
Variables can only be accessed in the `Layouts` folder and not in the `.md` files of the `content` folder.  
The syntax of a variable is as follows:
```
{{ .<VarName> }}
```
Some useful variables:
```
{{.Title}}
{{.Date}}
{{.URL}}
```
Also, you can create your own custom variables in the Front Matter and access them from the template. They can be accessed in the following way:
{{ .Params.<VarName> }}  
Furthermore, you can also create YOUR OWN variables in the template with the followig syntax:  
```
{{ $myVarName := "whatever" }}
```
To access it, later in the same template you can use
```
{{ $myVarName }}
```
More info on [variables](https://gohugo.io/variables/).  

* How do you create the Home page of your Hugo site?
Creating an `index.html` file in the root layouts folder.

* How to override the single or list templates for a specific dir (section)?
You need to replicate the dir structure in the Layouts folder and within this dir,
create the single and list templates.  
Also, in the front matter of your .md you HAVE to switch `type = <section name>` to the name of the section. In this case it would have been `type : "dir"`

* The `baseof` template is a Higher Level Template, which means every single page is going to implement it. You can see an example in about-to-rescue project. 

* Hugo Funtions
Can only be used inside the `layouts` folder. The syntax is as follows:
```
{{ functionName param1 param2 ... paramN }}
```
Examples of built in functions:
```
{{ truncate 10 "A really long string" }}
{{ add 10 5 }}
{{ subtract 10 5 }}
{{ singularize "dogs" }}
```
Loop through collection:
```
{{ range .Pages }}
	{{ .Title }}<br />
{{ end }}
```
To check a list of the available functions, you can come [here](https://gohugo.io/functions/).

* Hugo Conditionals
An example
```
{{ $var1 := "dog" }}
{{ $var2 := "cat" }}
 comparison operators
 eq	gt ge lt le not
{{ if eq $var1 $var2 }}
	// conditional rendering
{{ end }}
{{ else }}
	// else rendering
{{ end }}
```
Negating:
```
{{ if not(eq $var1 $var2) and ge $var1 $var2 or <another boolean> }}
{{ else if condition }}
```