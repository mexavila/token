# Tokens Studio Configuration Guide

## Personal Access Token (PAT)

This repository uses a GitHub Personal Access Token for syncing design tokens from Figma using Tokens Studio.

### Using the Personal Access Token

The Personal Access Token for this repository should be obtained from the repository owner or project administrator. For security reasons, it is not stored in this repository.

**Important**: The token should be kept secure and only used within Tokens Studio for Figma. Never commit tokens to the repository.

### Configuring Tokens Studio

1. Open Tokens Studio plugin in Figma
2. Navigate to Settings → Sync Providers
3. Click "Add new" and select "GitHub"
4. Enter the following details:
   - **Name**: Token Repository (or any name you prefer)
   - **Personal Access Token**: `<YOUR_PAT_TOKEN>` (obtain from repository owner)
   - **Repository**: `mexavila/token`
   - **Branch**: `main`
   - **File Path**: `tokens/tokens.json`
5. Click "Save"

### Syncing Tokens

#### Push to GitHub
1. Make changes to your tokens in Figma
2. In Tokens Studio, click the "Push" button
3. Add a commit message
4. Click "Push to GitHub"

#### Pull from GitHub
1. In Tokens Studio, click the "Pull" button
2. Your Figma file will update with the latest tokens from GitHub

### Troubleshooting

#### Authentication Failed
- Verify the PAT is entered correctly
- Ensure the token has the `repo` scope
- Check that the repository name is correct

#### Sync Failed
- Ensure the repository is not empty (it should have at least a README)
- Check that the file path exists or can be created
- Verify you have write access to the repository

#### Tokens Not Updating
- Ensure you're on the correct branch
- Check that the file path matches exactly
- Try pulling first to ensure you have the latest version

### Creating a New PAT

If you need to create a new Personal Access Token:

1. Go to GitHub Settings
2. Navigate to Developer Settings → Personal Access Tokens → Tokens (classic)
3. Click "Generate new token"
4. Give it a descriptive name (e.g., "Tokens Studio - Token Repo")
5. Select the `repo` scope
6. Set an expiration date (recommended: 90 days or less)
7. Click "Generate token"
8. Copy the token immediately (you won't be able to see it again)
9. Update the token in Tokens Studio settings

### Security Best Practices

- Never commit PATs to the repository
- Rotate tokens regularly
- Use fine-grained tokens when possible
- Revoke tokens that are no longer needed
- Limit token scope to only what's necessary
