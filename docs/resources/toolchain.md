---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "opentoolchain_toolchain Resource - terraform-provider-opentoolchain"
subcategory: ""
description: |-
  
---

# opentoolchain_toolchain (Resource)



## Example Usage

```terraform
resource "opentoolchain_toolchain" "tc" {
  env_id              = "ibm:yp:us-east"
  name                = "TEST" # can be updated in place
  resource_group_id   = "<resource group id>"
  repository_token    = var.git_api_key
  template_repository = "https://github.ibm.com/whc-toolchain/whc-developer-toolchain-CI"
  template_branch = "stable-3.3.3"
  tags = ["dev", "tf"]
  template_properties = {
    "toolchain.name" = "TEST"
    "apiKey" = var.ic_api_key
    "prodRegion" = "us-south"
    "clusterName" = "mycluster-free"
    "clusterNamespace" = "dev"
    "dockerConfigJson" = var.docker_config_json
    "inputGitBranch" = "master"
    "gitrepourl" = "https://github.ibm.com/<your repository>"
    "form.pipeline.parameters.UMBRELLA_GIT_BRANCH" = "dev"
    // add more properties here, depending on the template used
  }

  lifecycle {
    ignore_changes = [
      template_properties["toolchain.name"],
    ]
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **env_id** (String) Environment ID, example: `ibm:yp:us-south`
- **resource_group_id** (String) The GUID of resource group where toolchain will be created.

### Optional

- **id** (String) The ID of this resource.
- **name** (String) Toolchain name
- **repository_token** (String) If you are using a private GitHub or GitLab repository to host your template repo you will need to provide a personal access token
- **tags** (Set of String)
- **template_branch** (String) The Git branch name that the template will be read from
- **template_properties** (Map of String) Additional properties that are used by the template
- **template_repository** (String) The Git repository that the template will be read from

### Read-Only

- **crn** (String)
- **description** (String) Toolchain description
- **guid** (String) The toolchain `guid`
- **key** (String) Toolchain key
- **services** (List of Object) (see [below for nested schema](#nestedatt--services))
- **url** (String) Toolchain URL

<a id="nestedatt--services"></a>
### Nested Schema for `services`

Read-Only:

- **broker_id** (String)
- **instance_id** (String)
- **parameters** (Map of String)
- **service_id** (String)


