---
layout: default
title: Local Development
---

## Local Development

### Jekyll
Run `jekyll serve` to build your site any time a source file changes and serves it locally.

### Docker
Run `docker-compose up --build` to (re)build the jekyll images and run the container.

This will create a container and mount your current repository directory on the container. The container runs `jekyll serve` and creates a local server environment in the container.

Any changes you make to your local repository will be made to the container. To see updates you will need to refresh your browser.