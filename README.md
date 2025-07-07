# Claude Code Cheat Sheet (Note : 60% Tested WIP)

![Alt text](images/claude-code-cheat-sheet.png)

> **Your complete guide to mastering Claude Code - from zero to hero in minutes!**

After testing Claude Code extensively, I've developed this comprehensive cheat sheet that will take you from basic to advanced user without wasting time. Whether you're completely new to Claude Code or looking to master advanced features, this guide has you covered.

## Quick Start

```bash
# Install Claude Code
curl -sL https://install.anthropic.com | sh

# Launch interactive REPL
claude

# Check version
claude --version
```

## 📚 Table of Contents

- 🟢 **Level 1: Basic Commands**
- 🟡 **Level 2: Intermediate Commands**
- 🟠 **Level 3: Advanced Commands**
- 🔴 **Level 4: Expert Commands**
- 🔵 **Level 5: Power User Commands**
- 🟣 **Level 6: Master Commands**
- 🤝 **Contributing**
- 📄 **License**

## 🟢 Level 1: Basic Commands

Essential commands to get started

### Installation & Getting Started

```bash
# Install Claude Code
curl -sL https://install.anthropic.com | sh

# Start interactive REPL
claude

# Start with initial prompt
claude "explain this project"

# Check version
claude --version

# Update to latest version
claude update
```

### Basic Navigation

```bash
/help                     # Show help and available commands
/exit                     # Exit the REPL
/clear                    # Clear conversation history
/config                   # Open config panel
/doctor                   # Check Claude Code installation health
```

### Basic File Operations

```bash
# Print mode (SDK) - execute and exit
claude -p "explain this function"

# Process piped content
cat logs.txt | claude -p "explain"

# Continue most recent conversation
claude -c

# Continue via SDK
claude -c -p "Check for type errors"
```

### Session Management

```bash
# Resume session by ID
claude -r "abc123" "Finish this PR"

# Resume with flag
claude --resume abc123 "query"

# Continue session
claude --continue
```

### Keyboard Shortcuts

```bash
Ctrl+C                    # Cancel current operation
Ctrl+D                    # Exit Claude Code
Tab                       # Auto-complete
Up/Down                   # Navigate command history
```

## 🟡 Level 2: Intermediate Commands

Configuration and model management

### Model Configuration

```bash
# Switch models
claude --model sonnet                    # Use Sonnet model
claude --model opus                      # Use Opus model
claude --model claude-sonnet-4-20250514  # Use specific model version
```

### Directory Management

```bash
# Add additional working directories
claude --add-dir ../apps ../lib

# Validate directory paths
claude --add-dir /path/to/project
```

### Output Formatting

```bash
# Different output formats
claude -p "query" --output-format json
claude -p "query" --output-format text
claude -p "query" --output-format stream-json

# Input formatting
claude -p --input-format stream-json
```

### Session Control

```bash
# Limit conversation turns
claude -p --max-turns 3 "query"

# Verbose logging
claude --verbose

# Session cost and duration
/cos                      # Show total cost and duration
```

## 🟠 Level 3: Advanced Commands

Tools and permission management

### Tool Management

```bash
# Allow specific tools without prompting
claude --allowedTools "Bash(git log:*)" "Bash(git diff:*)" "Write"

# Disallow specific tools
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# Prompt for specific tool permission
claude -p --permission-prompt-tool mcp_auth_tool "query"

# Skip all permission prompts (dangerous)
claude --dangerously-skip-permissions
```

### Slash Commands - Session Management

```bash
/compact [instructions]   # Summarize conversation with optional instructions
/clear                    # Reset conversation history and context
/exit                     # Exit the REPL
/help                     # Show available commands
/config                   # Open configuration panel
```

### Slash Commands - System

```bash
/doctor                   # Check installation health
/cos                      # Show cost and duration of current session
/ide                      # Manage IDE integrations
```

## 🔴 Level 4: Expert Commands

MCP and advanced integrations

### Model Context Protocol (MCP)

```bash
# Configure MCP servers
claude mcp

# MCP server management (via slash commands)
/mcp                      # Access MCP functionality
```

### Advanced Piping

```bash
# Complex piping operations
git log --oneline | claude -p "summarize these commits"
cat error.log | claude -p "find the root cause"
ls -la | claude -p "explain this directory structure"
```

### Programmatic Usage

```bash
# JSON output for scripting
claude -p "analyze code" --output-format json

# Stream JSON for real-time processing
claude -p "large task" --output-format stream-json

# Batch processing
claude -p --max-turns 1 "quick query"
```

## 🔵 Level 5: Power User Commands

Advanced workflows and automation

### Custom Slash Commands

```bash
# Create custom commands in .claude/commands/
# Example: .claude/commands/debug.md
/debug                    # Execute custom debug command
/test                     # Execute custom test command
/deploy                   # Execute custom deploy command
```

