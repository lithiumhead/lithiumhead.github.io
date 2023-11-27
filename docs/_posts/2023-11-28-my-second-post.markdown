---
layout: post
title:  "My Second Post on GitHub Pages with Jekyll"
date:   2022-02-28 02:20:00 +0530
categories: howto
---

This post shows you how to clone your existing repo that has been previously been setup to serve GiHub Pages and replicate the setup on a computer with freshly installed Ubuntu so that you can continue to add pages and publish to the same repo.

References
==========

* [My First Post]({% post_url 2022-02-24-my-first-post %})

Prerequisites
=============

* Ubuntu Computer
* Account on Github

Cloning your existing repo and recreating the environment
=========================================================

1. Install and setup git on your Ubuntu Computer to work with your GitHub account
    1. `sudo apt install git`
    2. `git config --global user.name "Anurag Chugh"`
    3. `git config --global user.email "me@email.com"`
2. Install Github CLI
    1. `curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg`
    2. `sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg`
    3. `echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null`
    4. `sudo apt update`
    5. `sudo apt install gh -y`
3. Setup Github Authentication
    1. `gh auth login`
    2. Follow on screen instructions
4. Install Ruby
    1. `sudo apt-get install ruby-full build-essential zlib1g-dev`
5. Avoid installing RubyGems packages (called gems) as the root user.
    1. `echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc`
    2. `echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc`
    3. `echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc`
    4. `source ~/.bashrc`
6. Install Jekyll and Bundler
    1. `gem install jekyll bundler`
7. Clone the repo
    1. `gh repo clone lithiumhead/lithiumhead.github.io`
8. Run commands
    1. `cd ~/lithiumhead.github.io/docs`
    2. `bundle install`
9. If your the version specified for gh-pages in your Gemfile is old, now is a good time to update it
    1. `nano Gemfile`
    2. Change the `223` in `gem "github-pages", "~> 223"` to the latest version thats specified [here](https://pages.github.com/versions/). (It was 228 on 2023-11-28)
    3. `bundle update`
    4. `bundle add webrick # Solves https://github.com/github/pages-gem/issues/752`
10. To render existing posts locally
    1. `bundle exec jekyll serve`
    2. Open [http://127.0.0.1:4000/](http://127.0.0.1:4000/) in Browser
11. To add a new post, just add a new markdown file to `lithiumhead.github.io/docs/_posts/` and then add, commit and push to gh-pages branch.

