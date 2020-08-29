# System Requirements - DevOps Tools
GitHub Actions - System Requirements (DevOps Tools)

![GitHub Actions - System Requirements](https://github.com/emvaldes/operations-toolset/workflows/GitHub%20Actions%20-%20System%20Requirements/badge.svg)

[Pipeline Deployment](https://github.com/emvaldes/configure-access/blob/master/.github/workflows/main.yaml)

```console
name: GitHub Actions - System Requirements
## on: [push]
on:
####----------------------------------------------------------------------------
  workflow_dispatch:
    name: 'Manual Deployment'
    description: 'Triggering Manual Deployment'
    inputs:
      logLevel:
        description: 'Log level'
        required: true
        default: 'warning'
      tags:
        description: 'System Requirements'
####----------------------------------------------------------------------------
  push:
    branches: [ master ]
    paths: 
      - action.yaml
####----------------------------------------------------------------------------
# env:
####----------------------------------------------------------------------------
jobs:
  system-requirements:
    runs-on: ubuntu-latest
    steps:
      - name: checkout
        uses: actions/checkout@v2
####----------------------------------------------------------------------------
      ## Privision Access KeyPair
      - name: System Requirements
        uses: ./
        id: system-requirements
        with:
          update-operating-system: true
          update-python-version: true
          install-default-tools: true
          install-custom-tools: 'netcat'
          install-awscli-tool: true
          install-terraform-cli: true
        continue-on-error: false
      - name: Check On Failures
        if: steps.system-requirements.outputs.status == 'failure'
        run: |
          echo -e "Warning: System Requirements Failed [Status]: ${{ steps.system-requirements.outputs.status }}" ;
####----------------------------------------------------------------------------
      ## Installed Packages
      - name: Installed Packages
        id: installed-packages
        shell: bash
        run: |
          jq --version;
          tree --version;
          terraform --version;
```

**<span style="color:red">4</span>** -) The output will be like this: [Pipeline Execution](https://github.com/emvaldes/operations-toolset/actions?query=workflow%3A%22GitHub+Actions+-+System+Requirements%22)

```console
Updating/Upgrading Operating System ...
Reading package lists...
Building dependency tree...
Reading state information...
lsb-release is already the newest version (9.20170808ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.5 LTS
Release:	18.04
Codename:	bionic

Re-Linking Python (latest: 3.6) ...

Python 3.6.9

Installing Default Tools ...
Package: jq ...
Package: tree ...

Installing Custom Tools ...
Package: netcat ...

AWS CLI is Installed ... Ok!
/usr/local/bin/aws
aws-cli/1.18.120 Python/2.7.17 Linux/5.3.0-1034-azure botocore/1.17.43

Upgrading AWS-CLI to version 2.0.40
lrwxrwxrwx 1 root root 22 Aug 17 06:21 /usr/local/bin/aws -> /usr/local/aws/bin/aws
You can now run: /usr/local/bin/aws --version
aws-cli/2.0.44 Python/3.7.3 Linux/5.3.0-1034-azure exe/x86_64.ubuntu.18

HashiCorp Terraform is Installed ... Ok!
/usr/local/bin/terraform

Your version of Terraform is out of date! The latest version
is 0.13.1. You can update by downloading from https://www.terraform.io/downloads.html
Terraform v0.13.0

Terraform Source: releases.hashicorp.com/terraform/0.13.1/terraform_0.13.1_linux_amd64.zip
-rw-r--r-- 1 runner docker 34860186 Aug 26 18:16 /tmp/terraform_0.13.1_linux_amd64.zip
Archive:  /tmp/terraform_0.13.1_linux_amd64.zip
  inflating: terraform
Terraform v0.13.1

Completed!

jq-1.5-1-a5b5cbe
tree v1.7.0 (c) 1996 - 2014 by Steve Baker, Thomas Moore, Francesc Rocher, Florian Sesser, Kyosuke Tokoro
Terraform v0.13.1
```

Happy Coding & Share your work!
