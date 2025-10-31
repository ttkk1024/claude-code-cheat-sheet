# Claude Code Cheat Sheet (Beta)
# Claude Code 简明手册

![Alt text](images/claude-code-cheat-sheet.png)

> **Your complete guide to mastering Claude Code - from zero to hero in minutes!**
> **掌握Claude Code的完整手册 - 从小白速成大牛**

After testing Claude Code extensively, I've developed this comprehensive cheat sheet that will take you from basic to advanced user without wasting time. Whether you're completely new to Claude Code or looking to master advanced features, this guide has you covered.
经过重度测试Claude Code之后，我完成了全面的简明手册来帮助你在很短的时间之内，完成从初级用户到高级用户的转变。无论你是Claude Code的新手还是想要掌握高级功能，本指南都能满足你的需求。
## Quick Start
## 快速启动
```bash

# Windows users Windows用户
wsl

# Install Claude Code 安装Claude
npm install -g @anthropic-ai/claude-code

# Launch interactive REPL 启动交互式REPL
claude

# Check version 检查版本
claude --version
```

## 📚 Table of Contents
## 📚 目录
- 🟢 **Level 1: Basic Commands**
- 🟢 **等级 1: 基本命令**
- 🟡 **Level 2: Intermediate Commands**
- 🟡 **等级 2: 交互式命令**
- 🟠 **Level 3: Advanced Commands**
- 🟠 **等级 3: 高级命令**
- 🔴 **Level 4: Expert Commands**
- 🔴 **等级 4: 专家命令**
- 🔵 **Level 5: Power User Commands**
- 🔵 **等级 5: 强大用户命令**
- 🟣 **Level 6: Master Commands**
- 🟣 **等级 6: 大师命令**
- 🤝 **Contributing**
- 🤝 **贡献**
- 📄 **License**
- 📄 **协议**

### Pages
### 页面

- 🤖 **[Subagents](subagents.md)** - Specialized AI agents for specific development tasks
- 🤖 **[子代理](subagents.md)** - 为特定开发任务设置的AI代理

---

## 🟢 Level 1: Basic Commands
## 🟢 等级 1: 基本命令

Essential commands to get started
启动的基本命令

### Installation & Getting Started
### 安装和启动命令

```bash
# Install Claude Code  安装Claude Code
curl -sL https://install.anthropic.com | sh

# Start interactive REPL  启动交互式REPL
claude

# Start with initial prompt 带初始化提示的启动
claude "summarize this project"

# Check version 检查版本
claude --version

# Update to latest version 更新最新版
claude update
```

### Basic Navigation
### 基本导航

```bash
/help                     # Show help and available commands 显示帮助和有效命令
/exit                     # Exit the REPL 退出REPL
/clear                    # Clear conversation history 清除会话历史
/config                   # Open config panel 打开配置面板
/doctor                   # Check Claude Code installation health 检查Claude Code的安装健康度
```

### Basic File Operations
### 基本文件操作

```bash
# Print mode (SDK) - execute and exit 打印模式（SDK） - 执行和退出
claude -p "explain this function"

# Process piped content 执行管道内容
cat logs.txt | claude -p "explain"

# Continue most recent conversation 继续最近的会话
claude -c

# Continue via SDK 经由SDK继续
claude -c -p "Check for type errors"
```

### Session Management
### 会话管理


```bash
# Resume session by ID 按ID恢复会话
claude -r "abc123" "Finish this PR"

# Resume with flag 用标签恢复会话
claude --resume abc123 "query"

# Continue session 持续会话
claude --continue
```

### Keyboard Shortcuts
### 快捷键

```bash
Ctrl+C                    # Cancel current operation
Ctrl+D                    # Exit Claude Code
Tab                       # Auto-complete
Up/Down                   # Navigate command history
```

## 🟡 Level 2: Intermediate Commands
## 🟡 等级2：中级命令

Configuration and model management
配置和模型管理

