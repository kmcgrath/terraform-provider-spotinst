## 1.6.0 (Unreleased)

NOTES:
* resource/spotinst_elastigroup_azure: Added a new spotinst_elastigroup_azure resource for creating Spotinst elastigroups using Microsoft Azure
* resource/spotinst_elastigroup_gcp: Added a new spotinst_elastigroup_gcp resource for creating Spotinst elastigroups using Google Cloud
* resource/spotinst_elastigroup_gke: Added a new spotinst_elastigroup_gke resource for creating Spotinst elastigroups using Google Kubernetes Engine

FEATURES:

* *New Resource*: `spotinst_elastigroup_azure`
* *New Resource*: `spotinst_elastigroup_gcp`
* *New Resource*: `spotinst_elastigroup_gke`


## 1.5.0 (December 28, 2018)

NOTES:

* resource/spotinst_elastigroup_aws_beanstalk: Added a new `elastigroup_aws_beanstalk` resource for creating Spotinst elastigroups that are managed by an existing AWS Elastic Beanstalk

FEATURES:

* *New Resource*: `spotinst_elastigroup_aws_beanstalk`
* *New Feature*: spotinst provider version added to the User-Agent header

ENHANCEMENTS:

* resource/spotinst_elastigroup_aws_beanstalk: Added a the ability to transition in and out of maintenance modes by setting `maintenance` mode to `START` or `END`
* resource/spotinst_elastigroup_aws: Added the ability to wait for a minimum number of healthy instances for a certain period of time
* resource/spotinst_elastigroup_aws: Added ability to maintain scaling policy configuration when disabled
* resource/spotinst_elastigroup_aws: Scheduled tasks now support `adjustment` field
* resource/spotinst_elastigroup_aws: Rancher integration now supports `version` field
* resource/spotinst_elastigroup_aws: Use new `wait_for_capacity` field to indicate the minimum number of healthy instances required before continuing plan execution
* resource/spotinst_elastigroup_aws: Use new `wait_for_capacity_timeout` to indicate how long to wait for minimum number of instances to become healthy
* resource/spotinst_elastigroup_aws: Use new `is_enabled` field in scaling policies to indicate if that policy is active
* resource/spotinst_elastigroup_aws: Use new `adjustment` field in `scheduled_tasks` to indicate the number of instances to add or remove when scaling

BUG FIXES:

* resource/spotinst_elastigroup_aws: `user_data` and `shutdown_script` no longer updates to empty string SHA
* resource/spotinst_elastigroup_aws: Fixed an issue of `tags`, `instance_types_spot` and `instance_types_preferred_spot` not being imported properly 
* resource/spotinst_elastigroup_aws: Fixed an issue where `associate_public_ip` incorrectly defaulting to `false` when undefined

## 1.4.0 (September 13, 2018)

ENHANCEMENTS:

* resource/spotinst_elastigroup_aws: Shutdown script is now supported under `shutdown_script`
* resource/spotinst_elastigroup_aws: ECS integration support for `autoscale_is_autoconfig`
* resource/spotinst_elastigroup_aws: Docker Swarm integration as `integration_docker_swarm`

## 1.3.0 (August 13, 2018)

ENHANCEMENTS:

* resource/spotinst_elastigroup_aws: Added a new Route53 integration as `integration_route53`
* resource/spotinst_elastigroup_aws: Added support for preferred spot instances as `instance_types_preferred_spot`

## 1.2.0 (July 26, 2018)

ENHANCEMENTS:

* resource/spotinst_elastigroup_aws: Added `kms_key_id` support for `ebs_block_device`
* resource/spotinst_elastigroup_aws: Added `autoscale_attributes` support for `integration_ecs`
* resource/spotinst_elastigroup_aws: Added `autoscale_labels` support for `integration_kubernetes`
* resource/spotinst_elastigroup_aws: Added `autoscale_constraints` support for `integration_nomad`

## 1.1.1 (July 09, 2018)

BUG FIXES:

* resource/spotinst_elastigroup_aws: `scheduled_task` & `network_interface` now properly address fields not specified on TF file as nil instead of their default values

## 1.1.0 (July 02, 2018)

NOTES

