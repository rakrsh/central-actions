# Get Version Action

A reusable GitHub Action to fetch the project version from common configuration files: `pyproject.toml`, `package.json`, or `go.mod`.

## Usage

```yaml
steps:
  - name: Checkout code
    uses: actions/checkout@v4

  - name: Get project version
    id: get_version
    uses: rakrsh/central-actions/get-version@v1
    with:
      path: '.'

  - name: Use version
    run: echo "The version is ${{ steps.get_version.outputs.version }}"
```

## Supported Files

- **pyproject.toml**: Extracts the `version` field from `[project]` or `[tool.poetry]`.
- **package.json**: Extracts the `version` field using `jq`.
- **go.mod**: Searches for a commented version line `// version: x.y.z` or falls back to the `go` directive version.

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `path` | Path to the directory containing the version file | No | `.` |

## Outputs

| Output | Description |
|--------|-------------|
| `version` | The extracted version string |
