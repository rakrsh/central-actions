# Doc Build and Deploy

A reusable GitHub Action that builds documentation and deploys it to GitHub Pages.

## Inputs

- `doc-directory` - Path to the documentation source directory. Default: `.`
- `doc-build-command` - Command used to build documentation. Default: `make html`
- `publish-directory` - Directory containing built docs to publish. Default: `./_build/html`
- `github-token` - GitHub token used for publishing to gh-pages.

## Example

```yaml
uses: ./doc-build-deploy
with:
  doc-directory: "./docs"
  doc-build-command: "make html"
  publish-directory: "./docs/_build/html"
  github-token: ${{ secrets.GITHUB_TOKEN }}
```
