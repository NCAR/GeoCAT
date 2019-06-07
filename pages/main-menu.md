---
layout: default
title: Main Menu
---

## Updating the main menu

The main menu is set in the mainmenu.yml file in the _data directory. Paths can be both absolute and relative in the menu. The structure for creating a menu is:

```yml
menu:
  - title: Software
    url: /pages/documentation.html
```

If you are using a relative path to a page in the repository you will need to include the repository name in the `url:` value. This would look like: `url: /jekyll-koru-test/pages/main-menu.html`

When developing locally, you will need to remove the repository name from the URL.