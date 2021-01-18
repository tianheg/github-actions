# VuePress GitHub Actions

A GitHub Action to build and deploy Vuepress sites to GitHub Pages

## Usage

Create `vuepress-deploy.yml` in the `.github/workflows` directory in the root of your repository.

```yml
name: Build and Deploy
on: [push]
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: vuepress-deploy
      uses: tianheg/github-actions@vuepress
      env:
        ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
        TARGET_REPO: username/repo
        TARGET_BRANCH: gh-pages
        BUILD_SCRIPT: yarn && yarn build
        BUILD_DIR: blog/.vuepress/dist/
```

## Parameters

|  Parameter |  Description | Type | Required
| :------------ | :------------ |:------------ |:------------ |
| `ACCESS_TOKEN` | Personal access token | `secrets`  |  **Yes** |
| `TARGET_REPO` | The repository you want to deploy. e.g.:`tianheg/blog`. Default: **current repository** | `env` | **No** |
| `TARGET_BRANCH` | The branch you want to deploy. e.g.:`gh-pages`.Default: **gh-pages** | `env` | **No** |
| `TARGET_LINK` | The full address of the target repo will cover `TARGET_REPO` for other platforms. e.g.:`https://user:${{ secrets.CODING_TOKEN }}@team.coding.net/team/repo.git`. | `env` | **No** |
| `BUILD_SCRIPT` | The script to build the vuepress project. e.g.: `yarn && yarn build` | `env` | **Yes** |
| `BUILD_DIR` | The output of the build-script above. e.g.: `blog/.vuepress/dist/` | `env` | **Yes** |
| `CNAME` | Alias Record of your site. | `env` | **no** |

## Step-by-Step Guide

### Create a personal access token

click your profile icon > Settings > Developer settings > Personal access tokens > Generate new token > At least check `repo`. Then you will get a token, copy it.

### Creating encrypted secrets

Under your repository name, click  Settings > Secrets > Type `ACCESS_TOKEN` in the "Name" input box && the the personal access token as value.

### Create a workflow file

If you repo doesn't already have one, create a workflow file. You must store workflows in the `.github/workflows` directory in the root of your repository.

In `.github/workflows`, add a `.yml` or `.yaml` file for your workflow. For example, `.github/workflows/vuepress-deploy.yml`.

**For more information**:

1. [Triggering new workflows using a personal access token](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#triggering-new-workflows-using-a-personal-access-token)
2. [Encrypted secrets](https://docs.github.com/en/actions/reference/encrypted-secrets)
3. [Learn GitHub Actions](https://docs.github.com/en/actions/learn-github-actions)

## References

- [jenkey2011/vuepress-deploy](https://github.com/jenkey2011/vuepress-deploy)
