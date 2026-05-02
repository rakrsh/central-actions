# Doc Build and Deploy

The `doc-build-deploy` action builds documentation and deploys it to GitHub Pages.

## Inputs

- `doc-directory` - Path to the documentation source directory. Default: `.`
- `doc-build-command` - Command used to build documentation. Default: `mkdocs build`
- `publish-directory` - Directory containing built docs to publish. Default: `./site`
- `github-token` - GitHub token used for publishing to gh-pages.

## Example

```yaml
uses: ./doc-build-deploy
with:
  doc-directory: "./"
  doc-build-command: "mkdocs build"
  publish-directory: "./site"
  github-token: ${{ secrets.GITHUB_TOKEN }}
```
