# Build Python Wheel

Builds a Python wheel (.whl) file using the standard `build` package.

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `python-version` | Python version to use | No | `3.12` |
| `project-path` | Path to the Python project (containing pyproject.toml or setup.py) | No | `.` |
| `output-path` | Directory where the built wheel should be saved | No | `dist` |

## Outputs

| Output | Description |
|--------|-------------|
| `wheel-path` | The path to the generated wheel file |

## Example usage

```yaml
steps:
  - uses: actions/checkout@v4
  - name: Build Wheel
    id: build_wheel
    uses: ./.github/actions/build-python-wheel
    with:
      python-version: '3.12'
  - name: Upload Artifact
    uses: actions/upload-artifact@v4
    with:
      name: release-wheel
      path: ${{ steps.build_wheel.outputs.wheel-path }}
```
