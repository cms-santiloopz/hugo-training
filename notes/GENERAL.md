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