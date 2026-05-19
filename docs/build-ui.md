# Build UI

The `build-ui` action builds a UI project using npm, pnpm, or npx. It automatically detects the package manager based on lock files if not specified.

## Inputs

- `working-directory` - The directory where the UI project is located. Default: `.`
- `package-manager` - The package manager to use (`npm`, `pnpm`, `npx`). Set to `auto` to detect based on lock files. Default: `auto`
- `build-command` - The command to run to build the UI. Defaults to `npm run build` or `pnpm run build` based on manager.
- `node-version` - Node.js version to use. Default: `20`
- `pnpm-version` - Version of pnpm to use if manager is pnpm. Default: `9`


## Example

### Auto-detect Package Manager and Build
```yaml
uses: ./build-ui
```

### Specific Package Manager and Working Directory
```yaml
uses: ./build-ui
with:
  working-directory: ./frontend
  package-manager: pnpm
```

### Using npx for Custom Build Command
```yaml
uses: ./build-ui
with:
  package-manager: npx
  build-command: npx vite build
```
