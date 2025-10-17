# GitHub Copilot Basics Cheat Sheet

Quick reference for essential GitHub Copilot commands, shortcuts, and basic usage patterns.

## 🚀 Getting Started

### Installation

**VS Code:**
```
1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X / Cmd+Shift+X)
3. Search for "GitHub Copilot"
4. Install and sign in with your GitHub account
```

**Visual Studio:**
```
1. Go to Extensions > Manage Extensions
2. Search for "GitHub Copilot"
3. Download and install
4. Restart Visual Studio and sign in
```

**JetBrains IDEs:**
```
1. Go to Settings/Preferences > Plugins
2. Search for "GitHub Copilot"
3. Install and restart IDE
4. Sign in with your GitHub account
```

## ⌨️ Keyboard Shortcuts

### VS Code

| Action | Windows/Linux | macOS |
|--------|---------------|-------|
| Accept suggestion | `Tab` | `Tab` |
| Dismiss suggestion | `Esc` | `Esc` |
| Next suggestion | `Alt+]` | `Option+]` |
| Previous suggestion | `Alt+[` | `Option+[` |
| Trigger suggestion | `Alt+\` | `Option+\` |
| Open Copilot Chat | `Ctrl+Shift+I` | `Cmd+Shift+I` |
| Inline Chat | `Ctrl+I` | `Cmd+I` |
| Show 10 suggestions | `Ctrl+Enter` | `Ctrl+Enter` |

### Visual Studio

| Action | Shortcut |
|--------|----------|
| Accept suggestion | `Tab` |
| Next suggestion | `Alt+.` |
| Previous suggestion | `Alt+,` |
| Accept word | `Ctrl+Right Arrow` |
| Open Copilot Chat | `Alt+/` |

### JetBrains IDEs

| Action | Windows/Linux | macOS |
|--------|---------------|-------|
| Accept suggestion | `Tab` | `Tab` |
| Next suggestion | `Alt+]` | `Option+]` |
| Previous suggestion | `Alt+[` | `Option+[` |
| Show alternatives | `Alt+\` | `Option+\` |

## 💻 Basic Usage Patterns

### 1. Function Generation

**Pattern:** Write a descriptive comment, then press Enter

```javascript
// Function to calculate the factorial of a number
// [Copilot will suggest the implementation]
```

### 2. Code Completion

**Pattern:** Start typing, let Copilot complete

```python
def fibonacci(n):
    # Start typing 'if' and Copilot suggests the rest
```

### 3. Test Generation

**Pattern:** Write a test name, get implementation

```typescript
// Test: should validate email format
test('should validate email format', () => {
    // Copilot suggests test implementation
});
```

### 4. Documentation

**Pattern:** Add comment starter, get full documentation

```java
/**
 * [Copilot suggests JavaDoc]
 */
public void processPayment(double amount) {
    // implementation
}
```

## 🎯 Language Support

### Highly Supported Languages
- Python
- JavaScript/TypeScript
- Java
- C#
- C/C++
- Go
- Ruby
- PHP

### Good Support
- Swift
- Kotlin
- Rust
- Scala
- R
- Shell scripts

### Supported Frameworks & Libraries
- React, Vue, Angular
- Node.js, Express
- Django, Flask
- Spring Boot
- .NET Core
- And many more...

## 🔧 Configuration

### Enable/Disable Copilot

**VS Code:**
```
1. Click Copilot icon in status bar, or
2. Command Palette: "GitHub Copilot: Enable/Disable"
```

**Disable for specific languages:**
```json
// settings.json
{
  "github.copilot.enable": {
    "*": true,
    "yaml": false,
    "plaintext": false
  }
}
```

### Advanced Settings

```json
// VS Code settings.json
{
  "github.copilot.inlineSuggest.enable": true,
  "editor.inlineSuggest.enabled": true,
  "github.copilot.editor.enableAutoCompletions": true
}
```

## 💬 Copilot Chat Basics

### Chat Commands

| Command | Description |
|---------|-------------|
| `/explain` | Explain selected code |
| `/fix` | Suggest fixes for problems |
| `/tests` | Generate unit tests |
| `/help` | Get help with Copilot |
| `/clear` | Clear chat history |

### Using Chat

```
1. Select code
2. Right-click > Copilot > Explain This
   Or: Open Chat and ask questions
```

**Example Questions:**
- "How does this function work?"
- "Can you optimize this code?"
- "What are potential bugs here?"
- "Generate tests for this class"

## 🎨 Inline Chat

**Quick edits without leaving your code:**

```
1. Place cursor in code
2. Press Ctrl+I (Cmd+I on Mac)
3. Type your request:
   - "Add error handling"
   - "Add comments"
   - "Refactor to use async/await"
```

## ⚡ Quick Tips

### Getting Better Suggestions

1. **Write clear comments**
   ```python
   # Calculate compound interest with principal, rate, and time
   ```

2. **Provide context**
   ```javascript
   // Using the User class defined above
   // Create a function to validate user credentials
   ```

3. **Use descriptive names**
   ```java
   // Good: calculateMonthlyPayment
   // Bad: calc
   ```

4. **Include examples**
   ```python
   # Parse date string (e.g., "2024-01-15") to datetime object
   ```

### Accepting Suggestions

- **Tab**: Accept entire suggestion
- **Ctrl+Right Arrow**: Accept next word
- **Esc**: Reject suggestion
- **Keep typing**: Refine the suggestion

## 🚫 Common Issues

### Copilot Not Working?

1. **Check Status Bar**: Ensure Copilot icon shows as active
2. **Check Subscription**: Verify your GitHub Copilot subscription is active
3. **Restart IDE**: Sometimes a restart resolves connection issues
4. **Check Internet**: Copilot requires internet connection
5. **Sign Out/In**: Try signing out and back in to GitHub

### Poor Suggestions?

1. **Add more context**: Include comments and surrounding code
2. **Be specific**: Clear, detailed prompts work better
3. **Try different wording**: Rephrase your comment
4. **Provide examples**: Show the expected format
5. **Use appropriate language**: Ensure correct file extension

## 📊 Monitoring Usage

### View Copilot Activity

**VS Code:**
```
1. Click Copilot icon in status bar
2. View "Copilot: Show Output"
```

### Telemetry

```json
// Disable telemetry (settings.json)
{
  "github.copilot.telemetry": false
}
```

## 🔒 Privacy & Security

### What Copilot Sends

- Current file content
- Related open files
- Cursor position
- File type and path

### What Copilot Doesn't Send

- Other files not in your workspace
- Your local secrets or credentials
- Corporate network data

### Best Practices

- ✅ Review all generated code
- ✅ Don't include secrets in prompts
- ✅ Validate security implications
- ✅ Check license compatibility
- ❌ Don't blindly accept suggestions
- ❌ Don't commit without review

## 📚 Next Steps

1. **Practice**: Try generating different types of code
2. **Experiment**: Test different prompting styles
3. **Learn Prompt Engineering**: Check out [prompt-engineering.md](prompt-engineering.md)
4. **Explore Advanced Features**: See [copilot-features.md](copilot-features.md)
5. **Read Responsible AI Guide**: Review [../guides/responsible-ai.md](../guides/responsible-ai.md)

## 🔗 Resources

- [Official Documentation](https://docs.github.com/en/copilot)
- [VS Code Extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
- [Community Forum](https://github.com/orgs/community/discussions/categories/copilot)
- [Getting Started Guide](../guides/getting-started.md)

---

*Keep this cheat sheet handy as you start your journey with GitHub Copilot!*
