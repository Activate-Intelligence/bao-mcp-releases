# Bao MCP Server Releases

This repository contains release packages for the Bao Literary Archive MCP Server.

## Structure

- `releases.json` - Version manifest with download URLs and checksums
- `versions/` - Directory containing release archives

## Release Process

1. Create a new release archive:
   ```bash
   tar -czf source.tar.gz --exclude=node_modules --exclude=.git --exclude=dist src/ package.json tsconfig.json
   ```

2. Generate SHA256 checksum:
   ```bash
   shasum -a 256 source.tar.gz
   ```

3. Update `releases.json` with new version info

4. Create GitHub release and upload archive

5. Update the "latest" field in releases.json

## Auto-Update System

The MCP server checks this repository for updates and can automatically download, build, and install new versions.

### Security

All releases include SHA256 checksums for verification. The auto-update system will not install packages that fail checksum validation.

## Versioning

Follows semantic versioning (MAJOR.MINOR.PATCH):
- MAJOR: Breaking changes
- MINOR: New features, backward compatible  
- PATCH: Bug fixes, backward compatible