# AI Agent Context & Execution Guidelines (`AGENTS.md`)

This file provides context, rules, and constraints for AI agents (Copilot, Cursor, and other LLMs) modifying or generating code in this repository. **Read this file in its entirety before proposing any changes.**

---

## 1. Repository Purpose

This repository is a centralized source of truth for **reusable GitHub Actions** and **reusable workflows**. It is designed to be imported by downstream application and infrastructure repositories. 

Your goal as an AI agent is to keep code **DRY**, **highly parameterized**, **secure**, and **backwards-compatible**.

---

## 2. Core Constraints & Execution Rules

When generating code, you **must** strictly adhere to the following rules without exception:

### Rule 1: No Hardcoded Configurations
* Do not hardcode specific AWS Account IDs, GCP Project IDs, domain names, or environment-specific variables.
* Use `inputs` for dynamic variables and `secrets` for sensitive tokens.

### Rule 2: Composite Actions vs. Reusable Workflows
* **Custom (Composite) Actions:** Build these for discrete, reusable *steps* within a job (e.g., setting up a specific toolchain, running tests). 
  * **Every single `run` step must contain `shell: bash`.**
* **Reusable Workflows:** Build these when standardizing an entire *job* or complete multi-job pipeline across multiple repositories (e.g., a standard Kubernetes deployment workflow).

### Rule 3: Version Pinning & Latest Versions
* Do not use `@main` or `@master` for third-party actions. Pin to specific major versions.
* **Always use the latest stable major version** of an action (e.g., `actions/checkout@v6`). Check for newer releases before proposing changes.

### Rule 4: Boolean Input Handling
* In GitHub Actions, boolean inputs are evaluated as strings (`'true'` and `'false'`). Always write conditional logic as:
  ```yaml
  if: ${{ inputs.deploy-now == 'true' }}

### Rule 5: Consistency Across Documentation, Tests, and CI
* **On every change**, ensure all related artifacts are updated consistently:
  * Update documentation in `docs/` for any changes to action inputs, outputs, or behavior.
  * Modify tests in `.github/workflows/test-actions.yml` to validate new or changed functionality.
  * Update CI/CD workflows (e.g., `deploy-docs.yml`, `release.yml`) if changes affect deployment, testing, or release processes.
  * Keep `README.md` synchronized with action descriptions and repository structure.
* This maintains the repository as a reliable, well-documented source of truth for reusable CI/CD assets.