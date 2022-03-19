---
title: How to setup github pages with jekyll
tags: [jekyll, github-page]
---

## My work environment
- ubuntu

## Prerequisites
- github account

## Steps
1. Create **public** repository on github whose name is
    > \<username\>.github.io

2. Install required modules
    - Git
    - Ruby
    - RubyGems
    - Jekyll
    - Bundler

    Refer to [jekyll documents](https://jekyllrb.com/docs/installation/)

3. Choose your jekyll theme

    You can pick up a theme from [several websites](https://jekyllrb.com/docs/themes/#pick-up-a-theme).<br>

4. Initial setup

    1. Clone your public repository (from step 1) on your local environment.
    2. Download zip file of theme from github page.<br>
    (or clone/fork the repository if you want)
    3. Unzip, and paste files to your local repository.

5. Customize
    - Customize configs by modifying '_config.yml'.<br>
      - your name, email, github url, etc
    - Add some sample posts on '_posts'. (if you want to test)
    - Refer to README of your theme's github page for details.

6. Test locally

    On your root path of jekyll project, run
    ```sh
    bundle install
    bundle exec jekyll s
    ```
    and access localhost:4000

7. Push files to your remote repository

    Github action will be automatically triggered on your push by bot named 'github-pages'.<br>
    Check details on \[Actions\] tab on your public repository(from step 1)'s github page.

8. Browse to your github page whose url is
    > https://\<username\>.github.io
  
9. Customize more
    - Upload more posts
    - Enable posts' categories, tags
    - Enable comments on posts
    - Customize styles
    - etc
