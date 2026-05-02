# central-actions

Centralized repository for your custom GitHub Actions.

## Repository structure

```text
central-actions/
├── .github/
│   └── workflows/
│       └── test-actions.yml
├── terraform-deploy/
│   ├── action.yml
│   └── README.md
├── docker-build-push/
│   ├── action.yml
│   └── README.md
├── doc-build-deploy/
│   ├── action.yml
│   └── README.md
└── README.md
```

## Actions

- `terraform-deploy` - Runs Terraform CLI commands in a target directory.
- `docker-build-push` - Builds a Docker image and pushes it to a registry.
- `doc-build-deploy` - Builds documentation and deploys it to GitHub Pages.

## Testing

A sample workflow is included at `.github/workflows/test-actions.yml` to exercise the actions locally in this repository.
