# Blockchain Certificates Web Site

This repo contains the source for the [Blockchain Certificates Web Site](http://www.blockcerts.org). It is based on the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/).

## How to add documentation

- content is written in markdown, located in the _docs folder
- note that file headers in the markdown files. These are used by jekyll when generating the site:

  ```
  ---
  title: "Page title"
  sitemap: true
  permalink: /docs/my_link/
  ---
  ```
  
- The main page content is located in _includes/index.md
 
# Site layout

The most common site layout changes you'll want to make are to navigation menus; see _data/navigation.yml.

For other changes, consult the [Minimal Mistakes Technical Documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/).

# Rebuilding the site

To regenerate the site after you've made changes, run the following:

```
bundle exec jekyll build
```

To preview the site locally, run:

```
bundle exec jekyll serve
```

Note: the first time you do either, run bundle install as follows:

```
bundle install
```
