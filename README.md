# ESLint Config

This is a shared ESLint configuration package that provides consistent linting rules across different project types in our monorepo.

## Installation

```bash
npm install eslint-config --save-dev
```

Note: This package is marked as private and intended for internal use only.

## Configurations

This package exports three different ESLint configurations for different use cases:

### Library

For general TypeScript/JavaScript libraries:

```js
// eslint.config.js
module.exports = {
  extends: ["eslint-config/library"],
};
```

This configuration includes:
- `eslint:recommended` - ESLint's recommended rules
- `prettier` - Disables ESLint rules that conflict with Prettier
- `eslint-config-turbo` - TurboRepo's recommended rules
- `only-warn` - Plugin that converts all errors to warnings

### Next.js

For Next.js applications:

```js
// eslint.config.js
module.exports = {
  extends: ["eslint-config/next"],
};
```

This configuration extends the Library config and adds:
- `@vercel/style-guide/eslint/next` - Vercel's Next.js style guide
- `@typescript-eslint` - TypeScript-specific linting rules
- Custom rules for unused variables and environment variables

### React Internal

For internal React libraries that are bundled by their consumers:

```js
// eslint.config.js
module.exports = {
  extends: ["eslint-config/react-internal"],
};
```

This configuration includes:
- `eslint:recommended` - ESLint's recommended rules
- `prettier` - Disables ESLint rules that conflict with Prettier
- `eslint-config-turbo` - TurboRepo's recommended rules
- `@typescript-eslint` - TypeScript-specific linting rules
- `@vitest` - Vitest testing framework rules
- Environment settings for browser, node, and jest

## Development

### Dependencies

- `@typescript-eslint/eslint-plugin` - TypeScript ESLint plugin
- `@typescript-eslint/parser` - TypeScript parser for ESLint
- `@vercel/style-guide` - Vercel's style guide
- `@vitest/eslint-plugin` - Vitest ESLint plugin
- `eslint-config-prettier` - Prettier configuration for ESLint
- `eslint-config-turbo` - TurboRepo ESLint configuration
- `eslint-plugin-only-warn` - Plugin to convert ESLint errors to warnings
- `typescript` - TypeScript

### Adding a New Configuration

1. Create a new `.js` file in the root of this package
2. Export an ESLint configuration object
3. Add the file to the `files` array in `package.json`
4. Update this README to document the new configuration

## Usage in Projects

To use any of these configurations in your project, extend them in your ESLint configuration file:

```js
// eslint.config.js
module.exports = {
  extends: ["eslint-config/library"], // or "eslint-config/next" or "eslint-config/react-internal"
  // Add any project-specific overrides here
};
```

## Contributing

This package is maintained internally. For changes, please submit a pull request with your proposed modifications.
