# Heroku Build

![GitHub](https://img.shields.io/github/license/AkhileshNS/heroku-deploy.svg)

## Getting Started

To get started using the action, just make sure to have a [Procfile](https://devcenter.heroku.com/articles/getting-started-with-nodejs#define-a-procfile) or a [Dockerfile](https://docs.docker.com/engine/reference/builder/) in your project and then create a folder called **.github** and inside it, create another folder called **workflows**. Finally inside the workflows folder, create a file called **main.yml** with the following contents:

_.github/workflows/main.yml_

```yaml
name: Deploy

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to Heroku
        uses: behe/heroku-build@v1
        with:
          app-name: "your-app-name-on-heroku"
          api-key: "${{secrets.HEROKU_API_KEY}}"
          path: "optional-path-of-build-to-deploy"
```

Now go to your Heroku account and go to Account Settings. Scroll to the bottom until you see API Key. Copy this key and go to your project's repository on GitHub.

In your Repo, go to Settings -> Secrets and click on "New Secret". Then enter HEROKU_API_KEY as the name and paste the copied API Key as the value.

You can now push your project to GitHub and it will be automatically deployed to Heroku henceforth.

You learn more about GitHub Secrets [here](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) and GitHub Actions [here](https://docs.github.com/en/actions)
