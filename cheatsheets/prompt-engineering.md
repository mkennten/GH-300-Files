# Prompt Engineering for GitHub Copilot - Cheat Sheet

Quick reference for crafting effective prompts to get the best results from GitHub Copilot.

## 🎯 Core Principles

### The 4 C's of Effective Prompts

1. **Clear**: Be explicit about what you want
2. **Concise**: Avoid unnecessary information
3. **Contextual**: Provide relevant surrounding code
4. **Consistent**: Use consistent naming and style

## 📝 Prompt Structure

### Basic Comment Pattern

```javascript
// [Action] [What] [How/Constraints]
// Calculate monthly payment using compound interest formula
```

### Detailed Pattern

```python
# Function: calculateTax
# Input: income (float), tax_rate (float)
# Output: tax_amount (float)
# Description: Calculate tax with progressive rates
```

## ✅ Effective Prompt Examples

### Function Generation

**❌ Poor:**
```javascript
// function to get data
```

**✅ Good:**
```javascript
// Function to fetch user data from API endpoint
// Parameters: userId (string)
// Returns: Promise<User> object with name, email, and role
// Handles errors with try-catch
```

### Class Creation

**❌ Poor:**
```python
# make a user class
```

**✅ Good:**
```python
# User class with properties: username, email, created_at
# Methods: validate_email(), to_json(), from_json()
# Include type hints and docstrings
```

### Algorithm Implementation

**❌ Poor:**
```java
// sort function
```

**✅ Good:**
```java
// Implement quicksort algorithm for integer array
// Use Lomuto partition scheme
// Include helper method for partitioning
// Time complexity: O(n log n) average case
```

## 🎨 Prompt Patterns

### 1. Test-Driven Development

**Pattern:** Write test first, generate implementation

```typescript
// Test for email validation
describe('EmailValidator', () => {
  it('should accept valid email addresses', () => {
    expect(isValidEmail('user@example.com')).toBe(true);
  });
  
  it('should reject invalid email addresses', () => {
    expect(isValidEmail('invalid.email')).toBe(false);
  });
});

// Now write the implementation comment
// Implement isValidEmail function based on tests above
```

### 2. Example-Driven Generation

**Pattern:** Provide examples of input/output

```python
# Function to format phone numbers
# Examples:
# "1234567890" -> "(123) 456-7890"
# "123-456-7890" -> "(123) 456-7890"
# "+1-123-456-7890" -> "+1 (123) 456-7890"
```

### 3. Step-by-Step Instructions

**Pattern:** Break down complex tasks

```javascript
// Function to process user registration:
// 1. Validate email format
// 2. Check if email already exists in database
// 3. Hash password using bcrypt
// 4. Create user record
// 5. Send welcome email
// 6. Return user object or error
```

### 4. Constraint-Based Prompts

**Pattern:** Specify requirements and limitations

```java
// Parse CSV file with following constraints:
// - Handle quoted fields with commas
// - Support escaped quotes
// - Trim whitespace from fields
// - Skip empty lines
// - Return List<Map<String, String>>
```

### 5. By-Example Pattern

**Pattern:** Show the pattern you want to follow

```typescript
// Existing pattern:
const fetchUsers = async () => {
  try {
    const response = await api.get('/users');
    return response.data;
  } catch (error) {
    logger.error('Failed to fetch users', error);
    throw error;
  }
};

// Create similar function for fetching posts
```

## 🧠 Context Management

### Include Relevant Code

```typescript
interface User {
  id: string;
  name: string;
  email: string;
}

// Function to create a new user from form data
// Use the User interface defined above
```

### Reference Previous Definitions

```python
# Using the DatabaseConnection class from db.py
# Create a function to execute parameterized queries
# Return results as list of dictionaries
```

### Specify Dependencies

```javascript
// Using axios for HTTP requests
// Using lodash for array manipulation
// Function to batch API requests and merge results
```

## 🎯 Language-Specific Tips

### Python

```python
# Use type hints throughout
# Follow PEP 8 style guidelines
# Include docstrings with Args, Returns, Raises sections
# Function to calculate statistics from list of numbers
```

### JavaScript/TypeScript

```typescript
// Use async/await instead of .then()
// Add proper TypeScript types
// Include JSDoc comments
// Function to debounce search input
```

### Java

```java
// Follow Java naming conventions
// Include JavaDoc comments
// Use appropriate access modifiers
// Implement Builder pattern for User class
```

### C#

```csharp
// Use async/await pattern
// Follow C# coding conventions
// Include XML documentation comments
// Implement repository pattern for data access
```

## 🔄 Iterative Refinement

### Start Broad, Then Refine

**First Attempt:**
```javascript
// Function to validate password
```

**Add Requirements:**
```javascript
// Function to validate password with these rules:
// - At least 8 characters
// - Contains uppercase and lowercase
// - Contains at least one number
```

