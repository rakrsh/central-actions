# GitHub Copilot Instructions: Reusable GitHub Actions Repository

This repository is the centralized source of truth for reusable CI/CD assets (Custom Composite Actions and Reusable Workflows). Follow the architectural guidelines, strict validation rules, and naming conventions outlined below when generating or editing any code in this repository.

---

## 1. Directory & Repository Architecture

All custom actions and reusable workflows must live in the following exact hierarchy:

```text
central-actions-repo/
├── .github/
│   └── workflows/
│       ├── test-action-a.yml    # Workflows to test actions locally
│       └── release.yml          # Semantic versioning release automation
├── action-name-a/               # Discrete directory per custom action
│   ├── action.yml               # Metadata file for the action
│   └── README.md                # Usage documentation and inputs/outputs
└── action-name-b/
    ├── action.yml
    └── README.md