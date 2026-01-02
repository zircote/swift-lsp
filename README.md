# swift-lsp

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Plugin](https://img.shields.io/badge/claude-plugin-orange.svg)](https://docs.anthropic.com/en/docs/claude-code/plugins)
[![Marketplace](https://img.shields.io/badge/marketplace-zircote--lsp-purple.svg)](https://github.com/zircote/lsp-marketplace)
[![Swift](https://img.shields.io/badge/Swift-F05138?logo=swift&logoColor=white)](https://www.swift.org/)

A Claude Code plugin providing comprehensive Swift development support through:

- **SourceKit-LSP** integration for IDE-like features
- **Automated hooks** for formatting, linting, and building
- **Swift ecosystem** integration (SwiftFormat, SwiftLint)

## Quick Setup

```bash
# Run the setup command (after installing the plugin)
/setup
```

Or manually:

```bash
# SourceKit-LSP is included with Xcode
xcode-select --install

# Install development tools
brew install swiftformat swiftlint
```

## Features

### LSP Integration

The plugin configures SourceKit-LSP for Claude Code via `.lsp.json`:

```json
{
    "swift": {
        "command": "sourcekit-lsp",
        "args": [],
        "extensionToLanguage": {
            ".swift": "swift"
        },
        "transport": "stdio"
    }
}
```

**Capabilities:**
- Go to definition / references
- Hover documentation
- Code completion
- Refactoring support
- Real-time diagnostics

### Automated Hooks

| Hook | Trigger | Description |
|------|---------|-------------|
| `swiftformat` | `**/*.swift` | Code formatting |
| `swiftlint` | `**/*.swift` | Linting and style checks |
| `swift-syntax` | `**/*.swift` | Syntax validation |
| `swift-todo-fixme` | `**/*.swift` | Surface TODO/FIXME comments |

## Required Tools

| Tool | Installation | Purpose |
|------|--------------|---------|
| `sourcekit-lsp` | Included with Xcode | LSP server |
| `swiftformat` | `brew install swiftformat` | Formatting |
| `swiftlint` | `brew install swiftlint` | Linting |

## Project Structure

```
swift-lsp/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata
├── .lsp.json                  # SourceKit-LSP configuration
├── commands/
│   └── setup.md              # /setup command
├── hooks/
│   └── scripts/
│       └── swift-hooks.sh
├── tests/
│   └── SampleTest.swift      # Test file
├── CLAUDE.md                  # Project instructions
└── README.md                  # This file
```

## License

MIT