### Model Configuration
### 模型配置
```bash
# Switch models 切换模型
claude --model sonnet                    # Use Sonnet model 使用sonnet模型
claude --model opus                      # Use Opus model 使用Opus模型
claude --model claude-sonnet-4-20250514  # Use specific model version 使用特定模型版本
```

### Directory Management
### 目录管理

```bash
# Add additional working directories 添加附加工作目录
claude --add-dir ../apps ../lib

# Validate directory paths 校验目录路径
claude --add-dir /path/to/project
```

### Output Formatting 
### 输出格式

```bash
# Different output formats 不同输出格式
claude -p "query" --output-format json
claude -p "query" --output-format text
claude -p "query" --output-format stream-json

# Input formatting 输入格式
claude -p --input-format stream-json
```

### Session Control
### 会话控制

```bash
# Limit conversation turns 限制会话转换
claude -p --max-turns 3 "query"

# Verbose logging 冗余日志
claude --verbose

# Session cost and duration 会话成本和持续阶段
/cos                      # Show total cost and duration
```

## 🟠 Level 3: Advanced Commands
## 🟠 等级 3: 高级命令
Tools and permission management
工具和权限管理
### Tool Management
### 工具管理

```bash
# Allow specific tools without prompting 无需提示运行使用的特定工具
claude --allowedTools "Bash(git log:*)" "Bash(git diff:*)" "Write"

# Disallow specific tools 禁止使用的特定工具
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# Prompt for specific tool permission 特定工具权限的提示
claude -p --permission-prompt-tool mcp_auth_tool "query"

# Skip all permission prompts (dangerous) 跳过所有的权限提示（危险）
claude --dangerously-skip-permissions
```

### Slash Commands - Session Management
### 斜杠命令 - 会话管理

```bash
/compact [instructions]   # Summarize conversation with optional instructions 使用可选指令摘要会话
/clear                    # Reset conversation history and context 重置会话历史和上下文
/exit                     # Exit the REPL 退出REPL
/help                     # Show available commands 显示有效命令
/config                   # Open configuration panel 打开配置面板
```

### Slash Commands - System
### 斜杠命令 - 系统
```bash
/doctor                   # Check installation health 检查安装安全度
/cos                      # Show cost and duration of current session 显示当前会话的成本和持续时间
/ide                      # Manage IDE integrations 管理IDE集成
```

## 🔴 Level 4: Expert Commands
## 🔴 等级 4：专家命令
MCP and advanced integrations
MCP和高级集成

### Model Context Protocol (MCP)
### 模型上下文协议

```bash
# Configure MCP servers 配置MCP服务器
claude --mcp

# MCP server management (via slash commands) MCP服务管理（经由斜杠命令）
/mcp                      # Access MCP functionality 访问MCP的基本功能
```

### Advanced Piping
### 高级管道

```bash
# Complex piping operations 复杂管道会话
git log --oneline | claude -p "summarize these commits"
cat error.log | claude -p "find the root cause"
ls -la | claude -p "explain this directory structure"
```

### Programmatic Usage
### 编程用法


```bash
# JSON output for scripting 针对脚本的JSON输出
claude -p "analyze code" --output-format json

# Stream JSON for real-time processing 针对实时处理的流式JSON
claude -p "large task" --output-format stream-json

# Batch processing 批处理
claude -p --max-turns 1 "quick query"
```

## 🔵 Level 5: Power User Commands
## 🔵 等级5：强大用户命令
Advanced workflows and automation
高级工作流和自动化

### Custom Slash Commands
### 自定义斜杠命令
```bash
# Create custom commands in .claude/commands/ 在.claude/commands/目录创建自定义命令
# Example: .claude/commands/debug.md 例如 ./cluade/commands/debug.md
/debug                    # Execute custom debug command 执行自定义debug命令
/test                     # Execute custom test command  执行自定义test命令
/deploy                   # Execute custom deploy command 执行自定义deploy命令
```

### Complex Tool Combinations
### 复杂工具结合

