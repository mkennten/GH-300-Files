# GitHub Copilot Across Environments

A comprehensive guide to using GitHub Copilot in different development environments and platforms.

## 📋 Table of Contents

1. [Overview](#overview)
2. [Visual Studio Code](#visual-studio-code)
3. [Visual Studio](#visual-studio)
4. [JetBrains IDEs](#jetbrains-ides)
5. [GitHub Copilot CLI](#github-copilot-cli)
6. [GitHub.com](#githubcom)
7. [Neovim](#neovim)
8. [Comparing Environments](#comparing-environments)
9. [Best Practices by Environment](#best-practices-by-environment)

## Overview

GitHub Copilot is available across multiple development environments, each offering unique features and workflows. Understanding the strengths of each environment helps you maximize productivity.

### Available Platforms

| Platform | Type | Key Strengths |
|----------|------|---------------|
| VS Code | Desktop IDE | Full-featured, extensive extensions |
| Visual Studio | Desktop IDE | Enterprise development, .NET focused |
| JetBrains IDEs | Desktop IDEs | Language-specific optimizations |
| Copilot CLI | Command Line | Terminal workflows, shell commands |
| GitHub.com | Web | Code review, quick edits |
| Neovim | Terminal Editor | Lightweight, keyboard-driven |

## Visual Studio Code

### Installation

```bash
# Install VS Code extensions
1. Open VS Code
2. Press Ctrl+Shift+X (Cmd+Shift+X)
3. Search "GitHub Copilot"
4. Install both:
   - GitHub Copilot
   - GitHub Copilot Chat
```

### Key Features

#### 1. Inline Suggestions

**How it works:**
- Type code naturally
- Ghost text appears automatically
- Press Tab to accept

**Example:**
```javascript
// Type this comment and press Enter:
// Function to validate email address

// Copilot suggests full implementation
```

#### 2. Copilot Chat Panel

**Open:** `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac)

**Capabilities:**
```typescript
// Ask questions about code
"How does this async function work?"

// Get suggestions
"How can I optimize this loop?"

// Generate code
"Create a React component for user profile"

// Debug issues
"Why is this returning undefined?"
```

**Slash Commands:**
```
/explain - Explain selected code
/fix - Suggest bug fixes
/tests - Generate unit tests
/help - Get help with Copilot
/clear - Clear chat history
```

#### 3. Inline Chat

**Open:** `Ctrl+I` (Windows/Linux) or `Cmd+I` (Mac)

**Quick edits without leaving code:**
```javascript
// Place cursor in function, press Ctrl+I
// Type: "Add error handling"
// Changes appear inline
```

#### 4. Quick Actions

**Right-click context menu:**
- Explain This
- Fix This
- Generate Tests
- Generate Docs

#### 5. Command Palette Integration

**Access:** `Ctrl+Shift+P` (Cmd+Shift+P)

Common commands:
```
- GitHub Copilot: Enable/Disable
- GitHub Copilot: Toggle Inline Suggestions
- GitHub Copilot: Open Chat
- GitHub Copilot: Generate Tests
```

### VS Code Settings

**Recommended configuration:**

```json
{
  // Enable Copilot
  "github.copilot.enable": {
    "*": true
  },
  
  // Inline suggestions
  "editor.inlineSuggest.enabled": true,
  
  // Auto completions
  "github.copilot.editor.enableAutoCompletions": true,
  
  // Disable for specific file types
  "github.copilot.enable": {
    "*": true,
    "yaml": false,
    "plaintext": false
  },
  
  // Chat settings
  "github.copilot.chat.localeOverride": "en"
}
```

### Keyboard Shortcuts (VS Code)

| Action | Windows/Linux | macOS |
|--------|---------------|-------|
| Accept suggestion | Tab | Tab |
| Reject suggestion | Esc | Esc |
| Next suggestion | Alt+] | Option+] |
| Previous suggestion | Alt+[ | Option+[ |
| Trigger suggestion | Alt+\ | Option+\ |
| Open Chat | Ctrl+Shift+I | Cmd+Shift+I |
| Inline Chat | Ctrl+I | Cmd+I |
| Show alternatives | Ctrl+Enter | Ctrl+Enter |

### Best Use Cases

- **Web Development**: React, Vue, Angular, Node.js
- **Python**: Django, Flask, data science
- **General Purpose**: Multi-language projects
- **API Development**: REST, GraphQL
- **TypeScript**: Full type safety support

### Extensions Compatibility

Works well with:
- ESLint / Prettier
- GitLens
- Live Share
- Debugger extensions
- Language servers

## Visual Studio

### Installation

```
1. Open Visual Studio 2022
2. Extensions > Manage Extensions
3. Search "GitHub Copilot"
4. Download and install
5. Restart Visual Studio
6. Sign in: Tools > Options > GitHub > Copilot
```

### Key Features

#### 1. Code Completions

Similar to VS Code but optimized for:
- C# development
- .NET frameworks
- ASP.NET Core
- XAML design
- Visual Basic

#### 2. Copilot Chat

**Open:** `Alt+/` (keyboard shortcut)

**Features:**
- Context-aware suggestions
- Solution-wide understanding
- Project template awareness
- NuGet package integration

#### 3. IntelliCode Integration

Combines with Visual Studio IntelliCode:
- Enhanced completion ranking
- Team completions
- Whole-line completions

### Visual Studio Shortcuts

| Action | Shortcut |
|--------|----------|
| Accept suggestion | Tab |
| Next suggestion | Alt+. |
| Previous suggestion | Alt+, |
| Accept word | Ctrl+Right Arrow |
| Open Chat | Alt+/ |
| Inline suggestions | Alt+\ |

### Best Use Cases

- **Enterprise .NET**: Large-scale C# applications
- **Desktop Apps**: WPF, WinForms, UWP
- **Game Development**: Unity projects
- **Mobile**: Xamarin applications
- **Cloud**: Azure integration

### Configuration

**Access:** Tools > Options > GitHub Copilot

**Settings:**
```
- Enable/disable Copilot
- Suggestion display options
- Language preferences
- Telemetry settings
```

## JetBrains IDEs

### Supported IDEs

- IntelliJ IDEA
- PyCharm
- WebStorm
- PhpStorm
- Rider
- GoLand
- RubyMine
- CLion
- DataGrip

### Installation

```
1. Open IDE (IntelliJ, PyCharm, etc.)
2. Settings/Preferences (Ctrl+Alt+S / Cmd+,)
3. Plugins
4. Search "GitHub Copilot"
5. Install plugin
6. Restart IDE
7. Sign in when prompted
```

### Key Features

#### 1. Language-Specific Optimization

Each IDE provides optimized suggestions:

**IntelliJ IDEA (Java):**
```java
// Understands Spring Boot patterns
// Suggests appropriate annotations
// Integrates with project structure

@RestController
@RequestMapping("/api/users")
public class UserController {
    // Copilot suggests CRUD operations
}
```

**PyCharm (Python):**
```python
# Understands Django/Flask patterns
# Suggests type hints
# Integrates with virtual env

# Django model with relationships
class BlogPost(models.Model):
    # Copilot suggests fields and Meta class
```

**WebStorm (JavaScript):**
```typescript
// React/Vue/Angular aware
// Suggests framework-specific patterns
// TypeScript type inference

// React component with hooks
const UserProfile: React.FC = () => {
    // Copilot suggests component logic
};
```

#### 2. Code Completion

**Inline suggestions:**
- Appears as you type
- Gray preview text
- Tab to accept
- Alt+] / Alt+[ for alternatives

#### 3. Copilot Chat

**Access:** Tools > Copilot > Open Chat

**Features:**
- Code explanation
- Refactoring suggestions
- Test generation
- Bug detection

### JetBrains Shortcuts

| Action | Windows/Linux | macOS |
|--------|---------------|-------|
| Accept suggestion | Tab | Tab |
| Next suggestion | Alt+] | Option+] |
| Previous suggestion | Alt+[ | Option+[ |
| Show alternatives | Alt+\ | Option+\ |
| Open Chat | Tools menu | Tools menu |

### Best Use Cases

- **Java Enterprise**: IntelliJ IDEA
- **Python Development**: PyCharm
- **Web Development**: WebStorm
- **PHP Applications**: PhpStorm
- **C# (.NET Core)**: Rider
- **Go Development**: GoLand
- **Ruby/Rails**: RubyMine

### Configuration

**Access:** Settings > Tools > GitHub Copilot

**Options:**
```
- Enable/disable suggestions
- Language-specific settings
- Show inline suggestions
- Chat preferences
```

## GitHub Copilot CLI

### Installation

```bash
# Install via npm
npm install -g @githubnext/github-copilot-cli

# Authenticate
github-copilot-cli auth

# Verify installation
github-copilot-cli --version
```

### Shell Integration

#### Bash/Zsh Setup

```bash
# Add to ~/.bashrc or ~/.zshrc
eval "$(github-copilot-cli alias -- "$0")"

# Creates these aliases:
# ?? - Command suggestions
# git? - Git command help
# gh? - GitHub CLI help
```

#### PowerShell Setup

```powershell
# Add to $PROFILE
github-copilot-cli alias -- pwsh | Out-String | Invoke-Expression
```

### Usage

#### Command Suggestions

```bash
# Ask for command suggestions
?? list all files modified in the last 24 hours

# Copilot suggests:
# find . -type f -mtime -1

# Accept suggestion and it runs
```

#### Git Commands

```bash
# Get Git command help
git? undo last commit but keep changes

# Suggests:
# git reset --soft HEAD~1
```

#### GitHub CLI

```bash
# GitHub CLI assistance
gh? create pull request with title and body

# Suggests:
# gh pr create --title "Title" --body "Description"
```

### Interactive Mode

```bash
# Start interactive session
github-copilot-cli

# Ask questions interactively
> How do I compress a directory?
# Receives suggestion
# Can execute or refine
```

### Best Use Cases

- **System Administration**: File operations, permissions
- **DevOps**: Deployment scripts, automation
- **Git Operations**: Complex git commands
- **Data Processing**: Text processing, file manipulation
- **Troubleshooting**: Finding and fixing issues

### CLI Tips

1. **Be specific**: "compress files over 1GB" vs "compress"
2. **Ask for explanations**: Prefix with "explain: "
3. **Chain commands**: Ask for complex multi-step operations
4. **Review before execution**: Always check suggested commands

## GitHub.com

### Copilot on GitHub.com

GitHub Copilot is integrated into the GitHub web interface.

### Features

#### 1. Code Review Assistance

```
# In Pull Request:
- Explain code changes
- Suggest improvements
- Identify potential issues
- Review security concerns
```

#### 2. GitHub Copilot Chat

**Access:** Click Copilot icon in:
- File editor
- Pull requests
- Issues
- Discussions

**Capabilities:**
```
- Explain code in PR
- Suggest fixes for issues
- Help write better issue descriptions
- Generate PR descriptions
- Answer questions about repository
```

#### 3. Quick File Editing

**Usage:**
1. Navigate to file on GitHub
2. Click Edit button (pencil icon)
3. Make changes with Copilot assistance
4. Commit directly

#### 4. Codespaces Integration

**Full Copilot support in GitHub Codespaces:**
- VS Code in browser
- All VS Code Copilot features
- Cloud-based development

### Best Use Cases

- **Code Review**: PR analysis and suggestions
- **Quick Fixes**: Small edits and patches
- **Documentation**: README updates
- **Issue Triage**: Understanding and responding to issues
- **Learning**: Exploring unfamiliar codebases

## Neovim

### Installation

```bash
# Install plugin using your plugin manager
# Example with vim-plug:

# Add to init.vim or init.lua
Plug 'github/copilot.vim'

# Install
:PlugInstall

# Authenticate
:Copilot setup
```

### Configuration

**Lua (init.lua):**
```lua
vim.g.copilot_no_tab_map = true
vim.api.nvim_set_keymap("i", "<C-J>", 'copilot#Accept("<CR>")', { silent = true, expr = true })

-- Disable for certain filetypes
vim.g.copilot_filetypes = {
  ["*"] = false,
  ["javascript"] = true,
  ["typescript"] = true,
  ["python"] = true,
}
```

### Keybindings

**Default:**
```
<C-]> (Ctrl+]) - Next suggestion
<C-[> (Ctrl+[) - Previous suggestion
<Tab> - Accept suggestion
```

**Custom:**
```vim
" Remap accept to Ctrl+J
imap <silent><script><expr> <C-J> copilot#Accept("\<CR>")
let g:copilot_no_tab_map = v:true
```

### Best Use Cases

- **Terminal-based Development**: Remote servers, SSH
- **Lightweight Editing**: Fast startup time
- **Keyboard-driven Workflow**: No mouse required
- **Tmux Integration**: Multiple panes with Copilot

## Comparing Environments

### Feature Matrix

| Feature | VS Code | Visual Studio | JetBrains | CLI | GitHub.com | Neovim |
|---------|---------|---------------|-----------|-----|------------|--------|
| Inline Suggestions | ✅ | ✅ | ✅ | ❌ | ⚠️ | ✅ |
| Chat Interface | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Code Explanation | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Test Generation | ✅ | ✅ | ✅ | ❌ | ⚠️ | ⚠️ |
| Multi-language | ✅ | ⚠️ | ✅ | ✅ | ✅ | ✅ |
| Offline Mode | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |

Legend: ✅ Full support | ⚠️ Limited | ❌ Not available

### Performance Comparison

**Suggestion Speed:**
- VS Code: Fast (optimized)
- Visual Studio: Fast (C# optimized)
- JetBrains: Medium (language-specific)
- Neovim: Fast (minimal UI)

**Memory Usage:**
- VS Code: ~200-500 MB
- Visual Studio: ~500-1000 MB
- JetBrains: ~500-1500 MB
- Neovim: ~50-100 MB

## Best Practices by Environment

### VS Code Best Practices

1. **Use Workspaces**: Group related projects
2. **Configure per-project**: `.vscode/settings.json`
3. **Leverage extensions**: ESLint, Prettier integration
4. **Use Chat for complex tasks**: Better than inline for architecture
5. **Enable auto-completions**: Faster suggestions

**Example Workflow:**
```typescript
// 1. Open workspace with related files
// 2. Use chat to plan implementation
// 3. Use inline suggestions for code
// 4. Use inline chat for refinements
// 5. Generate tests with /tests command
```

### Visual Studio Best Practices

1. **Solution-aware prompts**: Reference project structure
2. **Use with IntelliCode**: Combined AI benefits
3. **Leverage .NET knowledge**: Framework-specific prompts
4. **Chat for architecture**: Solution-wide decisions
5. **Quick actions integration**: Ctrl+. with Copilot

**Example Workflow:**
```csharp
// 1. Use solution explorer context
// 2. Generate interface in one file
// 3. Implement in another file
// 4. Copilot understands cross-file relationships
```

### JetBrains Best Practices

1. **Language-specific prompts**: Leverage IDE expertise
2. **Use framework templates**: Spring, Django, etc.
3. **Project structure awareness**: Reference project files
4. **Refactoring integration**: Use IDE refactoring + Copilot
5. **Database integration**: DataGrip with SQL generation

**Example Workflow:**
```python
# PyCharm workflow:
# 1. Define models in models.py
# 2. Generate views with framework knowledge
# 3. Create tests using pytest conventions
# 4. Copilot suggests Django-specific patterns
```

### CLI Best Practices

1. **Review before executing**: Always check suggestions
2. **Use for learning**: Understand commands before running
3. **Complex operations**: Break into steps
4. **Combine with man pages**: "explain command X"
5. **Save useful commands**: Create aliases

**Example Workflow:**
```bash
# 1. Ask for command suggestion
?? find all Python files and run black formatter

# 2. Review suggested command
find . -name "*.py" -exec black {} \;

# 3. Execute if safe
# 4. Save as alias if frequently used
```

### GitHub.com Best Practices

1. **Code review assistance**: Ask about PR changes
2. **Issue triage**: Generate response templates
3. **Documentation updates**: Quick README fixes
4. **PR descriptions**: Auto-generate from commits
5. **Learning codebases**: Ask about unfamiliar code

**Example Workflow:**
```
# In PR review:
# 1. Select changed code
# 2. Open Copilot chat
# 3. "Explain what this change does"
# 4. "Are there any potential issues?"
# 5. "Suggest improvements"
```

### Neovim Best Practices

1. **Configure keybindings**: Comfortable mappings
2. **Disable for some filetypes**: Avoid distractions
3. **Combine with LSP**: Language server + Copilot
4. **Terminal workflow**: Tmux + Neovim + Copilot
5. **Lightweight approach**: Use for focused coding

**Example Workflow:**
```vim
" 1. Open file in Neovim
" 2. Write comment describing function
" 3. Accept suggestion with custom key
" 4. Continue with keyboard-only workflow
```

## Multi-Environment Workflow

### Recommended Setup

**Development:**
- Primary IDE: VS Code / JetBrains (feature-rich)
- Quick edits: GitHub.com (code review)
- Terminal tasks: Copilot CLI (automation)
- Remote work: Neovim (SSH sessions)

**Example Day:**
```
Morning:
- VS Code for feature development
- Chat for architecture decisions
- Inline suggestions for implementation

Afternoon:
- GitHub.com for PR reviews
- CLI for deployment scripts
- VS Code for testing

Evening:
- Neovim on server for quick fixes
- CLI for monitoring tasks
```

## Troubleshooting Across Environments

### Common Issues

**All Environments:**
```
Issue: Suggestions not appearing
Fix:
1. Check internet connection
2. Verify subscription active
3. Restart IDE/editor
4. Check status in settings
```

**VS Code Specific:**
```
Issue: Extension conflicts
Fix:
1. Disable other AI assistants
2. Update all extensions
3. Clear extension cache
```

**JetBrains Specific:**
```
Issue: Slow suggestions
Fix:
1. Increase IDE memory (Help > Edit Custom VM Options)
2. Exclude build directories
3. Invalidate caches
```

**CLI Specific:**
```
Issue: Commands not working
Fix:
1. Reinstall CLI
2. Check shell configuration
3. Source profile again
```

## Next Steps

### Continue Learning

- [Getting Started Guide](getting-started.md)
- [Copilot Features](../cheatsheets/copilot-features.md)
- [Prompt Engineering](prompt-engineering-guide.md)
- [Responsible AI](responsible-ai.md)

### Recommended Reading

- [VS Code Copilot Docs](https://code.visualstudio.com/docs/editor/github-copilot)
- [Visual Studio Copilot](https://learn.microsoft.com/en-us/visualstudio/ide/visual-studio-github-copilot)
- [JetBrains Copilot](https://www.jetbrains.com/help/idea/github-copilot.html)
- [Copilot CLI Docs](https://githubnext.com/projects/copilot-cli)

---

**Choose the right environment for your task and maximize productivity with GitHub Copilot!**

*Each environment has unique strengths. Use the one that best fits your workflow.*
