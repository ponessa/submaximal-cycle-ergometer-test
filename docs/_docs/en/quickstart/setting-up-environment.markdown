---
title: Setting up environment
permalink: /en/quickstart/setting-up-environment
redirect_from: /docs/home/
layout: docs
abstract: >- # this means to ignore newlines until "baseurl:"
  To get the framework up and running, we start with the code base on GitHub. The framwork itself are bodies of prewritten code used by developers to create documentation related to their project.
---

# Overivew

Welcome to our software project, aimed at standardizing product documentation through the use of GitHub Pages!

Documentation is an essential aspect of any product development cycle, as it provides users with critical information on how to use a product effectively. However, documentation can often be inconsistent or difficult to navigate, leading to confusion and frustration for users. This project aims to address this issue by providing a standardized platform for product documentation using GitHub Pages.

GitHub Pages is a free platform that enables the creation of simple, static websites that can be easily hosted and shared. By utilizing this platform, we can provide a consistent, user-friendly interface for product documentation that is easy to navigate and understand.

Our project will focus on creating a template for product documentation that can be easily customized to suit the needs of different products and industries. We will provide clear guidelines on how to use the template and ensure that it adheres to best practices for documentation. Additionally, we will offer support for maintaining and updating documentation, ensuring that it remains accurate and up-to-date.

Overall, our goal is to make product documentation more accessible and user-friendly for everyone. We believe that by utilizing GitHub Pages and providing a standardized template, we can achieve this goal and help improve the user experience for products across a wide range of industries.

## Pulling the GitHub repository

The following are the instructions to use this existing GitHub repository as the basis of a new documentation project:

1. Fork the repository
   1. Go to the [https://github.ibm.com/IBM-Services-WFM/wfm-docs](https://github.ibm.com/IBM-Services-WFM/wfm-docs){:target="_blank"}
   2. Click the "**Fork**" button in the top-right corner of the page. This will create a copy of the repository under your GitHub account.
   3. (Optional) One the repository is forked, if you want to change the name, you can do so under **Settings**

2. Clone the repository: Once you've forked the repository, you'll want to clone it to your local machine. To do this, navigate to the forked repository on your GitHub account, click the "Code" button, and then copy the HTTPS or SSH URL.

   Next, open up your terminal or command prompt and navigate to the directory where you want to store your new project. Once you're in the directory, use the `git clone` command to clone the repository:

   ```
   git clone <repository-url>
   ```

   Replace `<repository-url>` with the URL you copied from GitHub.

3. Create a new branch: Before making any changes to the code, it's a good idea to create a new branch. This way, any changes you make will be isolated from the main branch, and you can easily merge them back in later.

   To create a new branch, use the `git checkout` command with the `-b` flag:

   ```
   git checkout -b new-branch-name
   ```

   Replace `new-branch-name` with a descriptive name for your new branch.

4. Make your changes: Now that you have the repository cloned and a new branch created, you can start making your changes to the code. You can open up the code in your favorite text editor or IDE and make any necessary modifications.

5. Commit your changes: Once you've made your changes, it's time to commit them to your new branch. Use the `git add` command to add any new files or changes to your branch, and then use the `git commit` command to commit them:

   ```
   git add .
   git commit -m "Descriptive commit message"
   ```

   Replace "Descriptive commit message" with a brief message that describes the changes you made.

6. Push your changes to GitHub: Now that you've committed your changes to your local branch, you can push them to your forked repository on GitHub using the `git push` command:

   ```
   git push origin new-branch-name
   ```

   Replace `new-branch-name` with the name of your new branch.

7. Merge the brach back to **main** then **commit** and **push** merged main branch back to GitHub.  This will invoke the new publish process.

8. (**OR to push back to the original branch**) Create a pull request: Finally, you'll want to create a pull request to merge your changes back into the main branch of the original repository. To do this, navigate to your forked repository on GitHub and click the "Compare & pull request" button next to your new branch. 

   Give your pull request a descriptive title and description, and then click the "Create pull request" button. The original repository's owner will review your changes and decide whether or not to merge them into the main branch.

That's it! By following these steps, you can use this GitHub repository as the basis for a new project and start making your own modifications to the code.

## Telling new repository to use GitHub pages

Within your GitHub repository, go to **Settings** then scroll down to **GitHub Pages**.  When there, select the source to be the **main** branch and the directory to be `/docs`. 

![setup-repository-to-use-github-pages]({{ site.baseurl }}/assets/images/docs/setup-repository-to-use-github-pages.png){: class="zoom"}

[![go-to]({{ site.baseurl }}/assets/images/go-to.svg){: style="height:24px;" } open full image]({{ site.baseurl }}/assets/images/docs/setup-repository-to-use-github-pages.png){: target="_blank"}
 