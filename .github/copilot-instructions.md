# GitHub Copilot Instructions: Reusable GitHub Actions Repository

This repository is the centralized source of truth for reusable CI/CD assets (Custom Composite Actions and Reusable Workflows). Follow the architectural guidelines, strict validation rules, and naming conventions outlined below when generating or editing any code in this repository.

---

## 1. Directory & Repository Architecture

All custom actions and reusable workflows must live in the following exact hierarchy:

```text
central-actions/
├── .github/
│   ├── copilot-instructions.md
│   └── workflows/
│       ├── test-actions.yml       # Workflows to test actions locally
│       ├── deploy-docs.yml        # Deploy documentation to GitHub Pages
│       └── release.yml            # Semantic versioning release automation
├── action-name-a/                 # Discrete directory per custom action
│   ├── action.yml                 # Metadata file for the action
│   └── README.md                  # Usage documentation and inputs/outputs
├── action-name-b/
│   ├── action.yml
│   └── README.md
├── docs/                          # Documentation source files
│   ├── index.md
│   ├── action-name-a.md
│   └── action-name-b.md
├── test-terraform/                # Test directory for Terraform action
├── pyproject.toml                 # Python project configuration and versioning
├── mkdocs.yml                     # MkDocs configuration for documentation
├── Dockerfile                     # Docker configuration for testing
├── AGENTS.md                      # AI agent guidelines
├── LICENSE                        # Repository license
├── README.md                      # Main repository documentation
└── site/                          # Built documentation output
```

---

## 2. Consistency Requirements

**On every change to actions, workflows, or configurations, ensure the following are updated consistently:**

- **Documentation (docs/)**: Update relevant .md files in docs/ to reflect changes in inputs, outputs, usage, or behavior.
- **Tests (test-actions.yml)**: Modify or add test jobs in .github/workflows/test-actions.yml to validate new functionality or changes.
- **CI/CD Workflows**: Update other workflows (e.g., deploy-docs.yml, release.yml) if changes affect deployment or release processes.
- **README.md**: Keep the main README.md synchronized with action descriptions, repository structure, and usage instructions.

This ensures the repository remains a reliable, well-documented source of truth for reusable CI/CD assets.

## 3. Latest Action Versions

**Always use the latest stable major version for third-party GitHub Actions. For example:**

*   `actions/checkout@v6`
*   `actions/setup-python@v6`
*   `hashicorp/setup-terraform@v4`
*   `docker/login-action@v4`
*   `docker/build-push-action@v7`

Before proposing an action, verify if a newer major version is available.

## 4. Composite Actions Shell

Every `run` step in a composite action (`action.yml`) **must** include `shell: bash`.

## 5. Boolean Inputs

Remember that GitHub Actions boolean inputs are strings. Always use `if: ${{ inputs.param == 'true' }}`.

## 6. No Hardcoding

Never hardcode secrets, account IDs, or environment-specific strings. Use `inputs` and `secrets`.
