---
title: Overview
permalink: en/learning-framework/solution-overview
abstract: >- # this means to ignore newlines until "baseurl:"
  This project is a lightweight documentation site builder that uses Markdown files to generate documentation pages, and configured with a single YAML configuration file.  It provides a customizable, responsive user interface that is optimized for both desktop and mobile devices. The documentation is kept along with the produce and hosted for free on GitHub Pages. 

---

Documentation is an essential aspect of any product development cycle, as it provides users with critical information on how to use a product effectively. However, documentation can often be inconsistent or difficult to navigate, leading to confusion and frustration for users. Our project aims to address this issue by providing a standardized platform for product documentation, stored in the same GitHub repository as the produce code, using [GitHub Pages](https://pages.github.com/){:target="_blank"}. 

GitHub Pages is a free platform that enables the creation of simple, static websites that can be easily hosted and shared. By utilizing this platform, we can provide a consistent, user-friendly interface for product documentation that is easy to navigate and understand. 

Our project will focus on creating a template for product documentation that can be easily customized to suit the needs of different products and projects. Providing templates and using these templates to build the site effectively separates **content** from **presentation**. This allows content authors to focus on their content ONLY. They don't need to worry about fonts, formats, CSSs, or screen readers.  Additionally, **markdown** provides a simple syntax that allows authors to write content using plain text with simple markup to add formatting and structure. 

Finally, this framework encourages product code and documentation to live within the same repository. Maintaining and updating documentation in the same repository with the product code helps ensure that the documentation remains accurate and up-to-date. 

Overall, our goal is to make product documentation more accessible and user-friendly for everyone. We believe that by utilizing GitHub Pages and providing a standardized template, we can achieve this goal and help improve the user experience for products across the IBM Consulting Workforce Managment portfolio.

## Separating content from presentation

When publishing a website, separating content from presentation has several advantages:

1. **Improved flexibility**: By separating content from presentation, you can create a more flexible and adaptable website that can easily be updated and changed without affecting the underlying content. This allows you to modify the website's design and layout without having to rewrite or restructure the content, saving time and effort.

1. **Easier maintenance**: Separating content from presentation makes it easier to maintain and update the website over time. You can modify the website's design and layout independently of the content, making it easier to fix issues or make improvements without having to touch the content itself.

1. **Improved accessibility**: Separating content from presentation can improve the accessibility of your website, making it easier for users with disabilities to access and use the content. By structuring the content in a logical and semantic way, and using CSS to control the presentation, you can ensure that the website is easily navigable and readable for all users.

1. **Faster load times**: Separating content from presentation can improve the load times of your website. By keeping the content separate from the presentation, you can minimize the amount of code that needs to be loaded, reducing the size of your web pages and improving their performance.

1. **Improved SEO**: Separating content from presentation can also improve the search engine optimization (SEO) of your website. By structuring the content in a logical and semantic way, and using CSS to control the presentation, you can ensure that search engines can easily crawl and index your website, improving its visibility and ranking in search results.

Overall, separating content from presentation can provide numerous advantages when publishing a website, including improved flexibility, easier maintenance, improved accessibility, faster load times, and improved SEO.

## Storing product technical documenation in same repository as product code

Storing product documentation in the same GitHub repository as the product code and publishing the documentation using GitHub Pages offers several benefits:

1. **Centralized and version-controlled documentation**: By storing the product documentation in the same repository as the product code, you can ensure that the documentation is always up-to-date and in sync with the codebase. Additionally, version control systems like Git allow you to track changes to both the code and the documentation over time, making it easy to roll back changes or review historical versions of the documentation.

1. **Simplified collaboration**: Storing the product documentation in the same repository as the code makes it easy for developers and technical writers to collaborate on the documentation. They can use the same tools and processes for version control, code review, and issue tracking, streamlining the development process and improving overall collaboration.

1. **Seamless deployment**: GitHub Pages makes it easy to publish static websites, such as product documentation, directly from a GitHub repository. By storing the documentation in the same repository as the code, you can streamline the deployment process and ensure that the documentation is always up-to-date and available to users.

1. **Improved discoverability**: Storing product documentation in the same repository as the code and publishing it using GitHub Pages can make it easier for users to discover and access the documentation. They can navigate to the repository for the product code and find the documentation easily, rather than having to search for it on a separate site or platform.

Overall, storing product documentation in the same GitHub repository as the product code and publishing it using GitHub Pages offers numerous benefits, including centralized and version-controlled documentation, simplified collaboration, seamless deployment, and improved discoverability.

## Architectural Overview

The diagram below shows the flow and tools that are used in this soltuion.  As the user promotes (`git push`) changes to GitHub, at the same time the updated code goes through the CI/CD pipeline to deploy the updated application, the documentation is projecssed with Jekyll and published on GitHub pages.

[GitHub Pages](https://pages.github.com/){:target="_blank"}, [Jekyll](https://jekyllrb.com/){:target="_blank"}, and the [Shopify Liquid template language](https://shopify.github.io/liquid/){:target="_blank"} make it easy to create and host a static website. 


![solution-architecture]({{ site.baseurl }}/assets/images/docs/solution-architecture.png){:class="center zoom"}


**GitHub Pages** is a static site hosting service that allows you to publish your website directly from your GitHub repository. It is a great way to host a simple website or blog without having to worry about managing a server.

**Jekyll** is a static site generator that is written in Ruby. It takes your Markdown and HTML files and converts them into static HTML files that can be hosted on GitHub Pages. Jekyll also has a number of features that make it a powerful tool for creating websites, such as support for Markdown, Liquid templating, and a variety of plugins.

**Liquid** is a templating language that is used by Jekyll to generate dynamic content on your website. It allows you to insert variables, loops, and conditionals into your Markdown files. Liquid also has a number of filters that can be used to manipulate the text of your website.