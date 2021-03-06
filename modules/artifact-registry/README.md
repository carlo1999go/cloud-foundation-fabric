# Google Cloud Artifact Registry Module

This module simplifies the creation of repositories using Google Cloud Artifact Registry.

Note: Artifact Registry is still in beta, hence this module currently uses the beta provider.

## Example

```hcl
module "docker_artifact_registry" {
  source     = "./modules/artifact-registry"
  project_id = "myproject"
  location   = "europe-west1"
  format     = "DOCKER"
  id         = "myregistry"
  iam_roles  = ["roles/artifactregistry.admin"]
  iam_members = {
    "roles/artifactregistry.admin" = ["group:cicd@example.com"]
  }
}
```

<!-- BEGIN TFDOC -->
## Variables

| name | description | type | required | default |
|---|---|:---: |:---:|:---:|
| id | Repository id | <code title="">string</code> | ✓ |  |
| project_id | Registry project id. | <code title="">string</code> | ✓ |  |
| *description* | An optional description for the repository | <code title="">string</code> |  | <code title="">Terraform-managed registry</code> |
| *format* | Repository format. One of DOCKER or UNSPECIFIED | <code title="">string</code> |  | <code title="">DOCKER</code> |
| *iam_members* | Map of member lists used to set authoritative bindings, keyed by role. | <code title="map&#40;list&#40;string&#41;&#41;">map(list(string))</code> |  | <code title="">{}</code> |
| *iam_roles* | List of roles used to set authoritative bindings. | <code title="list&#40;string&#41;">list(string)</code> |  | <code title="">[]</code> |
| *labels* | Labels to be attached to the registry. | <code title="map&#40;string&#41;">map(string)</code> |  | <code title="">{}</code> |
| *location* | Registry location. Use `gcloud beta artifacts locations list' to get valid values | <code title="">string</code> |  | <code title=""></code> |

## Outputs

| name | description | sensitive |
|---|---|:---:|
| id | Repository id |  |
| name | Repository name |  |
<!-- END TFDOC -->
