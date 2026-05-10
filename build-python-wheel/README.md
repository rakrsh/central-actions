# Build Python Wheel Action

This action builds a Python wheel (.whl) file for your project using the standard `build` package. It supports both `pyproject.toml` and legacy `setup.py` based projects.

## Usage

```yaml
steps:
  - name: Checkout Code
    uses: actions/checkout@v4

  - name: Build Wheel
    id: build_wheel
    uses: ./.github/actions/build-python-wheel # Adjust path as needed
    with:
      python-version: '3.12'
      project-path: '.'
      output-path: 'dist'

  - name: Upload Artifact
    uses: actions/upload-artifact@v4
    with:
      name: python-wheel
      path: ${{ steps.build_wheel.outputs.wheel-path }}
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `python-version` | Python version to use | No | `3.12` |
| `project-path` | Path to the Python project | No | `.` |
| `output-path` | Directory where the wheel should be saved | No | `dist` |

## Outputs

| Output | Description |
|--------|-------------|
| `wheel-path` | The full path to the generated `.whl` file |