```bash
# Advanced tool permissions 高级工具权限
claude --allowedTools "Bash(git:*)" "Write" "Read" \
       --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# Multiple directory access 多目录访问
claude --add-dir ../frontend ../backend ../shared
```

### Performance Optimization
### 性能优化

```bash
# Limit context for performance 针对性能限制上下文
claude -p --max-turns 5 "focused query"

# Clear context frequently 频繁清除上下文
/clear                    # Use between tasks for better performance 针对更好性能在不同任务切换

# Compact conversations 压缩会话
/compact "keep only important parts"
```

## 🟣 Level 6: Master Commands
## 🟣 等级6：大师命令
Expert automation and custom workflows
专家自动化和自定义流程

### Advanced Configuration
### 高级配置
```bash
# Complex model and tool configuration 复杂模型和工具配置
claude --model claude-sonnet-4-20250514 \
       --add-dir ../apps ../lib ../tools \
       --allowedTools "Bash(git:*)" "Write" "Read" \
       --verbose \
       --output-format json
```

### Automation Scripts
### 自动化脚本

```bash
# Scripted Claude interactions 编写Claude集成脚本
#!/bin/bash
claude -p "analyze codebase" --output-format json > analysis.json
claude -p "generate tests" --max-turns 3 --output-format text > tests.txt
```

### Advanced Session Management
### 高级会话管理

```bash
# Session ID management 会话ID管理
SESSION_ID=$(claude -p "start analysis" --output-format json | jq -r '.session_id')
claude -r "$SESSION_ID" "continue analysis"
```

### Complex Workflows
### 复杂工作流
```bash
# Multi-step automation
claude -p "analyze project structure" | \
claude -p "suggest improvements" | \
claude -p "create implementation plan"
```

---

## 🟤 Level 7: Workflow Automation
## 🟤 等级7 ： 工作流自动化
Advanced automation patterns and multi-step processes
高级自动化模式和多步骤流程

### Automated Code Review Workflows
### 自动化编码复查工作流
```bash
# Automated PR review process
#!/bin/bash
git diff HEAD~1 | claude -p "review this PR for security issues" > security_review.md
git diff HEAD~1 | claude -p "check for performance issues" > performance_review.md
git diff HEAD~1 | claude -p "suggest improvements" > improvements.md
```

### Continuous Integration Integration
### 持续集成的集成
```bash
# CI/CD pipeline integration
claude -p "analyze test coverage" --output-format json | jq '.coverage_percentage'
claude -p "generate release notes from commits" --max-turns 2 > RELEASE_NOTES.md
```

### Batch Processing Workflows
### 批处理工作流
```bash
# Process multiple files 处理多个文件
find . -name "*.js" -exec claude -p "analyze this file for bugs: {}" \; > bug_report.txt

# Automated documentation generation 自动化文档生成
for file in src/*.py; do
    claude -p "generate docstring for $file" --output-format text >> docs.md
done
```

---

## ⚫ Level 8: Integration & Ecosystem
## ⚫ 等级 8： 集成&生态
IDE integrations, Git workflows, and third-party tool connections
IDE集成，Git工作流， 和第三方工具连接

### IDE Integration Commands
### IDE集成命令
```bash
# VS Code integration VS Code 集成
/ide vscode                # Configure VS Code integration 配置VS Code集成
/ide configure             # Setup IDE configurations 设置IDE配置

# Custom IDE commands 自定义IDE命令
claude --ide-mode "explain selected code"
claude --ide-mode "refactor this function"
```

### Git Workflow Integration
### Git 工作流集成

```bash
# Git hooks integration Git勾起集成
claude -p "create pre-commit hook for code quality" > .git/hooks/pre-commit

# Advanced Git operations 高级Git操作
git log --oneline -10 | claude -p "create changelog from these commits"
git diff --name-only | claude -p "explain what changed in this commit"
```

### Third-Party Tool Connections
### 第三方工具集成

