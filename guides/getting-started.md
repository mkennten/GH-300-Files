# Getting Started with GitHub Copilot

A comprehensive guide to installing, configuring, and using GitHub Copilot for the first time.

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Getting Access](#getting-access)
3. [Installation](#installation)
4. [First Steps](#first-steps)
5. [Your First Code Generation](#your-first-code-generation)
6. [Understanding Copilot Behavior](#understanding-copilot-behavior)
7. [Troubleshooting](#troubleshooting)

## Prerequisites

Before you begin, ensure you have:

- **GitHub Account**: Active GitHub account (free or paid)
- **GitHub Copilot Subscription**: Individual, Business, or Enterprise
- **Supported IDE**: One of the following:
  - Visual Studio Code (1.74.0 or later)
  - Visual Studio 2022 (17.4 or later)
  - JetBrains IDEs (2022.3 or later)
  - Neovim (0.6 or later)
  - Other supported editors

- **Internet Connection**: Required for Copilot to function
- **Programming Knowledge**: Basic understanding of at least one programming language

## Getting Access

### Step 1: Sign Up for GitHub Copilot

1. **Visit GitHub Copilot page**: https://github.com/features/copilot
2. **Choose a plan**:
   - **Individual**: Personal use ($10/month or $100/year)
   - **Business**: Team use ($19/user/month)
   - **Enterprise**: Large organizations (custom pricing)
   - **Free**: Students, teachers, and open source maintainers

3. **Start Free Trial**: 30-day free trial available for new users

### Step 2: Verify Access

1. Go to https://github.com/settings/copilot
2. You should see your subscription status
3. Configure settings if needed:
   - Suggestions matching public code
   - Telemetry preferences
   - Editor settings

### For Students and Teachers

Free access available through GitHub Education:

1. Visit: https://education.github.com
2. Apply for Student Developer Pack or Teacher Benefits
3. Verify your academic status
4. Access Copilot from your account settings

## Installation

### Visual Studio Code

#### Method 1: Extension Marketplace

1. Open VS Code
2. Click Extensions icon (Ctrl+Shift+X / Cmd+Shift+X)
3. Search for "GitHub Copilot"
4. Click "Install" on these extensions:
   - **GitHub Copilot** (code completions)
   - **GitHub Copilot Chat** (chat interface)
5. Click "Sign in to GitHub" when prompted
6. Authorize in your browser
7. Return to VS Code

#### Method 2: Command Palette

1. Open Command Palette (Ctrl+Shift+P / Cmd+Shift+P)
2. Type: "Extensions: Install Extensions"
3. Search for "GitHub Copilot"
4. Install and authenticate

#### Verify Installation

1. Check bottom right of VS Code status bar
2. Look for Copilot icon
3. Icon shows: ✓ (active) or × (inactive)
4. Click icon to see status details

### Visual Studio 2022

1. Open Visual Studio
2. Go to **Extensions > Manage Extensions**
3. Search for "GitHub Copilot"
4. Click "Download"
5. Close Visual Studio to start installation
6. Reopen Visual Studio
7. Sign in: **Tools > Options > GitHub > Copilot**
8. Authenticate with GitHub

### JetBrains IDEs (IntelliJ, PyCharm, WebStorm, etc.)

1. Open your JetBrains IDE
2. Go to **Settings/Preferences** (Ctrl+Alt+S / Cmd+,)
3. Navigate to **Plugins**
4. Search for "GitHub Copilot"
5. Click "Install"
6. Restart IDE
7. Sign in when prompted

### GitHub Copilot CLI

Install command-line interface:

```bash
# Install via npm
npm install -g @githubnext/github-copilot-cli

# Authenticate
github-copilot-cli auth

# Verify
github-copilot-cli --version
```

## First Steps

### 1. Verify Copilot is Active

**VS Code:**
- Check status bar for Copilot icon
- Icon should show checkmark (✓)
- Click icon to see details

**Visual Studio:**
- Check status bar bottom right
- Look for "Copilot" indicator

**JetBrains:**
- Check bottom status bar
- Copilot icon should be visible

### 2. Configure Basic Settings

**VS Code Settings (settings.json):**

```json
{
  "github.copilot.enable": {
    "*": true
  },
  "editor.inlineSuggest.enabled": true,
  "github.copilot.editor.enableAutoCompletions": true
}
```

**Access Settings:**
- File > Preferences > Settings (Ctrl+,)
- Search for "Copilot"
- Adjust preferences

### 3. Create a Test File

Create a simple test file to try Copilot:

**JavaScript/TypeScript:**
```javascript
// test.js or test.ts
```

**Python:**
```python
# test.py
```

**Java:**
```java
// Test.java
```

## Your First Code Generation

### Exercise 1: Simple Function

Let's generate your first function with Copilot!

1. **Open your test file**

2. **Write a comment describing what you want:**

```python
# Function to calculate the area of a circle
# Parameter: radius (float)
# Returns: area (float)
```

3. **Press Enter and wait**
   - Copilot will suggest a function
   - You'll see ghost text (gray)

4. **Review the suggestion:**
```python
def calculate_circle_area(radius):
    import math
    return math.pi * radius ** 2
```

5. **Accept the suggestion:**
   - Press **Tab** to accept
   - Or **Esc** to reject

6. **Test the generated code:**
```python
# Test it
print(calculate_circle_area(5))  # Should print ~78.54
```

### Exercise 2: Multiple Suggestions

Try getting alternative suggestions:

1. **Write the same comment again:**
```javascript
// Function to reverse a string
```

2. **Wait for initial suggestion**

3. **View alternatives:**
   - Press **Alt+]** (Windows/Linux) or **Option+]** (Mac) for next
   - Press **Alt+[** (Windows/Linux) or **Option+[** (Mac) for previous

4. **Or see all 10 suggestions:**
   - Press **Ctrl+Enter** (Windows/Linux/Mac)
   - A panel opens with all suggestions
   - Click to select one

### Exercise 3: Using Copilot Chat

1. **Open Copilot Chat:**
   - Press **Ctrl+Shift+I** (Cmd+Shift+I on Mac)
   - Or click Chat icon in sidebar

2. **Ask a question:**
```
"How do I read a JSON file in Python?"
```

3. **Review the response:**
   - Copilot provides code example
   - Includes explanations
   - Suggests best practices

4. **Try follow-up questions:**
```
"Now add error handling to that code"
```

### Exercise 4: Inline Chat

1. **Place cursor in your code**

2. **Open inline chat:**
   - Press **Ctrl+I** (Cmd+I on Mac)

3. **Type a request:**
```
"Add type hints to this function"
```

4. **Review and accept changes:**
   - Changes appear inline
   - Click Accept or Reject

## Understanding Copilot Behavior

### How Copilot Works

**Input Processing:**
- Reads current file content
- Considers open files in editor
- Analyzes cursor position
- Reviews recent changes

**Context Window:**
- ~8000 tokens of context
- Includes comments and code
- Prioritizes nearby code
- Considers file type and language

**Suggestion Generation:**
- Uses OpenAI Codex model
- Trained on public code
- Generates multiple options
- Ranks by relevance

### What Influences Suggestions

**Quality Factors:**

1. **Clear Comments**
   - Detailed descriptions
   - Expected inputs/outputs
   - Edge cases mentioned

2. **Context Richness**
   - Existing code structure
   - Import statements
   - Variable names
   - Code patterns

3. **File Type**
   - Correct extension (.py, .js, etc.)
   - Proper syntax
   - Language conventions

4. **Coding Style**
   - Consistent formatting
   - Naming conventions
   - Project patterns

### What Copilot Knows

**Copilot Can:**
- Generate functions and classes
- Write tests
- Add documentation
- Fix syntax errors
- Complete repetitive code
- Suggest algorithms
- Work with frameworks

**Copilot Cannot:**
- Access your local files (except open in editor)
- Read your secrets or environment variables
- Execute code
- Access external databases
- Browse the internet
- Remember between sessions (unless in current context)

### Response Time

**Typical delays:**
- Instant completions: Common patterns
- 1-2 seconds: Complex functions
- 3-5 seconds: Large code blocks
- May vary with connection speed

**If slow:**
- Check internet connection
- Reduce open files
- Restart IDE
- Check Copilot status

## Troubleshooting

### Copilot Not Showing Suggestions

**Check List:**

1. **Verify Activation**
   - Check status bar icon
   - Should show ✓ not ×
   - Click icon for details

2. **Check Subscription**
   - Visit: github.com/settings/copilot
   - Ensure subscription is active
   - Verify payment if needed

3. **Enable Suggestions**
```json
// VS Code settings.json
{
  "github.copilot.enable": {
    "*": true
  },
  "editor.inlineSuggest.enabled": true
}
```

4. **Restart IDE**
   - Close completely
   - Reopen
   - Wait for Copilot to initialize

5. **Re-authenticate**
   - Sign out of GitHub
   - Sign back in
   - Authorize Copilot

### Poor Quality Suggestions

**Improvement Steps:**

1. **Add More Context**
   - Write detailed comments
   - Include examples
   - Show expected format

2. **Improve Naming**
   - Use descriptive names
   - Follow conventions
   - Be consistent

3. **Provide Examples**
```python
# Format phone numbers
# Example: "1234567890" -> "(123) 456-7890"
```

4. **Split Complex Tasks**
   - Break into smaller functions
   - Generate piece by piece
   - Refine iteratively

### Extension Issues

**VS Code Problems:**

1. **Update Extension**
   - Extensions view
   - Check for updates
   - Install latest version

2. **Clear Extension Cache**
```bash
# Close VS Code
# Delete cache (Windows)
rd /s /q "%APPDATA%\Code\User\globalStorage\github.copilot"

# Delete cache (Mac/Linux)
rm -rf ~/.config/Code/User/globalStorage/github.copilot
```

3. **Reinstall Extension**
   - Uninstall Copilot
   - Restart VS Code
   - Reinstall from marketplace

### Network Issues

**Connection Problems:**

1. **Check Firewall**
   - Allow VS Code through firewall
   - Whitelist api.github.com
   - Check proxy settings

2. **Proxy Configuration**
```json
// VS Code settings.json
{
  "http.proxy": "http://proxy.company.com:8080",
  "http.proxyStrictSSL": false
}
```

3. **VPN Issues**
   - Try disconnecting VPN
   - Check VPN allows GitHub API
   - Contact IT if corporate VPN

## Next Steps

### Continue Learning

1. **Read Cheat Sheets:**
   - [Copilot Basics](../cheatsheets/copilot-basics.md)
   - [Prompt Engineering](../cheatsheets/prompt-engineering.md)
   - [Copilot Features](../cheatsheets/copilot-features.md)

2. **Practice Exercises:**
   - Complete [Exercises](../cheatsheets/exercises.md)
   - Start with Level 1
   - Progress gradually

3. **Explore Advanced Features:**
   - Try Copilot Chat
   - Use inline chat
   - Generate tests

4. **Learn Best Practices:**
   - [Responsible AI Guide](responsible-ai.md)
   - [Prompt Engineering Guide](prompt-engineering-guide.md)
   - [Copilot Across Environments](copilot-across-environments.md)

### Join the Community

- [GitHub Community Discussions](https://github.com/orgs/community/discussions/categories/copilot)
- [Stack Overflow - github-copilot tag](https://stackoverflow.com/questions/tagged/github-copilot)
- [GitHub Blog](https://github.blog/tag/github-copilot/)

### Get Help

- **Documentation**: https://docs.github.com/en/copilot
- **Support**: https://support.github.com
- **Feedback**: Copilot icon > "Send Feedback"

## Quick Reference Card

**Essential Shortcuts (VS Code):**

| Action | Shortcut |
|--------|----------|
| Accept | Tab |
| Reject | Esc |
| Next suggestion | Alt+] (Option+]) |
| Previous | Alt+[ (Option+[) |
| Open Chat | Ctrl+Shift+I (Cmd+Shift+I) |
| Inline Chat | Ctrl+I (Cmd+I) |
| All suggestions | Ctrl+Enter |

**First Steps:**
1. ✓ Install extension
2. ✓ Sign in to GitHub
3. ✓ Verify active status
4. ✓ Write comment
5. ✓ Accept suggestion
6. ✓ Test generated code

---

**Congratulations!** You're now ready to use GitHub Copilot effectively. Practice regularly, and you'll become proficient in AI-assisted development!

*For questions or issues, refer to the [Troubleshooting](#troubleshooting) section or visit the [GitHub Copilot documentation](https://docs.github.com/en/copilot).*
