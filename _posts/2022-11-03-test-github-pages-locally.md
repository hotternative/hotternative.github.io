---
title: "Test Github Pages locally"
date: 2022-11-03
---

Say you made some changes to your GitHub pages, commit and push. You then wait around 2 minutes to see the effect.
The feedback can be made much faster if we run the site locally. To do so:

Add a `Gemfile` to the root of the repo. In the file, have these as the minumum:
```
source "https://rubygems.org"
gem "minima", "~> 2.5"
gem "github-pages", "~> 227", group: :jekyll_plugins
gem "webrick", "~> 1.7"
```

In terminal:
```shell
eval "$(rbenv init -)"  
rbenv global 3.1.0    
bundle install  # this is required for the first time only
bundle exec jekyll serve
```

Reference: 
[docs.github.com](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)