# Create Archive

A reusable GitHub Action that creates a `zip`, `tar`, or `tar.gz` archive of a target directory or file, with support for compression levels and optional automatic uploading as a GitHub Actions workflow artifact.

## Inputs

- `path` - Path of the directory or file whose contents are supposed to be archived. Default: `.`
- `type` - The type of archive to create. Supported types: `zip`, `tar`, `tar.gz`. Default: `tar.gz`
- `compression-level` - Compression level (`0-9`; `0` is no compression, `9` is maximum compression). Default: `6`
- `output-name` - The filename of the created archive. Defaults to `archive.<type>`.
- `upload-artifact` - Whether to upload the generated archive as a GitHub Actions artifact (`true`/`false`). Default: `true`
- `artifact-name` - The name under which the artifact is uploaded. Defaults to the output archive filename.

## Outputs

- `archive-path` - The absolute path to the generated archive file.

## Example

### Default Archive (tar.gz of current workspace, uploaded)
```yaml
- name: Archive workspace
  uses: ./create-archive
```

### Create a zip archive of a specific folder
```yaml
- name: Zip build outputs
  uses: ./create-archive
  with:
    path: ./dist
    type: zip
    output-name: build-outputs.zip
    upload-artifact: 'true'
    artifact-name: frontend-build
```

### Create a high-compression tar.gz archive of a single file
```yaml
- name: Archive production binary
  uses: ./create-archive
  with:
    path: ./bin/server
    type: tar.gz
    compression-level: '9'
    output-name: server-bin.tar.gz
    upload-artifact: 'false'
```
