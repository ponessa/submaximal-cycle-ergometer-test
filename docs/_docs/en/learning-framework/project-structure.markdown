---
title: Project Structure
permalink: en/learning-framework/project-structure
abstract: >- # this means to ignore newlines until "baseurl:"
  An overview of the directory structure of the WFM documentation tool.
---

# Directory Structure

```
docs
├── _config.yml
├── _data
│   └── docs.yml
├── _docs
|   └── en
│        ├── user-defined-directory-1
│        |   ├── user-defined-file-1-1.markdown
│        |   └── ...
│        └── ...
├── _includes
│   ├── back-to-top.html
│   ├── breadcrums-versions.html
│   ├── contribute-selection.html
│   ├── footer.html
│   ├── head.html
│   ├── header.html
│   ├── logo.html
│   ├── navigator.html
│   └── toc.html
├── _layouts
│   ├── default.html
│   ├── docs.html
│   ├── home.html
│   ├── page.html
│   ├── post.html
│   └── search.html
├── _posts
│   ├── yyyy-MM-dd-name-of-post-1.markdown
│   └── ...
├── _site
├── assets
│   ├── css
│   ├── data
│   ├── images
│   ├── js
│   ├── post.html
│   └── search.html
├── fonts
├── .gitignore
├── 404.html
├── about.markdown
├── CONTRIGUTING.md
├── Gemfile          # Required to run Jekyll locally
├── Gemfile.lock
├── index.markdown
├── search.html
└── README.md 
```

Every file or directory beginning with the following characters: `.`, `_` , `#` or `~` in the source (`docs`) directory will not be included in the destination folder. Such paths will have to be explicitly specified via the config file in the include directive to make sure they’re copied over.

An overview of what each of these does:

| Directory or file | Description |
|-------------------|-------------|
| `_config.yml`     | Stores [configuration]({{site.baseurl | append: "/en/quickstart/initial-setup"}}) data.<br/> This  **YAML** file specifies various settings controlling how Jekyll generates the site. |
| `_data/docs.yml` | This **YAML** file contains the table of contents of the site. The user/publisher adds new topics/chapters and/or documents here. See [Adding Pages]({{site.baseurl | append: "/en/quickstart/adding-pages"}}) |
| `_docs/en` | This is where the user/publisher defines the directories (a.k.a., topics/chapters) and markdown content files.  Each of the markdown files will contain **front matter** that will contain the document's title and `permalink` (i.e., URL link) |
| `_includes` | These are the partials that can be mixed and matched by your layouts and posts to facilitate reuse. The liquid tag **&#123;% include file.ext %&#125;** can be used to include the partial in `_includes/file.ext`. The user/publisher should never need to touch the contents of this folder. | 
| `_layouts` | These are the templates that wrap posts. Layouts are chosen on a post-by-post basis in the front matter, which is described in the next section. The liquid tag **&#123;&#123;content &#125;&#125;** is used to inject content into the web page. The user/publisher should never need to touch the contents of this folder. |
| `_posts` | Your dynamic content, so to speak. The naming convention of these files is important, and must follow the format: `yyyy-MM-dd-title.MARKUP`. The permalinks can be customized for each post, but the date and markup language are determined solely by the file name.  |
| `_site` | This is where the generated site will be placed (by default) once Jekyll is done transforming it. It’s probably a good idea to add this to your `.gitignore` file. |
| `assets` | Set of static HTML assets such as `css`, `data` files, `images`, and `js` (JavaScript) files. |
| `index.markdown` <br/> `about.markdown` <br/> `404.html` <br/> `search.html` | Provided that the file has a **front matter** section, it will be transformed by Jekyll. The same will happen for any `.html`, `.markdown`, `.md`, or `.textile` file in your site’s root directory or directories not listed above |

Except for the special cases listed above, every other directory and file—such as `css` and `images` folders, `favicon.ico` files, and so forth—will be copied verbatim to the generated site. 

There are plenty of [sites already using Jekyll](https://jekyllrb.com/showcase/){:target="_blank"} if you’re curious to see how they’re laid out.
 

# Layouts within page structure

Below is an example of how the given `_includes` partials are combined to generate a page. The value here is that the user/publisher only needs to focus on the (green) **title**, **abstract**, and **content**, the resest of the formatting/presentation areas are handled by the tool. 

![Layouts within page structure]({{ site.baseurl }}/assets/images/docs/layouts-within-page-structure.png){:class="center zoom"}

Site search, navigation, document table of contents/navigation, feedback, contribution, issues, etc,. are all controlled by the tool.  Finally, the tool also handles print, excluding the navigation, headers, footers, etc., that should not be included in a printed version of the content. 

# Print layout

![print-layout]({{ site.baseurl }}/assets/images/docs/print-layout.png){:class="center zoom"}
