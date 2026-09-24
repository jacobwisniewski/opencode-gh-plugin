# opencode-gh-plugin

An OpenCode V2 TUI plugin that adds GitHub pull-request and CI context to the
session sidebar.

## Features

- Resolves repository context from the viewed session rather than the shell's
  current directory.
- Shows the current path and branch.
- Shows a clickable pull-request link.
- Summarizes GitHub Actions checks and expands the most relevant checks.
- Refreshes after session activity, branch changes, and Git HEAD changes.
- Can notify the active agent when CI enters a failing state.
- Opens links on macOS, Linux, and Windows.

## Requirements

- OpenCode V2 with CLI plugin support
- `gh`, authenticated for the repository
- `git`
- The viewed session directory must exist locally

## Install

Install the fork directly from GitHub:

```sh
opencode2 plugin add github:jacobwisniewski/opencode-gh-plugin
```

Alternatively, clone it into OpenCode's global plugin directory:

```sh
git clone https://github.com/jacobwisniewski/opencode-gh-plugin.git \
  ~/.config/opencode/plugins/opencode-gh-plugin
```

OpenCode discovers package directories under `~/.config/opencode/plugins/`
automatically. Alternatively, add the local package explicitly to
`~/.config/opencode/cli.json`:

```json
{
  "$schema": "https://opencode.ai/v2/cli.json",
  "plugins": ["./plugins/opencode-gh-plugin"]
}
```

Restart OpenCode after installation.

## Development

```sh
npm install
npm run check
```

The package exports a no-op server entrypoint and a `./tui` entrypoint, allowing
OpenCode V2 to load the sidebar automatically whether the package is discovered
locally or configured as a plugin.

## Upstream

This is a V2 port of
[`stefanmatar/opencode-gh-plugin`](https://github.com/stefanmatar/opencode-gh-plugin).
