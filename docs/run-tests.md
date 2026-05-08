# Run Tests and Coverage Action

A language-agnostic GitHub Composite Action to run unit tests and display coverage details.

## Usage

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: rakrsh/central-actions/run-tests@v1
        with:
          test-command: 'npm test -- --coverage'
          coverage-file: 'coverage/lcov-report/index.html'
```

## Inputs

| Name | Description | Required | Default |
| --- | --- | --- | --- |
| `test-command` | The command to run tests and generate coverage | Yes | |
| `coverage-file` | The path to the generated coverage file (if applicable) | No | |
| `working-directory` | Working directory for the test command | No | `.` |
| `fail-on-error` | Whether to fail the workflow if tests fail | No | `true` |

## Outputs

| Name | Description |
| --- | --- |
| `test-status` | Status of the test run (`success`, `failure`, `cancelled`, or `skipped`) |
