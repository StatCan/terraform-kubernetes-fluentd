# Terraform Kubernetes Fluentd

## Introduction

This module deploys and configures Fluentd inside a Kubernetes Cluster.

## Security Controls

The following security controls can be met through configuration of this template:

* TBD

## Dependencies

* None

## Optional (depending on options configured):

* None

## Usage

```terraform
module "helm_fluentd" {
  source = "git::https://github.com/canada-ca-terraform-modules/terraform-kubernetes-fluentd.git?ref=v2.0.0"
  
  chart_version = "0.0.2"
  dependencies = [
    "${module.namespace_monitoring.depended_on}",
  ]

  helm_service_account = "tiller"
  helm_namespace = "monitoring"
  helm_repository = "stable"

  values = <<EOF

EOF
```

## Variables Values

| Name                 | Type   | Required | Value                                               |
| -------------------- | ------ | -------- | --------------------------------------------------- |
| chart_version        | string | yes      | Version of the Helm Chart                           |
| dependencies         | string | yes      | Dependency name refering to namespace module        |
| helm_service_account | string | yes      | The service account for Helm to use                 |
| helm_namespace       | string | yes      | The namespace Helm will install the chart under     |
| helm_repository      | string | yes      | The repository where the Helm chart is stored       |
| values               | list   | no       | Values to be passed to the Helm Chart               |

## History

| Date     | Release    | Change                                                     |
| -------- | ---------- | ---------------------------------------------------------- |
| 20190729 | 20190729.1 | Improvements to documentation and formatting               |
| 20190909 | 20190909.1 | 1st release                                                |
| 20200620 | v2.0.0     | Module now modified for Helm 3                             |
