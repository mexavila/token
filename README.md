# Design Tokens Repository

This repository is configured to work with [Tokens Studio for Figma](https://tokens.studio/) and GitHub Actions for automated design token transformation.

## Overview

Design tokens are stored in the `tokens/` directory and automatically transformed into CSS variables and other formats when changes are pushed to the repository.

## Setup Instructions

### 1. Tokens Studio Configuration

To sync design tokens from Figma to this repository:

1. Install [Tokens Studio for Figma](https://www.figma.com/community/plugin/843461159678059254/Tokens-Studio-for-Figma)
2. In the plugin, go to Settings → Sync Providers
3. Select GitHub as the sync provider
4. Configure the following settings:
   - **Repository**: `mexavila/token`
   - **Branch**: `main` (or your preferred branch)
   - **File Path**: `tokens/tokens.json`
   - **Personal Access Token**: Use the provided PAT or create a new one

### 2. GitHub Personal Access Token (PAT)

A Personal Access Token is required for Tokens Studio to sync with GitHub. The token must have the following permissions:
- `repo` scope (full control of private repositories)

**Note**: The PAT provided in the setup instructions should be kept secure and not committed to the repository.

To create a new token:
1. Go to GitHub Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
2. Click "Generate new token"
3. Select the `repo` scope
4. Copy and save the token securely

### 3. Local Development

To work with tokens locally:

```bash
# Install dependencies
npm install

# Build tokens
npm run build:tokens
```

The build process will generate:
- `build/css/variables.css` - CSS custom properties
- `build/json/tokens.json` - Transformed tokens in JSON format

### 4. GitHub Actions Workflow

The repository includes a GitHub Actions workflow that automatically:
1. Triggers when tokens are updated in the `tokens/` directory
2. Installs dependencies
3. Transforms tokens using Style Dictionary
4. Commits the generated files back to the repository

The workflow runs on:
- Push to the `main` branch (for the `tokens/` directory)
- Pull requests targeting the `main` branch

### 5. Token Structure

Tokens are organized in the `tokens/tokens.json` file using the Tokens Studio format:

```json
{
  "global": {
    "colors": {
      "primary": {
        "value": "#0066cc",
        "type": "color"
      }
    },
    "spacing": {
      "small": {
        "value": "8",
        "type": "spacing"
      }
    }
  }
}
```

## Using the Tokens

### In CSS

After the build process, import the generated CSS file:

```css
@import 'build/css/variables.css';

.button {
  background-color: var(--global-colors-primary);
  padding: var(--global-spacing-medium);
}
```

### In JavaScript

Import the JSON file for programmatic access:

```javascript
import tokens from './build/json/tokens.json';

const primaryColor = tokens.global.colors.primary;
```

## Workflow

1. Designer updates tokens in Figma using Tokens Studio plugin
2. Designer pushes tokens to GitHub via the plugin
3. GitHub Actions automatically transforms tokens
4. Developers pull the updated tokens and use them in their projects

## References

- [Tokens Studio Documentation](https://docs.tokens.studio/)
- [Style Dictionary Documentation](https://amzn.github.io/style-dictionary/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)