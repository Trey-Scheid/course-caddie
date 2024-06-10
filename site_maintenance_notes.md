# Notes for myself on site upkeep
Last updated June 2024

Followed guidance from [Github Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) using [Jekyll Tutorial](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)

## How it was created
1. Github Repo
    1. Used the name I wanted to be the url (short catchy and descriptive)
    1. Created a new branch called gh-pages (I think this name defaults to turning sites on and deploying, but you can manually enable this from settings with any other name choice by selecting this branch)
1. cloned to desktop (I used some other remote function not git clone but they are functionally the same afterward)
1. locally made sure I had ruby and bundler using -v
1. ```mkdir docs```
1. ```cd docs```
1. ```bundle init``` (use --path?) 
1. ```bundle add```
1. Site files generated using Jekyll ```bundle exec jekyll new --skip-bundle .``` (maybe used force flag as well)
1. update gem file ```gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins``` (check [here](https://pages.github.com/versions/))
1. Update .gitignore at some point too with .bundle folder and the 
1. Change _config.yml theme to bulma (may have ran bundle install again to get the appropriate gems)

## Making Updates
Make changes to files locally.

Preview Changes by viewing the site on a local server using: ```bundle exec jekyll serve``` (clean and build can be used for the _site folder which is rendered)

To push you changes
1. cd to docs folder
1. ```git status``` check for any pulls
1. ```git add .```
1. ```git commit -m ""```
1. ```git push origin gh-pages```

## Customization
[jekyll info](https://jekyllrb.com/docs/themes/#overriding-theme-defaults) (and more on [Jekyll](https://kinsta.com/blog/jekyll-static-site/))

[Bulma Docs](https://www.csrhymes.com/bulma-clean-theme/docs/getting-started/theming/) easier ways to customize

More Bulma info [here](https://bulma.io/documentation/components/tabs/)

[Font Awesome](https://docs.fontawesome.com/web/style/lists) for icons

## How it works
Front matter (top of the file in the --- of .md files) is used to give pages metadata including their links and using presets from bulma. 