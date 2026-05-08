# Generate SBOM Action

A language-agnostic GitHub Composite Action to generate and upload Software Bill of Materials (SBOM). It automatically detects various language ecosystems (e.g. Node.js, Python, Go, Java, Rust) and generates an individual SBOM for each detected language, alongside a combined SBOM for the entire repository. It then uploads the generated SBOMs as workflow artifacts.

## Usage

```yaml
jobs:
  sbom:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: rakrsh/central-actions/generate-sbom@v1
        with:
          format: 'spdx-json'
          artifact-name: 'my-app-sbom'
```

## Inputs

| Name | Description | Required | Default |
| --- | --- | --- | --- |
| `path` | Path to scan | No | `.` |
| `format` | Format of SBOM (e.g. `spdx-json`, `cyclonedx-json`) | No | `spdx-json` |
| `artifact-name` | Name prefix for the uploaded artifacts | No | `sbom` |

## Outputs

| Name | Description |
| --- | --- |
| `combined-sbom-path` | Path to the generated combined SBOM file |