```bash
# Database integration 数据库集成
mysql -e "SHOW TABLES" | claude -p "analyze database structure"

# Docker integration Docker集成
docker ps | claude -p "analyze running containers"
docker logs container_name | claude -p "find errors in logs"
```

---

## ⚪ Level 9: Performance & Optimization
## ⚪ 等级 9： 性能&优化
Advanced performance tuning, resource management, and efficiency tips
高级性能调试， 资源管理，和性能技巧

### Memory & Resource Management
### 内存&资源管理

```bash
# Optimize memory usage 优化内存使用
claude -p --max-turns 1 "quick analysis"      # Single turn for efficiency 针对效率单个转换
claude -p --compact-mode "analyze with minimal context"

# Resource monitoring 资源监控
/cos                       # Check current session costs 检查当前会话成本
/doctor --performance      # Performance diagnostics 性能诊断
```

### Caching & Optimization
### 缓存和优化

```bash
# Efficient session reuse 高效会话恢复
claude -c "continue previous analysis"         # Reuse existing context 重用存在的会话
claude --cache-results "repetitive task"      # Cache common operations 缓存通用操作

# Parallel processing 并行处理
claude -p "task 1" & claude -p "task 2" & wait  # Parallel execution 并行处理
```

### Large-Scale Processing
## 大规模处理

```bash
# Handle large codebases efficiently 搞好处理大型代码库
claude --add-dir . --max-context 50000 "analyze entire project"
claude --stream-output "process large dataset" | head -100
```

---

## 🔘 Level 10: Enterprise & Production
## 🔘 等级 10: 企业级和生产级

Production-ready configurations, team workflows, and enterprise features
生成级别准备的配置，团体工作流，和企业特性

### Team Collaboration
### 团队合作

```bash
# Shared team configurations 共享团队配置
claude --config-file team-config.json "standardized analysis"

# Team session sharing 团队会话共享
claude -r "team-session-id" "continue team discussion"
```

### Production Environment Setup
### 生成环境设置

```bash
# Production-ready configuration 生成级别的配置
claude --production-mode \
       --security-enabled \
       --audit-logging \
       --max-turns 10 \
       "production analysis"
```

### Enterprise Security
### 企业安全

```bash
# Security-focused operations 聚焦安全的操作
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)" "Bash(chmod:*)" \
       --audit-mode \
       --no-external-calls \
       "secure code review"
```

### Monitoring & Compliance
### 监控和合规

```bash
# Audit and compliance 审计和合规
claude --audit-log /var/log/claude-audit.log "compliance check"
claude --compliance-mode "analyze for security compliance"
```

## Command Reference Tables
## 命令参考表

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
我们欢迎贡献！请查看Claude Code文档以获取指导。

### Ways to Contribute

- 🐛 Report bugs or issues 报告错误或问题
- 📝 Improve documentation 改进文档
- ✨ Add new command examples 添加新的命令示例
- 🔧 Test commands and report results 测试命令并报告结果

## 📄 License

This cheat sheet is provided under the MIT License.
本简明手册在MIT许可证下提供。

## ⭐ Support

If this cheat sheet helped you, please share it with other developers!
如果这个简明手册帮助了你，请分享给其他开发者！
If this cheat sheet helped you master Claude Code, please:
如果这个简明手册帮助你掌握了Claude Code，请：

- ⭐ Star our GitHub repository ⭐ 在GitHub上给我们加星
- 📢 Share it with other developers 📢 与其他开发者分享
- 💬 Leave feedback in the comments 💬 在评论中留下反馈
- 🔄 Follow for updates 🔄 关注更新

## Resources & Further Learning

For more Claude Code resources, visit the official Anthropic documentation at
更多Claude Code资源，请访问官方Anthropic文档：

- [Official Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Claude Code GitHub Repository](https://github.com/anthropic-ai/claude-code)
- [Anthropic API Documentation](https://docs.anthropic.com)
- [MCP Documentation](https://docs.anthropic.com/en/docs/build-with-claude/mcp)

**Last updated**: July 2025
**最后更新**: 2025年7月
