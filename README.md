# Using the koru-jekyll theme

This is a theme based on UCAR/NCAR's custom 'koru' design. It is built on top the Foundation framework. This provides users and developers with responsiveness and accessibility. The site can be found [here](https://ncar.github.io/jekyll-koru-test/).

* [Layouts](#layouts)
* [Main Menu](#main-menu)
* [Local Development](#local-development)

## Layouts
### Default

The only front matter information required for default pages is:

```yml
---
layout:
title:
---
```

### Front page

Front matter options for the front page are:

```yml
---
layout:
title:
banner-title:
banner-description:
banner-button-text:
banner-button-url:
---
```

## Updating the main menu

The main menu is set in the mainmenu.yml file in the _data directory. Paths can be either absolute or relative in the menu. The structure for creating a menu is:

```yml
menu:
  - title: Software
    url: /pages/documentation.html
```

If you are using a relative path to a page in the repository you will need to include the repository name in the `url:` value. This would look like: `url: /jekyll-koru-test/pages/main-menu.html`

When developing locally, you will need to remove the repository name from the URL.

## Local Development

Run `docker-compose up --build` to (re)build the jekyll images and run the container.

This will create a container and mount your current repository directory on the container. The container runs `jekyll serve` and creates a local server environment in the container.

Any changes you make to your local repository will be made to the container. To see updates you will need to refresh your browser.

## Support

### Jekyll Docs
* [Getting Started](https://jekyllrb.com/docs/)

### Github Docs
* [Github Pages Basics](https://help.github.com/en/categories/github-pages-basics)
* [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
* [Repository metadata on Github](https://help.github.com/en/articles/repository-metadata-on-github-pages)

### Sphinx and Jekyll

Sphinx documentation will not display correctly if both Jekyll and Sphinx are in the /docs directory. This is due to Jekyll ignoring all directories that begin with an underscore.

### Feature Requests

If you have a feature you would like to see added to this template, please contact [SWES](mailto:swes@ucar.edu).