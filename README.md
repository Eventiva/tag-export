# Bit Tag and Export for CI/CD Pipelines
Persist Bit Soft Tags and Export to Remote Scope

# GitHub Actions

This CD Task, executs `bit tag --persist and bit export` inside the workspace directory.

## Inputs

### `ws-dir`

**Optional** The workspace directory path from the root. Default `"./"`.

## Example usage

```yaml
name: Test Bit Tag and Export
on:
  workflow_dispatch:
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
      - name: Initialize Bit
        uses: bit-tasks/init@v1
        with:
          ws-dir: '<workspace-directory-path>'
      - name: Bit Tag and Export
        uses: bit-tasks/tag-export@v1
        with:
          ws-dir: '<workspace-directory-path>'
```

# Contributor Guide

Steps to create custom tasks in different CI/CD platforms.

## GitHub Actions

Go to the GithHub action task directory and build using NCC compiler. For example;

```
npm i -g @vercel/ncc
npm install
ncc build index.js --license licenses.txt
git commit -m "Update task"
git tag -a -m "action release" v1
git push --follow-tags
```

For more information refer [Create a javascript action](https://docs.github.com/en/actions/creating-actions/creating-a-javascript-action)

## GitLab CI/CD

For more information refer [Specify a custom CI/CD file](https://docs.gitlab.com/ee/ci/pipelines/settings.html#specify-a-custom-cicd-configuration-file)

## Azure DevOps

For more information refer [Add build task](https://learn.microsoft.com/en-us/azure/devops/extend/develop/add-build-task?view=azure-devops)