* resource/spotinst_subscription: Added a new subscription resource for creating Spotinst subscriptions that gets triggered by an elastigroup event type

FEATURES:

* **New Resource:** `spotinst_subscription`

ENHANCEMENTS:

* resource/spotinst_elastigroup_aws: Added a new Gitlab runner integration

BUG FIXES:

* resource/spotinst_elastigroup_aws: Resource now properly create multiple elastigroups using the count parameter and/or using parallelism via terraform apply

## 1.0.0 (June 21, 2018)

BREAKING CHANGES / NOTES

Introduced a new API schema to support the latest Spotinst API additions while using similar AWS terminology.

* resource/spotinst_group_aws: Resource name changed to `spotinst_elastigroup_aws`
* resource/spotinst_elastigroup_aws: Removed `capacity` and flattened its fields on the resource
* resource/spotinst_elastigroup_aws: Changed all previous `capacity` field names to `max_size`, `min_size`, `desired_capacity`, `capacity_unit`
* resource/spotinst_elastigroup_aws: Removed `launch_specification` and flattened its fields on the resource
* resource/spotinst_elastigroup_aws: Removed `persistence` and flattened its fields on the resource
* resource/spotinst_elastigroup_aws: Removed `strategy` and flattened its fields on the resource
* resource/spotinst_elastigroup_aws: Removed `availability_zone` and currently only `availability_zones` field is supported 
* resource/spotinst_elastigroup_aws: Removed `load_balancers` and broke it down to the following fields: `elastic_load_balancers`, `target_group_arns`, `multai_target_sets`
* resource/spotinst_elastigroup_aws: Dropped previous `tags` field and changed `tags_kv` name to `tags` which accepts only key/value objects
* resource/spotinst_elastigroup_aws: Introduced a new object `update_policy` for group roll configuration
* resource/spotinst_elastigroup_aws: Field `should_resume_stateful` is now available under `update_policy`
* resource/spotinst_elastigroup_aws: Changed `availability_vs_cost` name to `orientation`
* resource/spotinst_elastigroup_aws: Changed `risk` name to `spot_percentage`
* resource/spotinst_elastigroup_aws: Deprecated `hot_ebs_volume`
* resource/spotinst_elastigroup_aws: Deprecated `launch_specification.load_balancer_names`
* resource/spotinst_elastigroup_aws: Deprecated `elastic_beanstalk_integration`
* resource/spotinst_elastigroup_aws: Renamed `rancher_integration` to `integration_rancher`
* resource/spotinst_elastigroup_aws: Renamed `ec2_container_service_integration` to `integration_ecs`
* resource/spotinst_elastigroup_aws: Renamed `kubernetes_integration` to `integration_kubernetes`
* resource/spotinst_elastigroup_aws: Renamed `nomad_integration` to `integration_nomad`
* resource/spotinst_elastigroup_aws: Renamed `mesosphere_integration` to `integration_mesosphere`
* resource/spotinst_elastigroup_aws: Renamed `multai_runtime_integration` to `integration_multai_runtime`

FEATURES:

* **New Resource:** `spotinst_elastigroup_aws`

ENHANCEMENTS:

* resource/spotinst_elastigroup_aws: All singleton objects e.g. integrations now support proper logs formatting on any change
* resource/spotinst_elastigroup_aws: Added support for vpc zone identifier under field name `subnet_ids` as a list of subnet identifiers Strings and `region` field that represent the AWS region your group will be created in
* resource/spotinst_elastigroup_aws: Added support for `autoscale_is_auto_config` under `integration_kubernetes`
* resource/spotinst_elastigroup_aws: Added support for maintenance window under field name `revert_to_spot` 
* resource/spotinst_elastigroup_aws: Kubernetes integration now contain cluster controller support under `integration_mode` and `cluster_identifier`
* resource/spotinst_elastigroup_aws: Flattened previous objects `capacity`, `launch_specification`, `persistence`, `strategy`

## 0.1.0 (June 21, 2017)

NOTES:

* Same functionality as that of Terraform 0.9.8. Repacked as part of [Provider Splitout](https://www.hashicorp.com/blog/upcoming-provider-changes-in-terraform-0-10/)
