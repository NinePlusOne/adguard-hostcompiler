# AdGuard HostlistCompiler GitHub Workflow

This repository uses AdGuard's HostlistCompiler to compile blocklists from multiple sources and automatically update them via GitHub Actions.

## Repository Structure

```
.github/workflows/          # GitHub Actions workflows
configs/                    # HostlistCompiler configuration files
sources/                    # Local source files for blocklists
outputs/                    # Compiled blocklist outputs
```

## Quick Start

1. **Configuration**: Add your configuration files to the `configs/` directory
2. **Local Rules**: Add custom rules to `sources/local-rules.txt`
3. **GitHub Actions**: The workflow runs automatically on schedule and when configs change
4. **Outputs**: Compiled blocklists are saved in `outputs/` directory

## Configuration

Configuration files are JSON files placed in the `configs/` directory. See `configs/main-blocklist.json` for an example.

## Available Transformations

HostlistCompiler supports the following transformations:

1. `RemoveComments` - Removes comments from rules
2. `Compress` - Converts hosts lists to adblock format and removes redundant rules
3. `RemoveModifiers` - Removes unsupported DNS filtering modifiers
4. `Validate` - Removes dangerous or incompatible rules (excludes IP addresses)
5. `ValidateAllowIp` - Same as Validate but keeps IP addresses
6. `Deduplicate` - Removes duplicate rules
7. `InvertAllow` - Converts blocking rules to allow rules
8. `RemoveEmptyLines` - Removes empty lines
9. `TrimLines` - Removes leading/trailing whitespace
10. `InsertFinalNewLine` - Ensures file ends with newline
11. `ConvertToAscii` - Converts non-ASCII characters to ASCII equivalents

## Manual Testing

To test the compilation locally:

```bash
# Install HostlistCompiler globally
npm install -g @adguard/hostlist-compiler

# Compile a specific configuration
hostlist-compiler --config configs/main-blocklist.json --output outputs/main-blocklist.txt --verbose

# Or compile all configurations
for config in configs/*.json; do
  filename=$(basename "$config" .json)
  hostlist-compiler --config "$config" --output "outputs/$filename.txt"
done
```

## GitHub Actions Workflow

The workflow runs:
- Daily at 2 AM UTC
- When configuration files change
- When local source files change
- Manually via workflow_dispatch

## Cost Optimization

- Uses `ubuntu-latest` (cheapest GitHub runner)
- Caches Node.js dependencies
- Only runs when configuration changes or on schedule
- Uses efficient transformation combinations

## Security Considerations

- Validates remote sources during compilation
- Uses minimal GitHub token permissions
- Checks output file integrity before committing

## Additional Resources

- [HostlistCompiler GitHub Repository](https://github.com/AdguardTeam/HostlistCompiler)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [AdGuard DNS Filtering Syntax](https://adguard-dns.io/kb/general/dns-filtering-syntax/)