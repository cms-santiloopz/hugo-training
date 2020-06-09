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