### Complex Tool Combinations

```bash
# Advanced tool permissions
claude --allowedTools "Bash(git:*)" "Write" "Read" \
       --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# Multiple directory access
claude --add-dir ../frontend ../backend ../shared
```

### Performance Optimization

```bash
# Limit context for performance
claude -p --max-turns 5 "focused query"

# Clear context frequently
/clear                    # Use between tasks for better performance

# Compact conversations
/compact "keep only important parts"
```

## 🟣 Level 6: Master Commands

Expert automation and custom workflows

### Advanced Configuration

```bash
# Complex model and tool configuration
claude --model claude-sonnet-4-20250514 \
       --add-dir ../apps ../lib ../tools \
       --allowedTools "Bash(git:*)" "Write" "Read" \
       --verbose \
       --output-format json
```

### Automation Scripts

```bash
# Scripted Claude interactions
#!/bin/bash
claude -p "analyze codebase" --output-format json > analysis.json
claude -p "generate tests" --max-turns 3 --output-format text > tests.txt
```

### Advanced Session Management

```bash
# Session ID management
SESSION_ID=$(claude -p "start analysis" --output-format json | jq -r '.session_id')
claude -r "$SESSION_ID" "continue analysis"
```

### Complex Workflows

```bash
# Multi-step automation
claude -p "analyze project structure" | \
claude -p "suggest improvements" | \
claude -p "create implementation plan"
```

## Command Reference Tables

### CLI Commands

| Command | Description | Example |
|---------|-------------|---------|
| `claude` | Start interactive REPL | `claude` |
| `claude "query"` | Start REPL with prompt | `claude "explain this project"` |
| `claude -p "query"` | Print mode, execute and exit | `claude -p "explain function"` |
| `claude -c` | Continue recent conversation | `claude -c` |
| `claude -r "id" "query"` | Resume session by ID | `claude -r "abc123" "finish PR"` |
| `claude update` | Update to latest version | `claude update` |
| `claude mcp` | Configure MCP servers | `claude mcp` |

### CLI Flags

| Flag | Description | Example |
|------|-------------|---------|
| `--model` | Specify model | `--model sonnet` |
| `--add-dir` | Add working directories | `--add-dir ../apps ../lib` |
| `--allowedTools` | Allow tools without prompting | `--allowedTools "Bash(git:*)"` |
| `--disallowedTools` | Disallow specific tools | `--disallowedTools "Bash(rm:*)"` |
| `--output-format` | Set output format | `--output-format json` |
| `--input-format` | Set input format | `--input-format stream-json` |
| `--max-turns` | Limit conversation turns | `--max-turns 3` |
| `--verbose` | Enable verbose logging | `--verbose` |
| `--continue` | Continue session | `--continue` |
| `--resume` | Resume session | `--resume abc123` |
| `--dangerously-skip-permissions` | Skip all permission prompts | `--dangerously-skip-permissions` |

### Slash Commands

| Command | Description |
|---------|-------------|
| `/help` | Show help and available commands |
| `/exit` | Exit the REPL |
| `/clear` | Clear conversation history |
| `/config` | Open config panel |
| `/doctor` | Check installation health |
| `/cos` | Show cost and duration |
| `/ide` | Manage IDE integrations |
| `/compact [instructions]` | Summarize conversation |
| `/mcp` | Access MCP functionality |

### Keyboard Shortcut

| Shortcut | Action |
|----------|--------|
| `Ctrl+C` | Cancel current operation |
| `Ctrl+D` | Exit Claude Code |
| `Tab` | Auto-complete |
| `Up/Down` | Navigate command history |

## Best Practices

### Performance Tips

- Use `/clear` frequently between tasks
- Limit context with `--max-turns`
- Use `/compact` for long conversations
- Specify exact tools with `--allowedTools`

### Security Tips

- Avoid `--dangerously-skip-permissions`
- Use `--disallowedTools` for dangerous commands
- Review tool permissions regularly
- Keep Claude Code updated

### Workflow Tips

- Create custom slash commands in `.claude/commands/`
- Use `--output-format json` for automation
- Pipe commands for complex workflows
- Use session IDs for long-running tasks

## 🤝 Contributing

We welcome contributions! Please see the Claude Code documentation for guidelines.

### Ways to Contribute

- 🐛 Report bugs or issues
- 📝 Improve documentation
- ✨ Add new command examples
- 🔧 Test commands and report results

## 📄 License

This cheat sheet is provided under the MIT License.

## ⭐ Support

If this cheat sheet helped you, please share it with other developers!

## Resources

For more Claude Code resources, visit the official Anthropic documentation at [https://docs.anthropic.com/en/docs/claude-code]

**Last updated**: July 2025
