# Lint Config

This is a shared linting configuration package that provides consistent ESLint and Biome rules across different project types in our monorepo.

## Installation

```bash
npm install @repo/lint-config --save-dev
```

Note: This package is marked as private and intended for internal use only.

## Configurations

This package provides both ESLint and Biome configurations for different use cases.

### ESLint Configurations

#### Library

For general TypeScript/JavaScript libraries:

```js
// eslint.config.js
import libraryConfig from '@repo/lint-config/eslint/library.js';

export default libraryConfig;
```

This configuration includes:
- `eslint:recommended` - ESLint's recommended rules
- `prettier` - Disables ESLint rules that conflict with Prettier
- `eslint-config-turbo` - TurboRepo's recommended rules
- `@typescript-eslint` - TypeScript-specific linting rules
- React support with JSX

#### Next.js

For Next.js applications:

```js
// eslint.config.js
import nextConfig from '@repo/lint-config/eslint/next.js';

export default nextConfig;
```

This configuration extends the Library config and adds:
- `@vercel/style-guide/eslint/next` - Vercel's Next.js style guide
- Turbo-specific rules
- Custom rules for Next.js applications

### Biome Configurations

#### Base

Base Biome configuration with common settings:

```json
// biome.json
{
  "extends": ["@repo/lint-config/biome/base.json"]
}
```

This configuration includes:
- Formatter with 2-space indentation, single quotes
- Linter with recommended rules
- VCS integration with Git
- File ignore patterns for common build directories

#### Library

For TypeScript/JavaScript libraries:

```json
// biome.json
{
  "extends": ["@repo/lint-config/biome/library.json"]
}
```

This configuration extends the base config and adds:
- Stricter linting rules for libraries
- Import type enforcement
- Console log warnings
- Performance optimizations

#### Next.js

For Next.js applications:

```json
// biome.json
{
  "extends": ["@repo/lint-config/biome/next.json"]
}
```

This configuration extends the base config and adds:
- Next.js-specific file patterns
- Accessibility rules
- Double quotes for JSX consistency
- Relaxed console log rules for development

## Development

### Dependencies

#### ESLint Dependencies
- `@typescript-eslint/eslint-plugin` - TypeScript ESLint plugin
- `@typescript-eslint/parser` - TypeScript parser for ESLint
- `@vercel/style-guide` - Vercel's style guide
- `eslint-config-prettier` - Prettier configuration for ESLint
- `eslint-config-turbo` - TurboRepo ESLint configuration
- `eslint-plugin-only-warn` - Plugin to convert ESLint errors to warnings

#### Biome Dependencies
- `@biomejs/biome` - Biome formatter and linter

### Adding a New Configuration

#### ESLint Configuration
1. Create a new `.js` file in the `eslint/` directory
2. Export an ESLint configuration object
3. Update this README to document the new configuration

#### Biome Configuration
1. Create a new `.json` file in the `biome/` directory
2. Extend from `base.json` if appropriate
3. Update this README to document the new configuration

## Usage in Projects

### ESLint Usage

```js
// eslint.config.js
import libraryConfig from '@repo/lint-config/eslint/library.js';
// or
import nextConfig from '@repo/lint-config/eslint/next.js';

export default libraryConfig; // or nextConfig
```

### Biome Usage

```json
// biome.json
{
  "extends": ["@repo/lint-config/biome/library.json"]
  // or
  // "extends": ["@repo/lint-config/biome/next.json"]
}
```

### Combined Usage

Projects can use both ESLint and Biome simultaneously:

```js
// eslint.config.js
import eslintConfig from '@repo/lint-config/eslint/library.js';
export default eslintConfig;
```

```json
// biome.json
{
  "extends": ["@repo/lint-config/biome/library.json"]
}
```

## Migration from ESLint-only

To migrate existing projects to use Biome alongside ESLint:

1. Install `@biomejs/biome` as a dev dependency
2. Add a `biome.json` file extending the appropriate config
3. Update package.json scripts to include Biome commands
4. Gradually adopt Biome's formatter and linter rules

## Contributing

This package is maintained internally. For changes, please submit a pull request with your proposed modifications.
