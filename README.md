# Create, Build and Publish Packages into PyPI using Github Actions.

## Introduction

  - We are going to create, Build and Publish Packages into PyPI using Github Actions. Here, we are creating a very simple calculator that takes two numbers and either add, subtract, multiply or divide them. 
  - You can find the PACKAGE [here](https://github.com/VismayaM-2003/packages-yaml/blob/main/pypibasic/arithmetic.py). 


## Workflow Overview

The provided code is a GitHub Actions [Workflow](https://github.com/VismayaM-2003/packages-yaml/blob/main/.github/workflows/python-publish.yml) defined in YAML format.

```yaml
name: Publish Python distributions to PyPI and TestPyPI

on: [push]

```
- name Keyword: This keyword is used to specify a name for the workflow. In this case, the workflow is named "Publish Python distributions to PyPI and TestPyPI."

- on Keyword with push Event: This section specifies the events that trigger the workflow. In this case, the workflow is triggered when a push event occurs. A push event typically happens when changes are pushed to the repository, such as new commits or branches.


```yaml
jobs:
  python-build-n-publish:
    name: Build and publish Python distribution
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

```
Defines a job named "python-build-n-publish" that runs on the latest version of Ubuntu. The job includes a set of steps to be executed. The first step is to checkout the repository code using actions/checkout@v3.

```yaml
      - name: Initialize Python 3.11.5
        uses: actions/setup-python@v4
        with:
          python-version: "3.11.5"

```
This step initializes Python 3.11.5 using the actions/setup-python action with version 4. 

```yaml
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
```
Installs or upgrades pip to ensure the latest version is used.

```yaml
      - name: Build binary wheel and a source tarball
        run: python setup.py sdist

```
Runs the python setup.py sdist command to build a binary wheel and a source tarball of the Python distribution.

```yaml
      - name: Publish distribution to PyPI
        uses: pypa/gh-action-pypi-publish@release/v1
        with:
          username: __token__
          password: ${{ secrets.API_TOKEN }}
          repository_url: https://upload.pypi.org/legacy/

```
Uses the pypa/gh-action-pypi-publish GitHub Action to publish the distribution to PyPI. The action requires a username and password. In this case, the username is __token__, and the password is retrieved from GitHub Secrets (secrets.API_TOKEN). The repository_url points to the PyPI repository.

## Setup

You have to create a API TOKEN in the pypi account and copy that token then go to the Github repository, go to the settings, then click onto the Secrets and Variables under that click the Actions, In Actions you can find the New repository secret click into that, name a secret and paste the token into the Value section.

## License

The License text is [here](https://github.com/VismayaM-2003/packages-yaml/blob/main/LICENSE.txt)
