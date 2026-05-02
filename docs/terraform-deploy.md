# Terraform Deploy

The `terraform-deploy` action runs Terraform CLI commands in a target directory.

## Inputs

- `terraform-directory` - Path to the Terraform configuration directory. Default: `.`
- `terraform-command` - Terraform command to execute. Default: `plan`

## Example

```yaml
uses: ./terraform-deploy
with:
  terraform-directory: "./infra"
  terraform-command: "plan"
```
