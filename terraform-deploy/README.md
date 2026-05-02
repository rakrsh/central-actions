# Terraform Deploy

A reusable GitHub Action that runs Terraform CLI commands in a specified directory.

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
