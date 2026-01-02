# Publishing to GitHub

## Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `founder-support-system`
3. Description: "Strategic planning and executive coaching plugin for founders"
4. Public or Private (your choice)
5. Do NOT initialize with README (we have one)
6. Create repository

## Verify plugin.json

Verify that `.claude-plugin/plugin.json` has the correct repository URLs:

```json
{
  "homepage": "https://github.com/Pitchlab/founder-support-system",
  "repository": "https://github.com/Pitchlab/founder-support-system"
}
```

## Push to GitHub

```bash
cd /path/to/founder-support-system

# Add remote (replace Pitchlab)
git remote add origin https://github.com/Pitchlab/founder-support-system.git

# Verify files are staged
git status

# If needed, stage all files
git add .
git commit -m "feat: Initial release of Founder Support System v1.0.0"

# Push
git branch -M main
git push -u origin main
```

## Tag Release

```bash
git tag -a v1.0.0 -m "Initial release - Strategic planning and coaching for founders"
git push origin v1.0.0
```

## Create GitHub Release (Optional)

1. Go to your repository on GitHub
2. Click "Releases" → "Create a new release"
3. Choose tag: `v1.0.0`
4. Release title: `v1.0.0 - Initial Release`
5. Description: Copy from CHANGELOG.md
6. Publish release

## Distribution

Users can install via:

### From GitHub
```bash
# Direct GitHub installation (replace Pitchlab)
claude plugin install github:Pitchlab/founder-support-system
```

### From Local Clone
```bash
# Clone and install
git clone https://github.com/Pitchlab/founder-support-system.git
cd founder-support-system
claude plugin install .
```

## Updating

When you make changes:

1. Update version in `.claude-plugin/plugin.json`
2. Update `CHANGELOG.md` with changes
3. Commit and push:
   ```bash
   git add .
   git commit -m "feat: Description of changes"
   git push origin main
   ```
4. Tag new version:
   ```bash
   git tag -a v1.1.0 -m "Version 1.1.0 - Description"
   git push origin v1.1.0
   ```

Users update via:
```bash
claude plugin update founder-support-system
```

## Versioning

Follow Semantic Versioning (semver):
- **MAJOR** (1.x.x): Breaking changes, incompatible API changes
- **MINOR** (x.1.x): New features, backwards-compatible
- **PATCH** (x.x.1): Bug fixes, backwards-compatible

Examples:
- `1.0.0`: Initial release
- `1.0.1`: Bug fix (config loading issue)
- `1.1.0`: New feature (added new coach)
- `2.0.0`: Breaking change (changed config structure)

## Best Practices

1. **Always test locally** before pushing
2. **Update CHANGELOG.md** for every release
3. **Tag releases** consistently
4. **Keep README.md updated** with new features
5. **Respond to issues** on GitHub

## .gitignore Reminder

Make sure `.claude-plugin/config.json` is gitignored so users don't accidentally commit their personal Notion URLs.

The repository should only include:
- `.claude-plugin/config.template.json` (template)
- Not `.claude-plugin/config.json` (personal URLs)
