---
title: Running Locally with Jekyll
permalink: /en/quickstart/running-locally-with-jekyll
abstract: >- # this means to ignore newlines until "baseurl:"
  You can build your GitHub Pages site locally to preview and test changes to your site.
---

## Prerequisites
Before you can use Jekyll to test a site, you must:

- Install [Jekyll](https://jekyllrb.com/docs/installation/){:target="_blank"}.
- Create a Jekyll site. For more information, see "[Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/enterprise-server@3.3/articles/creating-a-github-pages-site-with-jekyll){:target="_blank"}."

We recommend using [Bundler](http://bundler.io/){:target="_blank"} to install and run Jekyll. Bundler manages Ruby gem dependencies, reduces Jekyll build errors, and prevents environment-related bugs. To install Bundler:

1. Install Ruby. For more information, see "[Installing Ruby](https://www.ruby-lang.org/en/documentation/installation/){:target="_blank"}" in the Ruby documentation.
1. Install Bundler. For more information, see "[Bundler](https://bundler.io/){:target="_blank"}."

**Tip**: If you see a Ruby error when you try to install Jekyll using Bundler, you may need to use a package manager, such as [RVM](https://rvm.io/){:target="_blank"} or [Homebrew](http://brew.sh/){:target="_blank"}, to manage your Ruby installation. For more information, see "[Troubleshooting](https://jekyllrb.com/docs/troubleshooting/#jekyll--macos){:target="_blank"}" in the Jekyll documentation.

## Building your site locally

1. Open Terminal.

2. Navigate to the publishing source for your site, in this case the `/dosc` folder. For more information, see "[Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/enterprise-server@3.3/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site){:target="_blank"}."

3. Run `bundle install`.

4. Run your Jekyll site locally (`bundle exec jekyll serve`).

<pre name="code" class="js">

$ bundle exec jekyll serve
> Configuration file: /Users/octocat/my-site/_config.yml
>            Source: /Users/octocat/my-site
>       Destination: /Users/octocat/my-site/_site
> Incremental build: disabled. Enable with --incremental
>      Generating...
>                    done in 0.309 seconds.
> Auto-regeneration: enabled for '/Users/octocat/my-site'
> Configuration file: /Users/octocat/my-site/_config.yml
>    Server address: http://127.0.0.1:4000/
>  Server running... press ctrl-c to stop.

</pre>

5. To preview your site, in your web browser, navigate to [http://localhost:4000](http://localhost:4000).

**Note**: If you've installed Ruby 3.0 or later (which you may have if you installed the default version via Homebrew), you might get an error at this step. That's because these versions of Ruby no longer come with `webrick` installed.

To fix the error, try running `bundle add webrick`, then re-running `bundle exec jekyll serve`.

## Updating the GitHub Pages gem

Jekyll is an active open source project that is updated frequently. If the `github-pages` gem on your computer is out of date with the `github-pages` gem on the GitHub Pages server, your site may look different when built locally than when published on GitHub Enterprise Server. To avoid this, regularly update the `github-pages` gem on your computer.

1. Open Terminal.
1. Update the `github-pages` gem.
    - If you installed Bundler, run `bundle update github-pages`.
    - If you don't have Bundler installed, run `gem update github-pages`.