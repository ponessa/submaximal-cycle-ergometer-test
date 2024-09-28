---
title: Writing your document
permalink: /en/quickstart/writing-your-documents
abstract: >- # this means to ignore newlines until "baseurl:"
  Overview of the components of the markdown document that will become your project documentation.
---

## Overview
Below are step-by-step instructions on how to create a Jekyll page with the specified front matter and basic Markdown content:

1. **Create the directory**:

   Navigate to the `_docs` directory and create the folder as defined in the `docs.yaml`

2. **Create a New Jekyll Page**:

   In your Jekyll project directory, create a new Markdown file (e.g., `my-jekyll-page.markdown` or `my-jekyll-page.md`) for your page. You can do this in your code editor or via the command line.  Create the new file with the name as defined in the `docs.yaml`.

3. **Add Front Matter**:

   At the beginning of your Markdown file, add the front matter.  Front matter is an area at the top of your Markdown documents that lets you write variables and even content for your pages. It uses YAML, a simple and friendly serialization language, and it works well in combination with Liquid.

   Front matter is written with simple YAML variable, using a **key**: **value** notation, with a colon.

   Any file that contains a YAML front matter block will be processed by Jekyll as a special file. The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines. Here is a basic example with the fields you'll need.

   ```markdown
   ---
   title: Creating a Jekyll Page
   permalink: /jekyll-page/
   features:
     - mermaid
     - d3
     - rest
   abstract: This is a sample Jekyll page that demonstrates how to create content with front matter and a table of contents.
   ---
   ```

   - `title`: Set the title of your page.
   - `permalink`: Specify the URL path where the page will be accessible on your published site.
   - `features`: List the features relevant to the page.
   - `abstract`: Provide a brief summary or abstract for the page, which can be displayed on the documentation's landing page.

4. **Add Content**:

   After the front matter, you can start adding your content in Markdown format.  Markdown is a plain text format for writing structured documents, see [Markdown Overview](https://pages.github.ibm.com/IBM-Services-WFM/wfm-docs/en/learning-framework/markdown-overview){: target="_blank"} or [GitHub Flavored Markdown Spec (more detailed)](https://github.github.com/gfm/){: target="_blank"} You can use `#` for H1 and use `##` for H2 headings, and `###` for H3 headings, as shown in the example:

   ```markdown
   ## Introduction

   This is the introduction to our Jekyll page.

   ## Section 1

   This is the first section of our page.

   ### Subsection 1.1

   This is a subsection under Section 1.

   ### Subsection 1.2

   Another subsection under Section 1.

   ## Section 2

   This is the second section of our page.

   ### Subsection 2.1

   This is a subsection under Section 2.

   ### Subsection 2.2

   Another subsection under Section 2.
   ```

   - Use `{% raw %}{{ page.title }}{% endraw %}`  and `{% raw %}{ page.abstract }}{% endraw %}` to dynamically include the title and abstract defined in the front matter.

4. **Save the File**:

   Save the Markdown file in your Jekyll project's directory.

5. **Generate the Site**:

   To see your new page on your Jekyll site, run the command to generate the site. Typically, you can use the following command:

   ```
   bundle exec jekyll build
   ```
   or
   ```
   bundle exec jekyll serve
   ```

   This will generate the HTML files based on your Markdown content and front matter.

6. **View the Page**:

   After generating the site, you can view the page in your local development environment or deploy it to your web server to make it accessible to others.

These instructions will help you create a Jekyll page with the specified front matter and basic Markdown content, including H2 and H3 headings for your table of contents.

## Table of contents

Note that a side **table of content** will be automatically generated based on the headers used within the content.

![Side TOC]({{ site.baseurl }}/assets/images/docs/side-toc.png){: class="zoom" }