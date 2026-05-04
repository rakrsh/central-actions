# Get Version

A reusable GitHub Action to fetch the project version from common configuration files.

## Features

- Supports `pyproject.toml` (PEP 621 or Poetry).
- Supports `package.json`.
- Supports `go.mod` (commented version or Go toolchain version).

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `path` | Path to the directory containing the version file | No | `.` |

## Outputs

| Output | Description |
|--------|-------------|
| `version` | The extracted version string |

## Example Usage

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Get version
        id: get_version
        uses: rakrsh/central-actions/get-version@v1

      - name: Build with version
        run: echo "Building version ${{ steps.get_version.outputs.version }}"
```
