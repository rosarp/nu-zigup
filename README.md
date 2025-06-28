# nu-zigup

A Nushell script to install, update, and manage Zig compiler and Zig Language Server (ZLS) installations.

## Overview

nu-zigup helps you manage multiple versions of the Zig compiler and ZLS. It allows you to:

- Download and install specific Zig versions
- Switch between installed versions
- Keep up with nightly (master) builds
- Install and manage ZLS for each Zig version
- Create symlinks to make Zig and ZLS available in your PATH

## Installation

1. Make sure you have [Nushell](https://www.nushell.sh/) installed
2. Clone this repository
3. Make the script executable: `chmod +x zigup`
4. Optionally, add the script to your PATH

## Commands

### Basic Usage

```nushell
# Show help information
zigup

# Download and set a specific version as default (defaults to master)
zigup install [VERSION]

# Download a specific version without setting as default (defaults to master)
zigup fetch [VERSION]

# Update to the latest master build (removes existing master first)
zigup master

# List installed compiler versions
zigup list
```

### Installation Directory Management

```nushell
# Print the current installation directory
zigup get-install-dir

# Set the default installation directory
zigup set-install-dir [PATH]
```

### Symlink Management

```nushell
# Create a symlink to zig in the specified PATH
zigup ln-zig PATH

# Create a symlink to zls in the specified PATH
zigup ln-zls PATH
```

### Advanced Usage

```nushell
# Download and update versions.json with available zig versions
zigup get-version-list

# Verify shasum & size of downloaded files
zigup verify-integrity
```

## Configuration

By default, nu-zigup stores all downloads and configuration in `~/.local/share/nu-zigup`. You can change this location using the `set-install-dir` command.

## How It Works

nu-zigup downloads Zig and ZLS binaries from their official sources and manages them locally. It creates symlinks to make the selected versions available as `zig` and `zls` commands.

The script keeps track of available versions using a versions.json file, which can be updated with the `get-version-list` command. By default, it tracks versions from the past 78 weeks (~1.5 years).

## Requirements

- Nushell
- Basic Unix utilities (tar, ln, etc.)

## License

MIT
