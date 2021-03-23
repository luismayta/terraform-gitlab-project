<!--


  ** DO NOT EDIT THIS FILE
  **
  ** 1) Make all changes to `README.yaml`
  ** 2) Run`make readme` to rebuild this file.
  **
  ** (We maintain HUNDREDS of open source projects. This is how we maintain our sanity.)
  **


  -->

# terraform-gitlab-project

[![Lint](https://github.com/hadenlabs/terraform-gitlab-project/actions/workflows/lint.yml/badge.svg?branch=develop)](https://github.com/hadenlabs/terraform-gitlab-project/actions) [![Issues](https://img.shields.io/github/issues/hadenlabs/terraform-gitlab-project.svg)](https://github.com/hadenlabs/terraform-gitlab-project/issues) [![Latest Release](https://img.shields.io/github/release/hadenlabs/terraform-gitlab-project.svg)](https://github.com/hadenlabs/terraform-gitlab-project/releases)

terraform gitlab project

## Usage

```hcl

   module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.1.1"

      providers = {
        gitlab = gitlab
      }

      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

Full working example can be found in [example](./example) folder.

## Examples

### common

```hcl

  module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.1.1"

      providers = {
        gitlab = gitlab
      }

      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

### with group new

```hcl

  resource "gitlab_group" "example" {
    name        = "example"
    path        = "example"
    description = "An example group"
  }

  module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.1.1"

      providers = {
        gitlab = gitlab
      }

      namespace_id = gitlab_group.example.id
      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

### with group exist

```hcl

  data "gitlab_group" "example" {
    full_path = "example"
  }

  module "main" {
      source = "hadenlabs/project/gitlab"
      version = "0.1.1"

      providers = {
        gitlab = gitlab
      }

      namespace_id = data.gitlab_group.example.id
      name        = "project-example"
      description = "gitlab project"
      visibility  = "public"
  }

```

 <!-- DO NOT EDIT. THIS FILE IS GENERATED BY THE MAKEFILE. -->

# Terraform variables

This document gives an overview of variables used in the platform of the terraform-gitlab-project.

## Requirements

| Name      | Version |
| --------- | ------- |
| terraform | >= 0.14 |
| gitlab    | >=3.5.0 |
| local     | >=1.3.0 |

## Providers

| Name   | Version |
| ------ | ------- |
| gitlab | >=3.5.0 |

## Inputs

| Name | Description | Type | Default | Required |
| --- | --- | --- | --- | :-: |
| description | The description of the project. | `string` | n/a | yes |
| name | The name of the project. | `string` | n/a | yes |
| namespace_id | The namespace (group or user) of the project. | `string` | `null` | no |
| settings | Create and manage settings. | `map(any)` | `{}` | no |
| tags | topics or tags of project. | `list(string)` | `[]` | no |
| visibility | The visibility of the project private or public. | `string` | `"private"` | no |

## Outputs

| Name     | Description             |
| -------- | ----------------------- |
| instance | output instance project |

## Help

**Got a question?**

File a GitHub [issue](https://github.com/hadenlabs/terraform-gitlab-project/issues), send us an [email](email) or join our [Slack Community](slack).

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/hadenlabs/terraform-gitlab-project/issues) to report any bugs or file feature requests.

### Development

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

1.  **Fork** the repo on GitHub
2.  **Clone** the project to your own machine
3.  **Commit** changes to your own branch
4.  **Push** your work back up to your fork
5.  Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to rebase the latest changes from "upstream" before making a pull request!

#### Versioning

Releases are managed using github release feature. We use [Semantic Versioning](http://semver.org) for all the releases. Every change made to the code base will be referred to in the release notes (except for cleanups and refactorings).

## Copyright

Copyright © 2018-2021 [Hadenlabs](https://hadenlabs.com)

## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## License

The code and styles are licensed under the MIT license [See project license.](LICENSE).

## Don't forget to 🌟 Star 🌟 the repo if you like terraform-gitlab-project

[Your feedback is appreciated](https://github.com/hadenlabs/terraform-gitlab-project/issues)
