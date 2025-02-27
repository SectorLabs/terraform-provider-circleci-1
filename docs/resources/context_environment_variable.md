---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "circleci_context_environment_variable Resource - terraform-provider-circleci"
subcategory: ""
description: |-
  
---

# circleci_context_environment_variable (Resource)

## Usage
Environment variables can be created using a context name:
```hcl
resource "circleci_context_environment_variable" "var" {
  context = "my-context"

  name  = "DUMMY"
  value = "VALUE"
}
```

Or using a data source for the context name:
```hcl
data "circleci_context" "context" {
  name = "my-context"
}

resource "circleci_context_environment_variable" "var" {
  context = data.circleci_context.context.name

  name  = "DUMMY"
  value = "VALUE"
}
```

Or using a context resource:
```hcl
resource "circleci_context" "context" {
  name = "my-context"
}

resource "circleci_context_environment_variable" "var" {
  context = circleci_context.context.name

  name  = "DUMMY"
  value = "VALUE"
}
```


<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `context` (String) The name of the context where the environment variable is defined
- `name` (String) The name of the environment variable
- `value` (String, Sensitive) The value that will be set for the environment variable.

### Read-Only

- `id` (String) The ID of this resource.

## Import

Contexts' environment variables can be imported using the context name and the variable
name:
```bash
$ terraform import circleci_context_environment_variable.var my-context/MY_VARIABLE
```

~> Importing a variable does not support importing the variable value since it is marked
as sensitive.
