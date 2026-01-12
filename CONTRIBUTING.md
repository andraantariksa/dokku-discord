# Contributing to Dokku Discord Plugin

Thank you for your interest in contributing to this project!

## Development Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/dokku-discord.git
   cd dokku-discord
   ```

2. Install on a Dokku server for testing:
   ```bash
   sudo dokku plugin:install /path/to/dokku-discord discord
   ```

## Project Structure

- `plugin.toml` - Plugin metadata and description
- `commands` - Help output handler
- `subcommands/` - Command implementations
  - `default` - Default help command
  - `set` - Set webhook URL
  - `get` - Get webhook URL
  - `clear` - Clear webhook URL
- `post-deploy` - Post-deploy trigger for sending notifications
- `install` - Installation script

## Making Changes

1. Create a new branch for your feature or bugfix
2. Make your changes to the bash scripts
3. Test your changes on a Dokku server:
   ```bash
   sudo dokku plugin:install /path/to/dokku-discord discord
   dokku discord:set https://discord.com/api/webhooks/... testapp
   ```
4. Update documentation if needed
5. Submit a pull request

## Code Style

- Use `#!/usr/bin/env bash` shebang
- Include `set -eo pipefail` for error handling
- Support trace mode with `[[ $DOKKU_TRACE ]] && set -x`
- Follow existing code style and conventions
- Use meaningful variable names (uppercase for constants)
- Add comments for complex logic
- Source common functions: `source "$PLUGIN_CORE_AVAILABLE_PATH/common/functions"`

## Testing

Before submitting a PR, ensure:

- All scripts are executable (`chmod +x`)
- The plugin installs without errors
- Commands work as expected (`discord:set`, `discord:get`, `discord:clear`)
- The post-deploy hook sends notifications correctly
- Error messages are clear and helpful
- Documentation is updated if needed

## Submitting a Pull Request

1. Update the CHANGELOG.md with your changes
2. Ensure all scripts are tested
3. Write a clear PR description explaining your changes
4. Reference any related issues

## Questions?

Feel free to open an issue for any questions or concerns!
