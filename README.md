# DevOps (DaaS) - System Requirements
GitHub Actions : DevOps As A Service (DaaS) - System Requirements

![GitHub Actions - System Requirements](https://github.com/emvaldes/operations-toolset/workflows/GitHub%20Actions%20-%20System%20Requirements/badge.svg)

---
### GitHub Variables (Required):

```console
AWSCLI_CLI              Install Amazon WebServices CLI (false)
AWSCLI_DOWNLOAD         AWS CLI Download (awscli.amazonaws.com)
AWSCLI_PACKAGE          AWS CLI Package (e.g.: awscli-exe-linux-x86_64.zip)
```
```console
CUSTOM_TOOLS            Install packages from custom list (default: null)
DEFAULT_TOOLS           Install packages from default list (default: null)

PYTHON_REQUIREMENTS     Listing Python packages (default: null)

TERRAFORM_CLI           Install Terraform CLI (false)
TERRAFORM_VERSION       Terraform specific target version (1.5.4)
```
```console
UPDATE_SYSTEM           Updating Operating System (false)
UPGRADE_SYSTEM          Upgrading Operating System (false)

UPDATE_PYTHON           Update Python to the latest version (true)
UPDATE_PIP              Update Python package management (true)

VERBOSE_MODE            Identify verbosity level (false)
```
