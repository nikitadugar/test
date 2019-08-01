<!-- This file was automatically generated by the `geine`. Make all changes to `README.yaml` and run `make readme` to rebuild this file. -->
# terraform-aws-acm 

Terraform module to create an ACM with either DNS or Email verificaton.

[![Build Status](https://img.shields.io/badge/Terraform-v0.12-green)](https://www.terraform.io) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

---

This module is a component of our extensive strategy to DevOps.
[<img align="right" title="Share on Facebook" src="https://docs.cloudposse.com/images/ionicons/social-facebook-outline-2.0.1-16x16-999999.svg" />][share_facebook]
[<img align="right" title="Share on LinkedIn" src="https://docs.cloudposse.com/images/ionicons/social-linkedin-outline-2.0.1-16x16-999999.svg" />][share_linkedin]
[<img align="right" title="Share on Twitter" src="https://docs.cloudposse.com/images/ionicons/social-twitter-outline-2.0.1-16x16-999999.svg" />][share_twitter]

It is a best-practice for running a piece of infrastructure such as database, cluster and storage. This module is basically combination of [Terraform open source](https://www.terraform.io/) and includes automatation tests and examples. It also helps to create and improve your infrastructure with minimalistic code instead of maintaining the whole infrastructure code yourself.

We have [*fifty plus terraform modules*][terraform_modules]. A few of them are comepleted and are available for open source usage while a few others are in progress.

## Prerequisites

This module has a few dependencies: 

- [Terraform 0.12](https://learn.hashicorp.com/terraform/getting-started/install.html)
- [Go Environment](https://golang.org/doc/install)

There are some GO packages which also needed:

- [github.com/stretchr/testify/assert](https://github.com/stretchr/testify)
- [github.com/gruntwork-io/terratest/modules/terraform](https://github.com/gruntwork-io/terratest)

## Examples


**IMPORTANT:** Since the `master` branch used in `source` varies based on new modifications, we suggest that you use the release versions [here](https://github.com/clouddrove/terraform-aws-acm/releases).

Here are some examples of how you can use this module in your inventory structure:
### ACM with DNS
```hcl
module "acm" {
  source            = "git::https://github.com/clouddrove/terraform-aws-acm.git"
  name              = "certificate"
  application       = "clouddrove"
  environment       = "test"
  label_order       = ["environment", "name", "application"]
  domain_name       = "clouddrove.com"
  validation_method = "DNS"
  dns_validation    = false
}
```

### ACM with Email
```hcl
module "acm" {
  source                = "git::https://github.com/clouddrove/terraform-aws-acm.git"
  name                  = "certificate"
  application           = "clouddrove"
  environment           = "test"
  label_order           = ["environment", "name", "application"]
  domain_name           = "clouddrove.com"
  validation_method     = "EMAIL"
  validate_certificate  = false
}
```

### ACM with Import Certificate
```hcl
module "acm" {
  source              = "git::https://github.com/clouddrove/terraform-aws-acm.git"
  name                = "certificate"
  application         = "clouddrove"
  environment         = "dev"
  label_order         = ["environment", "name", "application"]
  private_key         = "./../../../clouddrove-private-key.pem"
  certificate_body    = "./../../../clouddrove-cert.pem"
  certificate_chain   = "./../../../clouddrove-chain.crt"
  import_certificate  = true
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| application | application (e.g. `cp` or `clouddrove`) | string | - | yes |
| certificate_body | path of certificate body | string | `~` | no |
| certificate_chain | path of certificate chain | string | `` | no |
| create_acm_certificate | Set to false to prevent the creation of a acm certificate. | string | `true` | no |
| dns_validation | Set to prevent validation of DNS. | string | `false` | no |
| domain_name | A domain name for which the certificate should be issued | string | `` | no |
| environment | Environment (e.g. `prod`, `dev`, `staging`) | string | - | yes |
| import_certificate | Set to true or false to decide the creation and import of a acm certificate. | string | `false` | no |
| label_order | label order, e.g. `name`,`application` | list | `<list>` | no |
| name | Name  (e.g. `app` or `cluster`) | string | - | yes |
| private_key | path of private key | string | `` | no |
| ttl | Time to live. | string | `600` | no |
| validate_certificate | Set to false to prevent the validation of a acm certificate. | string | `false` | no |
| validation_method | Which method to use for validation, DNS or EMAIL | string | `` | no |

## Outputs

| Name | Description |
|------|-------------|
| arn | The ID of the s3 bucket |
| domain_validation_options | The ID of the s3 bucket |
| id | The ID of the s3 bucket |
| tags | A mapping of tags to assign to the resource. |

## Testing

In this module testing is performed with [terratest](https://github.com/gruntwork-io/terratest) and it creates a small piece of infrastructure, matches the output like ARN, ID and Tags name etc and destroy infrastructure in your AWS account. This testing is written in GO, so you need a [GO environment](https://golang.org/doc/install) in your system. 

You need to run the following command in the testing folder:
```hcl
  go test -run Test
```

## Feedback

If you come accross a bug or have any feedback, please log it in our [issue-tracker](https://github.com/clouddrove/terraform-aws-acm/issues), or feel free to drop us an email at [hello@clouddrove.com](mailto:hello@clouddrove.com).

If you have found it worth your time, go ahead and give us a * on [our GitHub](https://github.com/clouddrove/terraform-aws-acm)!

## About us

At CloudDrove, we offer expert guidance, implementation support and services to help organisations accelerate their journey to the cloud. Our services include docker and container orchestration, cloud migration and adoption, infrastructure automation, application modernisation and remediation, and performance engineering.

<center>We</center> ❤️  [ Open Source ][we_love_open_source] and you can check out [our other modules][github] to get help with your new Cloud ideas.


  [logo]: https://clouddrove.com/media/images/logo.png
  [website]: https://clouddrove.com
  [github]: https://github.com/clouddrove
  [linkedin]: https://cpco.io/linkedin
  [twitter]: https://twitter.com/clouddrove/
  [email]: https://clouddrove.com/contact-us.html
  [we_love_open_source]: https://github.com/clouddrove
  [terraform_modules]: https://github.com/clouddrove?utf8=%E2%9C%93&q=terraform-&type=&language=
  [share_twitter]: https://twitter.com/intent/tweet/?text=terraform-aws-acm&url=https://github.com/clouddrove/terraform-aws-acm
  [share_linkedin]: https://www.linkedin.com/shareArticle?mini=true&title=terraform-aws-acm&url=https://github.com/clouddrove/terraform-aws-acm
  [share_facebook]: https://facebook.com/sharer/sharer.php?u=https://github.com/clouddrove/terraform-aws-acm
