# Claude Code Cheat Sheet (Beta)

![Alt text](images/claude-code-cheat-sheet.png)

> **Your complete guide to mastering Claude Code - from zero to hero in minutes!**

After testing Claude Code extensively, I've developed this comprehensive cheat sheet that will take you from basic to advanced user without wasting time. Whether you're completely new to Claude Code or looking to master advanced features, this guide has you covered.

## Quick Start

```bash

# Windows users
wsl

# Install Claude Code
npm install -g @anthropic-ai/claude-code

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

### Pages

- 🤖 **[Subagents](subagents.md)** - Specialized AI agents for specific development tasks

---

## 🟢 Level 1: Basic Commands

Essential commands to get started

### Installation & Getting Started

```bash
# Install Claude Code
curl -sL https://install.anthropic.com | sh

# Start interactive REPL
claude

# Start with initial prompt
claude "summarize this project"

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
claude --mcp

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

---

## 🟤 Level 7: Workflow Automation

Advanced automation patterns and multi-step processes

### Automated Code Review Workflows

```bash
# Automated PR review process
#!/bin/bash
git diff HEAD~1 | claude -p "review this PR for security issues" > security_review.md
git diff HEAD~1 | claude -p "check for performance issues" > performance_review.md
git diff HEAD~1 | claude -p "suggest improvements" > improvements.md
```

### Continuous Integration Integration

```bash
# CI/CD pipeline integration
claude -p "analyze test coverage" --output-format json | jq '.coverage_percentage'
claude -p "generate release notes from commits" --max-turns 2 > RELEASE_NOTES.md
```

### Batch Processing Workflows

```bash
# Process multiple files
find . -name "*.js" -exec claude -p "analyze this file for bugs: {}" \; > bug_report.txt

# Automated documentation generation
for file in src/*.py; do
    claude -p "generate docstring for $file" --output-format text >> docs.md
done
```

---

## ⚫ Level 8: Integration & Ecosystem

IDE integrations, Git workflows, and third-party tool connections

### IDE Integration Commands

```bash
# VS Code integration
/ide vscode                # Configure VS Code integration
/ide configure             # Setup IDE configurations

# Custom IDE commands
claude --ide-mode "explain selected code"
claude --ide-mode "refactor this function"
```

### Git Workflow Integration

```bash
# Git hooks integration
claude -p "create pre-commit hook for code quality" > .git/hooks/pre-commit

# Advanced Git operations
git log --oneline -10 | claude -p "create changelog from these commits"
git diff --name-only | claude -p "explain what changed in this commit"
```

### Third-Party Tool Connections

```bash
# Database integration
mysql -e "SHOW TABLES" | claude -p "analyze database structure"

# Docker integration
docker ps | claude -p "analyze running containers"
docker logs container_name | claude -p "find errors in logs"
```

---

## ⚪ Level 9: Performance & Optimization

Advanced performance tuning, resource management, and efficiency tips

### Memory & Resource Management

```bash
# Optimize memory usage
claude -p --max-turns 1 "quick analysis"      # Single turn for efficiency
claude -p --compact-mode "analyze with minimal context"

# Resource monitoring
/cost                      # Check current session costs
/doctor --performance      # Performance diagnostics
```

### Caching & Optimization

```bash
# Efficient session reuse
claude -c "continue previous analysis"         # Reuse existing context
claude --cache-results "repetitive task"      # Cache common operations

# Parallel processing
claude -p "task 1" & claude -p "task 2" & wait  # Parallel execution
```

### Large-Scale Processing

```bash
# Handle large codebases efficiently
claude --add-dir . --max-context 50000 "analyze entire project"
claude --stream-output "process large dataset" | head -100
```

---

## 🔘 Level 10: Enterprise & Production

Production-ready configurations, team workflows, and enterprise features

### Team Collaboration

```bash
# Shared team configurations
claude --config-file team-config.json "standardized analysis"

# Team session sharing
claude -r "team-session-id" "continue team discussion"
```

### Production Environment Setup

```bash
# Production-ready configuration
claude --production-mode \
       --security-enabled \
       --audit-logging \
       --max-turns 10 \
       "production analysis"
```

### Enterprise Security

```bash
# Security-focused operations
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)" "Bash(chmod:*)" \
       --audit-mode \
       --no-external-calls \
       "secure code review"
```

### Monitoring & Compliance

```bash
# Audit and compliance
claude --audit-log /var/log/claude-audit.log "compliance check"
claude --compliance-mode "analyze for security compliance"
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

## Best Practices by Level

### Beginner Best Practices (Levels 1-3)

- Start with basic commands and gradually progress
- Use `/help` frequently to discover new features
- Practice with simple queries before complex ones
- Keep sessions focused with `/clear` between tasks

### Intermediate Best Practices (Levels 4-6)

- Master tool permissions for security
- Use JSON output for automation scripts
- Learn MCP for advanced integrations
- Create custom slash commands for repeated tasks

### Advanced Best Practices (Levels 7-10)

- Implement automated workflows for repetitive tasks
- Use enterprise features for team collaboration
- Monitor performance and optimize resource usage
- Follow security best practices in production

## Pro Tips & Tricks

### Efficiency Tips

- Use `Ctrl+C` to cancel long-running operations
- Combine multiple flags for complex configurations
- Use piping for multi-step data processing
- Cache common operations for better performance

### Security Pro Tips

- Always use `--disallowedTools` for dangerous commands
- Enable audit logging in production environments
- Review tool permissions regularly
- Use `--security-enabled` for sensitive operations

### Workflow Pro Tips

- Create templates for common automation patterns
- Use session IDs for long-running collaborative tasks
- Implement proper error handling in automation scripts
- Document custom workflows for team sharing

## Troubleshooting Common Issues

### Installation Issues

```bash
# Check installation
claude --version
claude /doctor

# Reinstall if needed
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code
```

### Performance Issues

```bash
# Clear context for better performance
/clear

# Limit context size
claude -p --max-turns 3 "focused query"

# Use compact mode
/compact "keep only essentials"
```

### Permission Issues

```bash
# Check current permissions
claude --list-permissions

# Reset permissions
claude --reset-permissions

# Configure specific permissions
claude --allowedTools "Bash(git:*)" --disallowedTools "Bash(rm:*)"
```

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
If this cheat sheet helped you master Claude Code, please:

- ⭐ Star our GitHub repository
- 📢 Share it with other developers
- 💬 Leave feedback in the comments
- 🔄 Follow for updates

## Resources & Further Learning

For more Claude Code resources, visit the official Anthropic documentation at

- [Official Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Claude Code GitHub Repository](https://github.com/anthropic-ai/claude-code)
- [Anthropic API Documentation](https://docs.anthropic.com)
- [MCP Documentation](https://docs.anthropic.com/en/docs/build-with-claude/mcp)

**Last updated**: July 2025
