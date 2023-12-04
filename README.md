# Create, Build and Upload packages into PyPI using GitHub Actions.

## INTRODUCTION:

  * We are going to create, build and upload packages into pypi using Github Actions. Here, we are going to create a very simple calculator that takes two numbers and either add, subtract, multiply or divide them.
  * [Python Package for Simple Calculator](https://github.com/VismayaM-2003/packages-yaml/blob/main/pypibacic/__init__.py)
  
## WORKFLOW OVERVIEW:

   * [Workflow file](https://github.com/VismayaM-2003/packages-yaml/blob/main/.github/workflows/python-publish.yml)
   * The provided code is a GitHub Actions workflow defined in YAML format.
     
'''python
name: Publish Python distributions to PyPI and TestPyPI

on:
  workflow_dispatch:
 
'''

