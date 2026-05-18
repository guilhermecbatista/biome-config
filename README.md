# @guilhermecbatista/biome

Guilherme Batista's personal, shared [Biome](https://biomejs.dev/) configuration for modern web development. Provides a consistent, opinionated baseline for formatting and linting across all projects — extend it and override only what you need.

---

## Requirements

- [`@biomejs/biome`](https://www.npmjs.com/package/@biomejs/biome) (peer dependency)

---

## Installation

Install the package alongside its peer dependency using your preferred package manager.

```bash
# Bun
bun add -d @guilhermecbatista/biome @biomejs/biome

# pnpm
pnpm add -D @guilhermecbatista/biome @biomejs/biome

# npm
npm install --save-dev @guilhermecbatista/biome @biomejs/biome
```

---

## Usage

Create a `biome.json` file at the root of your project and extend this package. No need to configure everything from scratch.

### Minimal setup

```json
{
  "$schema": "https://biomejs.dev/schemas/2.4.15/schema.json",
  "extends": ["@guilhermecbatista/biome"]
}
```

### With overrides

For project-specific needs — such as ignoring generated files or adjusting formatter settings — you can extend the shared config and override only what differs:

```json
{
  "$schema": "https://biomejs.dev/schemas/2.4.15/schema.json",
  "extends": ["@guilhermecbatista/biome"],
  "files": {
    "ignore": [
      ".next",
      "dist",
      "src/components/ui/*",
      "src/route-tree.gen.ts"
    ]
  },
  "formatter": {
    "lineWidth": 100
  }
}
```

> All shared rules are inherited as-is. Only the properties you explicitly define will be overridden locally.

---

## CLI Scripts

Add the following scripts to your project's `package.json` for formatting and linting:

```json
{
  "scripts": {
    "format": "biome format --write .",
    "check": "biome check --write ."
  }
}
```

| Script | Description |
|---|---|
| `format` | Formats all files in the project |
| `check` | Lints and formats all files, applying safe fixes automatically |

---

## License

[MIT](./LICENSE)