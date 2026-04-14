<h1>
  Drupalforge - Drupal CMS Nuxt Starter Template
</h1>

Setup based upon the Drupalforge Starter template + Drupal CMS v2 + [Nuxt Starter Site Template](https://www.drupal.org/project/lupus_decoupled_starter)


## How to run this template

- This repository is optimized for fast deployment with
  [DevPanel](https://www.devpanel.com). DevPanel deployment files are in the
  [`.devpanel`](.devpanel) directory. You can add the `.devpanel` directory
  from this repository to an existing repository.
- You can run this repository with any tool that supports
  [dev containers](https://containers.dev/supporting).
- This repository is also configured to run with [DDEV](https://ddev.com).


## Publishing a quick start image

For faster deployment, go to the [Actions](../../actions) tab in GitHub after
you create a new repository from this template and add a workflow that
pre-deploys your template in a Docker image, reducing the time needed to launch
a site.
- If your repository is in the Drupal Forge
  [GitHub organization](https://github.com/drupalforge), the Drupal Forge
  _Docker build and push template_ can set up the workflow for you. The
  workflow will generate a new Docker image whenever a commit is pushed to the
  `main` or `test/*` branches. Your images will be in the Drupal Forge
  [Docker Hub account](https://hub.docker.com/u/drupalforge).
- Otherwise, set up your own workflow with the
  _[Drupal Forge Docker Publish](https://github.com/marketplace/actions/drupal-forge-docker-publish)_
  action. It includes a reusable workflow you can call from your workflow. This
  is how the reusable workflow is used in the Drupal Forge _Docker build and
  push template_:

  ```yaml
  name: Docker build and push template
  on:
    push:
      branches:
        - main
        - test/*
    workflow_dispatch:
  jobs:
    build-application:
      uses: drupalforge/docker_publish_action/.github/workflows/docker-publish.yml@main
      with:
        dockerhub_username: ${{ vars.DOCKERHUB_USERNAME }}
      secrets:
        dockerhub_token: ${{ secrets.DOCKERHUB_TOKEN }}
        dp_ai_virtual_key: ${{ secrets.DP_AI_VIRTUAL_KEY }}
  ```