**Add More Detail:**
```javascript
// Function to validate password with these rules:
// - At least 8 characters long
// - Contains uppercase and lowercase letters
// - Contains at least one number
// - Contains at least one special character (!@#$%^&*)
// Return object with isValid (boolean) and errors (string[])
```

## 💡 Advanced Techniques

### 1. Chain of Thought Prompting

```python
# Calculate shipping cost based on weight and distance
# Step 1: Determine base rate from weight brackets
# Step 2: Apply distance multiplier
# Step 3: Add fuel surcharge
# Step 4: Apply any promotional discounts
# Return breakdown of costs and total
```

### 2. Role-Based Prompting

```java
// As a security-conscious developer, implement authentication
// that includes rate limiting, password hashing with salt,
// session management, and CSRF protection
```

### 3. Template Prompting

```typescript
// Create React component following this template:
// - Functional component with TypeScript
// - Use hooks for state management
// - Include prop types
// - Add loading and error states
// - Component: UserProfile displaying user information
```

## 🚫 Common Anti-Patterns

### 1. Too Vague

```javascript
// ❌ Bad: do something with data
// ✅ Good: Transform array of user objects to CSV format
```

### 2. Missing Context

```python
# ❌ Bad: add validation
# ✅ Good: Add email format validation to the User class above
```

### 3. Ambiguous Requirements

```java
// ❌ Bad: make it faster
// ✅ Good: Optimize database query using indexing and caching
```

### 4. Overcomplicated

```typescript
// ❌ Bad: Create a polymorphic, dependency-injected, factory pattern...
// ✅ Good: Create a simple factory to instantiate User objects
```

## 📊 Prompt Quality Checklist

Before submitting a prompt, ask:

- [ ] Is my intent clear?
- [ ] Have I provided enough context?
- [ ] Have I specified input/output formats?
- [ ] Have I mentioned constraints?
- [ ] Have I included examples if helpful?
- [ ] Is my prompt concise?
- [ ] Have I specified the programming language/framework?
- [ ] Have I referenced relevant existing code?

## 🎪 Chat-Specific Prompting

### Effective Chat Questions

**Code Explanation:**
```
"Explain this function line by line, focusing on the algorithm used"
```

**Optimization:**
```
"How can I optimize this loop for better performance with large datasets?"
```

**Debugging:**
```
"Why might this function return undefined in some cases?"
```

**Refactoring:**
```
"Refactor this code to use the repository pattern"
```

### Chat Best Practices

1. **Be specific about scope**: "Only modify the error handling"
2. **Request explanations**: "Explain why this change improves performance"
3. **Ask for alternatives**: "Show me 3 different ways to implement this"
4. **Iterative refinement**: "Now add input validation to that function"

## 🔍 Debugging with Prompts

### Error Analysis

```python
# Debug this function - it's throwing IndexError
# Input: list of integers
# Expected: return second largest number
# Current behavior: crashes on lists with < 2 elements
def find_second_largest(numbers):
    # buggy code here
```

### Performance Issues

```javascript
// This function is slow with large arrays (>10000 items)
// Profile and optimize for better performance
// Consider using more efficient data structures
function findDuplicates(array) {
    // slow implementation
}
```

## 📚 Documentation Generation

### Function Documentation

```typescript
// Generate comprehensive JSDoc for this function
// Include description, parameters, returns, and examples
function calculateCompoundInterest(principal, rate, time, frequency) {
    // implementation
}
```

### README Sections

```markdown
<!-- Generate a README section for installation instructions -->
<!-- Include prerequisites, step-by-step guide, and troubleshooting -->
```

## 🎓 Practice Exercises

Try these prompts and compare results:

1. **Basic Function**
   ```python
   # Function to check if string is palindrome
   ```

2. **With Examples**
   ```python
   # Function to check if string is palindrome
   # Examples: "radar" -> True, "hello" -> False
   ```

3. **With Constraints**
   ```python
   # Function to check if string is palindrome
   # Ignore case, spaces, and punctuation
   # "A man, a plan, a canal: Panama" -> True
   ```

## 🔗 Next Steps

- Practice with [exercises.md](exercises.md)
- Read the comprehensive [Prompt Engineering Guide](../guides/prompt-engineering-guide.md)
- Explore [Prompt Templates](../templates/prompt-templates/)
- Learn about [Copilot Advanced Features](copilot-features.md)

## 📖 Additional Resources

- [Official Prompt Engineering Guide](https://docs.github.com/en/copilot/using-github-copilot/prompt-engineering-for-github-copilot)
- [Best Practices Documentation](https://docs.github.com/en/copilot/using-github-copilot/best-practices-for-using-github-copilot)

---

*Master these patterns to unlock the full potential of GitHub Copilot!*
