---
layout: post
title:  "My First Post on GitHub Pages with Jekyll"
date:   2022-02-24 15:00:00 +0530
categories: howto
---

This first post describes the steps I followed to setup this site.

References
==========

* [GitHub Pages](https://pages.github.com/)
* [Set up Git](https://docs.github.com/en/get-started/quickstart/set-up-git)
* [GitHub CLI Installation on Ubuntu](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)
* [Jekyll on Ubuntu](https://jekyllrb.com/docs/installation/ubuntu/)
* [Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)

Prerequisites
=============

* Ubuntu Computer
* Account on Github

Setting up from scratch and Publishing your First Post
=====================================================

1. Head over to GitHub.com in your browser and create a new **public** repository named username.github.io, where username is your username (or organization name) on GitHub. If the first part of the repository doesn’t exactly match your username, it won’t work, so make sure to get it right. Look [here](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-a-repository-for-your-site) for screenshots. In my case this repo was https://github.com/lithiumhead/lithiumhead.github.io
2. Install and setup git on your Ubuntu Laptop to work with your GitHub account
    1. `sudo apt install git`
    2. `git config --global user.name "Anurag Chugh"`
    3. `git config --global user.email "me@email.com"`
3. Install Github CLI
    1. `curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg`
    2. `echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null`
    3. `sudo apt update`
    4. `sudo apt install gh`
4. Setup Github Authentication
    1. `gh auth login`
    2. Follow on screen instructions
5. Install Ruby
    1. `sudo apt-get install ruby-full build-essential zlib1g-dev`
6. Avoid installing RubyGems packages (called gems) as the root user.
    1. `echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc`
    2. `echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc`
    3. `echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc`
    4. `source ~/.bashrc`
7. Install Jekyll and Bundler
    1. `gem install jekyll bundler`
8. Create local repository, docs directory and branch
    1. `git init lithiumhead.github.io`
    2. `cd lithiumhead.github.io`
    3. `mkdir docs`
    4. `cd docs`
    5. `git checkout --orphan gh-pages`
    6. `git rm -rf`
9. Initialize new Jekyll Site
    1. `jekyll new --skip-bundle .`
10. Edit Gemfile
    1. Open the Gemfile that Jekyll created (`nano Gemfile`)
    2. Add `#` to the beginning of the line that starts with `gem "jekyll"` to comment out this line.
    3. In place of that, add line: `gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins`
    4. Replace `GITHUB-PAGES-VERSION` in the above line with the version number from [here](https://pages.github.com/versions/). (It was 223 on 2022-02-24)
    5. Save and close the Gemfile.
11. Run Commands:
    1. `bundle install`
    2. `git add .`
    3. `git commit -m 'Initial GitHub pages site with Jekyll'`
    4. `git remote add origin https://github.com/lithiumhead/lithiumhead.github.io`
    5. `git push -u origin gh-pages`
12. Configure GitHub Pages settings for your repo
    1. Open browser and goto [https://github.com/lithiumhead/lithiumhead.github.io/settings/pages](https://github.com/lithiumhead/lithiumhead.github.io/settings/pages)
    2. Under Source, change to `gh-pages`
    3. And folder to `/docs`
    4. Click Save
13. [https://lithiumhead.github.io/](https://lithiumhead.github.io/) should now work and show a “Welcome to Jekyll!“ Post
14. To add a post, create a markdown file for each new post in `lithiumhead.github.io/docs/_posts/` and commit and push to `gh-pages` branch.
    Each markdown file needs to have certain [front matter](https://jekyllrb.com/docs/posts/) for it to be parsed properly by Jekyll.
    Here are the raw content of the markdown file behind this very post:
    [https://github.com/lithiumhead/lithiumhead.github.io/raw/gh-pages/docs/_posts/2022-02-24-my-first-post.markdown](https://github.com/lithiumhead/lithiumhead.github.io/raw/gh-pages/docs/_posts/2022-02-24-my-first-post.markdown)
16. To test locally
    1. `bundle exec jekyll serve`
    2. Open [http://127.0.0.1:4000/](http://127.0.0.1:4000/) in Browser
17. To switch to a different theme check [this](https://pages.github.com/themes/) and [this](https://github.com/lithiumhead/lithiumhead.github.io/settings/pages)


