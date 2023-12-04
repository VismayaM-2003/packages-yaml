# Create, Build and Upload packages into PyPI using GitHub Actions.

## INTRODUCTION:

  * We are going to create, build and upload packages into pypi using Github Actions. Here, we are going to create a very simple calculator that takes two numbers and either add, subtract, multiply or divide them.
  * [Python Package for Simple Calculator](https://github.com/VismayaM-2003/packages-yaml/blob/main/pypibacic/__init__.py)
  
## WORKFLOW OVERVIEW:

   * [Workflow file](https://github.com/VismayaM-2003/packages-yaml/blob/main/.github/workflows/python-publish.yml)
   * The provided code is a GitHub Actions workflow defined in YAML format.
     
```yaml
name: Publish Python distributions to PyPI and TestPyPI

on:
  workflow_dispatch:
 
```
This specifies the name of the workflow as "Publish Python distributions to PyPI and TestPyPI." The on section indicates that this workflow is triggered by a manual event (workflow_dispatch). This means you can run this workflow manually from the GitHub Actions UI.

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
          #repository_url: https://upload.pypi.org/legacy/

```
Uses the pypa/gh-action-pypi-publish GitHub Action to publish the distribution to PyPI. The action requires a username and password. In this case, the username is __token__, and the password is retrieved from GitHub Secrets (secrets.API_TOKEN). The repository_url is commented out, but it typically points to the PyPI repository.

## SETUP:

   You have to create API TOKEN in the pypi account and copy that token, then go to the github settings, then go to the secrets and variables under that you can click into actions.
In Actions you can see the New repository secret option click into that and name the secret and paste the token into the Value section. 

## LICENSE:

   [This is the license text](https://github.com/VismayaM-2003/packages-yaml/blob/main/LICENSE.txt)
