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
├── docs/
│   ├── index.md
│   ├── docker-build-push.md
│   ├── doc-build-deploy.md
│   └── terraform-deploy.md
├── mkdocs.yml
└── README.md
```

## Actions

- `terraform-deploy` - Runs Terraform CLI commands in a target directory.
- `docker-build-push` - Builds a Docker image and pushes it to a registry.
- `doc-build-deploy` - Builds documentation and deploys it to GitHub Pages.
- `get-version` - Fetches project version from pyproject.toml, package.json, or go.mod.

## Documentation

The repository documentation is hosted with MkDocs and can be built locally with:

```bash
pip install mkdocs-material
mkdocs serve
```

A GitHub Actions workflow is included at `.github/workflows/deploy-docs.yml` to publish the site to GitHub Pages.

## Testing

A sample workflow is included at `.github/workflows/test-actions.yml` to exercise the actions locally in this repository.

## Release automation

The repository includes a release-please workflow at `.github/workflows/release-please.yml`.

To use it, create a repository secret named `RELEASE_PLEASE_TOKEN` with a personal access token that has `repo` scope. This token is required for the action to create pull requests and tags.

## Pre-commit

This repository includes a `.pre-commit-config.yaml` file to enforce consistent formatting and catch common issues.

Install and enable it locally with:

```bash
pip install pre-commit
pre-commit install
pre-commit run --all-files
```
