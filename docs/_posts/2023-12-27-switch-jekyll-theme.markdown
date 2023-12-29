---
layout: post
title:  "Switch the Jekyll theme on GitHub Pages from Minima to Modernist"
date:   2023-12-27 18:40:00 +0530
categories: howto
---

This post shows you how to switch the Jekyll theme on your existing GitHub Pages site

References
==========

* [Adding a theme to your GitHub Pages site using Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll)
* [List of themes supported on GitHub Pages](https://pages.github.com/themes/)

  * [Minima theme preview](https://jekyll.github.io/minima/)
  * [Modernist theme preview](https://pages-themes.github.io/modernist/)

Prerequisites
=============

* Your existing GitHub Pages repo cloned out on an Ubuntu Computer

Steps
=====

1. Open console and navigate to the `docs` sub-folder in your checked out repo (is `lithiumhead.github.io/docs/` in my case).
2. Open `_config.yml` for editing. Look for `theme: minima` and change it to `theme: jekyll-theme-modernist` and save the file.
3. Back at the bash prompt, run `bundle update` while still in the `docs` sub-folder.
   This will download all the themes supported by [GitHub pages](https://pages.github.com/themes/) locally to your computer.
4. Try to render existing posts locally by issuing `bundle exec jekyll serve`. You will get a build warning saying that the layouts for the types page, post and home are not known.  
   This is because if you look at the [GitHub repo](https://pages-themes.github.io/modernist/) for the modernist theme, you will realise that [_layouts](https://github.com/pages-themes/modernist/tree/master/_layouts) folder there only has default.html.  
   So at this point we can open the affected markdown files and switch the layout for each of them to default or we can supply the html files for the page, post and home layout types manually. We will try the latter.  
   Press ctrl+c to kill the server.
5. Copy the `home` layout files from the (_layouts)[https://jekyll.github.io/minima/tree/master/_layouts] folder of the minima theme:
   1. At the console while still in the `docs` sub-folder, issue `mkdir _layouts`
   2. `cd _layouts`
   3. `wget https://github.com/jekyll/minima/raw/master/_layouts/home.html`
6. For the `post` and `page` layout, let's just duplicate the `default` layout of the modernist theme, we can customize them later:
   1. `wget https://github.com/pages-themes/modernist/raw/master/_layouts/default.html -O post.html`
   2. `wget https://github.com/pages-themes/modernist/raw/master/_layouts/default.html -O page.html`
7. Edit home.html to use the theme
   1. Open home.html for editing and change
      ```
      ---
      layout: base
      ---
      ```
      
      to  

      ```
      ---
      layout: default
      ---
      ```
      
      and save.
8. Render locally
   1. Navigate one level up back to `docs` : `cd ..`
   2. `bundle exec jekyll serve`
   3. Open [http://127.0.0.1:4000/](http://127.0.0.1:4000/) in Browser


