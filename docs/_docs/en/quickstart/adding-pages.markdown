---
title: Adding Pages
permalink: /en/quickstart/adding-pages
abstract: >- # this means to ignore newlines until "baseurl:"
  Overview of how to add pages to the `docs.yaml` file so that they are incorporated into the finished static website.
---

## Defining the structure of the documentation

For each project we need to define an outline. This outline acts like a table of contents (TOC) and provides a hierarchical list of the sections or chapters in the documentation. It serves as a roadmap to help readers navigate the content and locate specific information quickly and easily.

A well-structured TOC allows readers to get an overview of the organization and scope of the document, including its major sections and subsections. It provides a clear outline of the content and helps readers to find the information they need, without having to scan through the entire document.

Overall, a well-designed table of contents is an important tool for making documentation more user-friendly, and can greatly enhance the reader's experience.

## Documents YAML file

Although `docs.yaml` is not a standard file used by Jekyll, it is common to use a file with a similar name to define documentation-related metadata for a project. For this documenation project `docs/_data/docs.yaml` contains the structure of the documentation.  Therefore, before you can add a new section or document to your documentation package, you need to update **docs.yaml**.  

The docs.yaml file contains a list of `title`s, that act as chapters or sections.  Thereafter, there is a `docs` element that contains a list of documents.  These document values must match the directory structure under the `_docs` folder, with the last entry being the name of the markdown file within the given directory (without the `.markdown` extension).  For example, `en/quickstart/setting-up-environment` means that there should be a document file `setting-up-environment.markdown` in the `_docs/en/quickstart` directory.  **Note** that the `en` prefix is positioning the framework to support multiple languages.  

Finally, this directory structure does not drive the URL structure of the static documentation site. The URL paths are defined in the **front matter** of the documents themselves, associated with the `permalink` attribute (and will be covered next).

An example of the `docs.yaml` is below.

<pre name="code" class="js">
- title: Quickstart
  docs:
  - en/quickstart/setting-up-environment
  - en/quickstart/initial-setup
  - en/quickstart/adding-pages
  - en/quickstart/writing-your-documents

- title: Learning the Framework
  docs:
  - en/learning-framework/solution-overview
  - en/learning-framework/document-structure
  - en/learning-framework/markdown-overview
  - en/learning-framework/running-locally-with-jekyll
</pre>
