---
title: Initial Setup
permalink: /en/quickstart/initial-setup
abstract: >- # this means to ignore newlines until "baseurl:"
  Overview of the documentation package's configuration file.
---

# The configuration file

The Jekyll configuration file `_config.yml` is a **YAML** file that specifies various settings for a Jekyll site. This file is located in the root directory, and it controls how Jekyll generates the site.

The purpose of the Jekyll configuration file is to define parameters such as the site title, the URL of the site, the default layout to use, and various other settings. These settings are used by Jekyll to generate the final HTML files for the site.

Some settings that can be configured in `_config.yml` include:

- **title:** the title of the site.
- **description**: a short description of the site.
- **url**: the URL of the site.
- **baseurl**: the base URL of the site.
- **permalink**: the permalink structure for posts and pages.
- **contact_reference**: the URL for the documentation's contact user or slack channel.
- **markdown**: the Markdown processor to use (default is `kramdown`).
- **theme**: the name of the theme to use.
- **plugins**: a list of plugins to use.
- **organization**: Organization, e.g., CIO, WFM, CDO
- **twitter_username**, **github_username**: Twitter or GitHub user name for contact pages.
- **max_abstract_length**: The maximum length of an abstract on the home landing page. If an abstract is longer than the maximum length, the home landing page will only show the abstract up to that length, followed by an ellipse. The default is 100 characters.
- **footer_links**: Array of links to add to the footer of the pages.  E.g., 
<pre name="code" class="js">

footer_links: [
  {"title": "Terms", "url": "https://w3.ibm.com/#/info_terms_of_use"},
  {"title": "Privacy", "url": "https://w3.ibm.com/w3-privacy-notice"},
  {"title": "WFM Home", "url": "https://w3.ibm.com/w3publisher/ibm-services-workforce-management"}
]

</pre>

By modifying these settings in `_config.yml`, you can customize the behavior and appearance of your site to meet your specific needs.

To validate YAML, [YAML Validator](https://codebeautify.org/yaml-validator){:target="_blank"}
