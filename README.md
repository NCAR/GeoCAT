# Using the koru-jekyll theme

This is a theme based on UCAR/NCAR's custom 'koru' design. It is built on top the Foundation framework. This provides users and developers with responsiveness and accessibility.

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

## Main menu

The main menu is set in the mainmenu.yml file in the _data directory. Paths can be both absolute and relative in the menu. The structure for creating a menu is:

```yml
menu:
  - title: Software
    url: /pages/documentation.html
```

## Local Development

To download koru-base from Artifactory, you will need to add your Artifactory credentials to a .env file. First, you will need to retrieve your credentials with the following command:

```sh
curl -u [username]:[password] http://<ARTIFACTORY_SERVER_DOMAIN>:8081/artifactory/api/npm/auth
```

Then copy the `_auth` and `email` strings into a .env file. The structure should be:

```
AUTH=[token]
EMAIL=[email address]
```

Run `docker-compose up --build` to (re)build the node.js and jekyll images and run the container.