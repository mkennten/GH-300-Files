# Prompt Engineering for GitHub Copilot - Comprehensive Guide

Master the art of crafting effective prompts to maximize GitHub Copilot's capabilities and generate high-quality code.

## 📋 Table of Contents

1. [Introduction to Prompt Engineering](#introduction-to-prompt-engineering)
2. [Fundamental Principles](#fundamental-principles)
3. [Anatomy of an Effective Prompt](#anatomy-of-an-effective-prompt)
4. [Prompt Patterns and Templates](#prompt-patterns-and-templates)
5. [Context Management](#context-management)
6. [Language-Specific Strategies](#language-specific-strategies)
7. [Advanced Techniques](#advanced-techniques)
8. [Common Pitfalls and Solutions](#common-pitfalls-and-solutions)
9. [Real-World Examples](#real-world-examples)
10. [Best Practices](#best-practices)

## Introduction to Prompt Engineering

### What is Prompt Engineering?

Prompt engineering is the practice of crafting effective instructions (prompts) to guide AI models like GitHub Copilot to generate desired code outputs. It's the bridge between what you need and what the AI produces.

### Why It Matters

**Poor Prompt:**
```python
# function for user
```

**Good Prompt:**
```python
# Function to validate user credentials
# Parameters: username (str), password (str)
# Returns: True if valid, False otherwise
# Checks against database and verifies password hash
```

**Result:** The good prompt generates a complete, secure implementation versus a vague, incomplete suggestion.

### The Prompt Engineering Mindset

Think of Copilot as a highly skilled but literal-minded assistant:
- **Be explicit**: State exactly what you want
- **Provide context**: Share relevant information
- **Show examples**: Demonstrate expected patterns
- **Iterate**: Refine based on results

## Fundamental Principles

### 1. Clarity Over Brevity

**❌ Too Brief:**
```javascript
// get data
```

**✅ Clear:**
```javascript
// Fetch user data from REST API
// GET request to /api/users/{id}
// Returns Promise<User> with id, name, email properties
```

### 2. Specificity Drives Quality

**❌ Vague:**
```python
# process the list
```

**✅ Specific:**
```python
# Filter list to remove null values
# Sort remaining items by timestamp descending
# Return first 10 results
```

### 3. Context is King

**❌ No Context:**
```typescript
// validate input
```

**✅ With Context:**
```typescript
interface LoginForm {
  email: string;
  password: string;
}

// Validate login form input
// Check email format and password length (min 8 chars)
// Return validation errors object
```

### 4. Examples Enhance Understanding

**❌ Without Examples:**
```java
// format currency
```

**✅ With Examples:**
```java
// Format number as currency
// Examples: 1234.56 -> "$1,234.56"
//          100 -> "$100.00"
//          -50.5 -> "-$50.50"
```

## Anatomy of an Effective Prompt

### Basic Structure

```
[Action] [What] [How] [Constraints]
```

**Example:**
```python
# [Action: Create] [What: function to parse CSV] 
# [How: using pandas library]
# [Constraints: handle missing values, return DataFrame]
```

### Detailed Structure

```
[Type] [Name/Purpose]
[Input Specification]
[Output Specification]
[Behavior Description]
[Constraints/Requirements]
[Examples (if helpful)]
```

**Example:**
```typescript
// Function: calculateShippingCost
// Input: weight (number in kg), distance (number in km), expressShipping (boolean)
// Output: cost (number in USD)
// Behavior: Base rate $5 + $0.50/kg + $0.10/km, double if express
// Constraints: weight and distance must be positive, round to 2 decimal places
// Example: calculateShippingCost(5, 100, false) should return 17.50
```

### Component Breakdown

#### 1. Action Verbs

Choose precise verbs:
- **Create/Generate**: Build something new
- **Transform/Convert**: Change format
- **Validate/Check**: Verify conditions
- **Parse/Extract**: Process data
- **Calculate/Compute**: Perform calculations
- **Fetch/Retrieve**: Get data
- **Filter/Sort**: Organize data

#### 2. Data Types

Specify types explicitly:
```typescript
// ✓ Good: userId: string
// ✓ Good: count: integer
// ✓ Good: prices: array of floats
// ✗ Bad: some value
// ✗ Bad: the data
```

#### 3. Constraints

Include limitations:
- Input ranges: "between 0 and 100"
- Performance: "efficient for arrays up to 10,000 items"
- Error handling: "throw Error if invalid"
- Format: "return ISO 8601 date string"

## Prompt Patterns and Templates

### Pattern 1: Function Generation

**Template:**
```
# Function to [ACTION] [WHAT]
# Parameters: [NAME] ([TYPE], [DESCRIPTION])
# Returns: [TYPE] - [DESCRIPTION]
# [Additional requirements or constraints]
```

**Example:**
```javascript
// Function to calculate compound interest
// Parameters: principal (number, initial amount),
//            rate (number, annual interest rate as decimal),
//            time (number, years),
//            frequency (number, compounds per year)
// Returns: number - final amount rounded to 2 decimals
// Use formula: A = P(1 + r/n)^(nt)
```

### Pattern 2: Class Design

**Template:**
```
# [ClassName] class for [PURPOSE]
# Properties:
#   - [property]: [type] - [description]
# Methods:
#   - [method]([params]): [return] - [description]
# [Additional specifications]
```

**Example:**
```python
# ShoppingCart class for e-commerce application
# Properties:
#   - items: list of CartItem - products in cart
#   - total: float - current cart total
#   - discount_code: str - applied discount code
# Methods:
#   - add_item(product, quantity): void - add product to cart
#   - remove_item(product_id): void - remove product
#   - apply_discount(code): bool - apply discount code
#   - calculate_total(): float - compute total with discounts
# Include input validation and error handling
```

### Pattern 3: Algorithm Implementation

**Template:**
```
# Implement [ALGORITHM NAME] for [PURPOSE]
# Input: [SPECIFICATION]
# Output: [SPECIFICATION]
# Algorithm: [APPROACH/STEPS]
# Time Complexity: [BIG O]
# Space Complexity: [BIG O]
```

**Example:**
```java
// Implement binary search algorithm for sorted integer array
// Input: sorted int[] array and int target value
// Output: index of target or -1 if not found
// Algorithm: Divide and conquer approach
// Time Complexity: O(log n)
// Space Complexity: O(1)
// Handle edge cases: empty array, null input
```

### Pattern 4: API Integration

**Template:**
```
# [HTTP METHOD] request to [ENDPOINT]
# Purpose: [WHAT IT DOES]
# Request: [HEADERS, BODY, PARAMS]
# Response: [EXPECTED FORMAT]
# Error Handling: [HOW TO HANDLE ERRORS]
```

**Example:**
```typescript
// POST request to /api/v1/users endpoint
// Purpose: Create new user account
// Request: 
//   Headers: Content-Type: application/json, Authorization: Bearer token
//   Body: { email, password, name }
// Response: 
//   Success (201): { id, email, name, createdAt }
//   Error (400): { error, message, validationErrors }
// Error Handling: Retry on network errors, validate input before sending
```

### Pattern 5: Test-Driven Development

**Template:**
```
# Test cases for [FUNCTION/CLASS]
# Test 1: [SCENARIO] - Expected: [RESULT]
# Test 2: [SCENARIO] - Expected: [RESULT]
# Test 3: [EDGE CASE] - Expected: [RESULT]
# Now implement the function to pass these tests
```

**Example:**
```python
# Test cases for email_validator function
# Test 1: valid email "user@example.com" - Expected: True
# Test 2: missing @ "userexample.com" - Expected: False
# Test 3: missing domain "user@" - Expected: False
# Test 4: multiple @ "user@@example.com" - Expected: False
# Test 5: empty string "" - Expected: False
# Now implement the email_validator function
```

### Pattern 6: Code Transformation

**Template:**
```
# Transform this [OLD APPROACH] to [NEW APPROACH]
# Requirements: [WHAT TO MAINTAIN]
# Changes: [WHAT TO MODIFY]
# [SHOW OLD CODE OR REFERENCE IT]
```

**Example:**
```javascript
// Transform this callback-based function to async/await
// Requirements: Maintain error handling and return values
// Changes: Use modern async/await syntax, remove callback parameter

// Old approach:
function fetchData(url, callback) {
  request(url, (error, response) => {
    if (error) return callback(error);
    callback(null, response);
  });
}

// Transform to async/await:
```

## Context Management

### What is Context?

Context is all the information Copilot considers when generating suggestions:
- Current file content
- Open files in editor
- Cursor position
- File type and language
- Comments and code structure

### Optimizing Context

#### 1. File Organization

**✅ Good Structure:**
```typescript
// Top: Imports and types
import { User } from './types';

// Middle: Interfaces and types for this file
interface ValidationResult {
  isValid: boolean;
  errors: string[];
}

// Bottom: Functions using above types
// Function to validate user data
// Uses User interface and returns ValidationResult
```

#### 2. Related Files

Keep related files open:
```
Open files:
- user.types.ts (interface definitions)
- user.service.ts (service implementation)
- user.validator.ts (currently editing)

// Copilot can now reference User interface from user.types.ts
```

#### 3. Code Proximity

Place related code nearby:
```python
class User:
    def __init__(self, name, email):
        self.name = name
        self.email = email

# This function will understand User class structure
# Function to create user from JSON data
# Parse JSON and return User instance
```

#### 4. Progressive Disclosure

Build context incrementally:
```javascript
// Step 1: Define data structure
const API_CONFIG = {
  baseURL: 'https://api.example.com',
  timeout: 5000
};

// Step 2: Reference in prompt
// Create API client using API_CONFIG above
// Include error handling and retry logic
```

### Context Poisoning

Avoid confusing Copilot:

**❌ Bad:**
```python
# Random unrelated code
user_data = None
car_info = {}
weather = []

# Now create database connection
# (Copilot is confused by unrelated variables)
```

**✅ Good:**
```python
# Database configuration
DB_HOST = 'localhost'
DB_PORT = 5432
DB_NAME = 'myapp'

# Create database connection using config above
```

## Language-Specific Strategies

### Python

**Best Practices:**
```python
# Always include type hints in Python 3.6+
# Follow PEP 8 style guidelines
# Use docstrings in Google or NumPy format
# Prefer list comprehensions where readable

# Function to filter and transform user list
# Parameters: users: List[Dict[str, Any]]
# Returns: List[str] - list of email addresses
# Filter active users only, extract emails, lowercase all
```

**Framework-Specific (Django):**
```python
# Django model for blog post
# Fields: title (max 200 chars), content (text), 
#         author (ForeignKey to User), created_at, updated_at
# Include Meta class with ordering and indexes
# Add __str__ method returning title
```

### JavaScript/TypeScript

**Best Practices:**
```typescript
// Use TypeScript for better suggestions
// Prefer async/await over .then()
// Include JSDoc or TypeScript types
// Follow Airbnb or Standard style guide

// Interface for API response
interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

// Fetch function using interface above
// Generic function to GET data from API
// Type-safe with proper error handling
```

**React-Specific:**
```typescript
// React functional component with TypeScript
// Props: user (User type), onUpdate (callback)
// Display user info with edit button
// Use hooks for state management
// Include loading and error states
```

### Java

**Best Practices:**
```java
// Follow Java naming conventions
// Use appropriate access modifiers
// Include JavaDoc comments
// Implement common interfaces (Comparable, Serializable)

/**
 * Service class for user management
 * Uses UserRepository for database operations
 * Implements business logic for user CRUD
 * Include transaction management with @Transactional
 */
@Service
public class UserService {
```

**Spring Boot Specific:**
```java
// Spring Boot REST controller for Product
// Endpoints: GET /api/products, POST /api/products
// Use @Valid for request validation
// Return ResponseEntity with appropriate status codes
// Include exception handling with @ExceptionHandler
```

### C#

**Best Practices:**
```csharp
// Follow C# naming conventions (PascalCase for public)
// Use async/await pattern
// Include XML documentation comments
// Implement IDisposable where needed

/// <summary>
/// Repository for Product entity
/// Implements generic repository pattern
/// Uses Entity Framework Core for data access
/// Include async methods for CRUD operations
/// </summary>
```

## Advanced Techniques

### 1. Chain of Thought Prompting

Break complex problems into steps:

```python
# Function to analyze customer purchase patterns
# Step 1: Group purchases by customer ID
# Step 2: Calculate total spent per customer
# Step 3: Identify customers spending > $1000
# Step 4: Find common products among top spenders
# Step 5: Return analysis object with insights
# Use pandas for data manipulation
```

### 2. Few-Shot Learning

Provide examples to establish patterns:

```javascript
// Format various data types consistently
// Example patterns:
// Date: "2024-01-15" -> "January 15, 2024"
// Phone: "1234567890" -> "(123) 456-7890"
// Currency: "1234.56" -> "$1,234.56"
// Now create formatData(type, value) function
```

### 3. Constraint-Based Generation

Specify what to avoid or include:

```typescript
// Create form validation function with constraints:
// MUST: Use Zod library for schema validation
// MUST: Return type-safe error objects
// MUST NOT: Use regex for email validation (use Zod)
// MUST NOT: Throw exceptions (return errors instead)
// SHOULD: Support custom error messages
```

### 4. Iterative Refinement

Start broad, then add details:

**Iteration 1:**
```python
# Function to process payment
```

**Iteration 2:**
```python
# Function to process credit card payment
# Parameters: card_number, amount, currency
# Returns: transaction_id or error
```

**Iteration 3:**
```python
# Function to process credit card payment
# Parameters: 
#   card_number: str (16 digits)
#   amount: Decimal (positive, 2 decimal places)
#   currency: str (ISO 4217 code)
# Returns: dict with transaction_id, status, timestamp
# Validate card using Luhn algorithm
# Use Stripe API for processing
# Include comprehensive error handling
```

### 5. Role-Based Prompting

Frame requests from a perspective:

```java
// As a security-conscious developer, implement JWT authentication
// Requirements:
// - Use RS256 algorithm (not HS256)
// - Include token expiration (15 min access, 7 day refresh)
// - Validate issuer and audience claims
// - Implement token refresh mechanism
// - Add rate limiting to prevent brute force
// - Log all authentication attempts
```

### 6. Template Programming

Show the pattern to follow:

```typescript
// Existing pattern for GET endpoint:
router.get('/users', async (req, res) => {
  try {
    const users = await userService.getAll();
    res.json({ data: users, status: 'success' });
  } catch (error) {
    logger.error('Failed to fetch users:', error);
    res.status(500).json({ error: 'Internal server error' });
  }
});

// Create similar POST endpoint for creating users
// Follow exact same pattern and error handling
```

## Common Pitfalls and Solutions

### Pitfall 1: Ambiguous Requirements

**Problem:**
```javascript
// create user thing
```

**Solution:**
```javascript
// Create User class with properties: id, username, email, createdAt
// Methods: validate() to check email format, toJSON() for serialization
// Constructor should accept object with user properties
```

### Pitfall 2: Missing Error Handling

**Problem:**
```python
# fetch data from API
```

**Solution:**
```python
# Fetch data from API with comprehensive error handling
# Handle: network errors (retry 3 times), 404 (return None),
#         500 (log and raise), timeout (5 seconds)
# Use requests library with session for connection pooling
```

### Pitfall 3: Ignoring Edge Cases

**Problem:**
```java
// sort array
```

**Solution:**
```java
// Sort integer array in ascending order
// Handle edge cases: null array (throw IllegalArgumentException),
//                    empty array (return empty),
//                    single element (return as-is)
// Use Arrays.sort() for efficiency
```

### Pitfall 4: Insufficient Context

**Problem:**
```typescript
// add validation
```

**Solution:**
```typescript
interface UserForm {
  email: string;
  password: string;
  age: number;
}

// Add validation function for UserForm above
// Rules: email must be valid format,
//       password min 8 chars with upper/lower/number,
//       age between 18 and 120
// Return object with field-specific errors
```

### Pitfall 5: Overcomplicating

**Problem:**
```python
# Create polymorphic factory with dependency injection
# using abstract factory pattern and strategy pattern
# with observer pattern for state changes...
```

**Solution:**
```python
# Create factory class to instantiate different User types
# Types: AdminUser, RegularUser, GuestUser
# Factory method: create_user(user_type, **kwargs)
# Return appropriate user instance
```

## Real-World Examples

### Example 1: REST API Endpoint

**Scenario:** Creating a complete API endpoint for user registration.

```typescript
// Express POST endpoint: /api/register
// Request body: { email, password, firstName, lastName }
// 
// Process:
// 1. Validate input (email format, password strength)
// 2. Check if email already exists in database
// 3. Hash password with bcrypt (10 rounds)
// 4. Create user record in database
// 5. Generate JWT token
// 6. Send welcome email (async, don't wait)
// 7. Return: { user: {id, email, name}, token }
//
// Error responses:
// - 400: Invalid input (with field errors)
// - 409: Email already exists
// - 500: Server error
//
// Include TypeScript types and proper error handling
```

### Example 2: Data Processing Pipeline

**Scenario:** ETL pipeline for processing CSV data.

```python
# Data processing pipeline for sales data
# 
# Input: CSV file with columns: date, product, quantity, price, region
# 
# Steps:
# 1. Read CSV using pandas
# 2. Clean data:
#    - Remove rows with missing required fields
#    - Convert date to datetime
#    - Validate quantity and price are positive
# 3. Transform:
#    - Calculate total_sale (quantity * price)
#    - Add month and year columns from date
#    - Normalize region names (uppercase, trim)
# 4. Aggregate:
#    - Group by product and month
#    - Calculate: total_quantity, total_revenue, avg_price
# 5. Output: Save to SQLite database and JSON file
#
# Include progress logging and error handling
# Return summary statistics
```

### Example 3: React Component

**Scenario:** Building a data table component with features.

```typescript
// React component: DataTable<T>
// Generic component to display tabular data
//
// Props:
// - data: T[] - array of objects to display
// - columns: ColumnDef<T>[] - column definitions
// - onRowClick?: (row: T) => void - optional row click handler
// - loading?: boolean - show loading state
// - error?: string - show error message
//
// Features:
// - Sortable columns (click header to sort)
// - Pagination (10 rows per page)
// - Search/filter (text input filters all columns)
// - Loading skeleton
// - Empty state message
// - Responsive design
//
// Use TypeScript generics for type safety
// Style with Tailwind CSS
// Include keyboard navigation
```

## Best Practices

### Do's ✅

1. **Be Specific**
   - State exact requirements
   - Include data types
   - Specify error handling

2. **Provide Context**
   - Show related code
   - Define interfaces first
   - Reference existing patterns

3. **Use Examples**
   - Input/output samples
   - Edge case scenarios
   - Expected behavior

4. **Iterate**
   - Start simple
   - Refine gradually
   - Build on results

5. **Validate**
   - Test generated code
   - Review for security
   - Check performance

### Don'ts ❌

1. **Don't Be Vague**
   - Avoid: "do something"
   - Instead: "calculate X using Y"

2. **Don't Skip Types**
   - Avoid: "some data"
   - Instead: "user_ids: List[int]"

3. **Don't Ignore Errors**
   - Avoid: "get data from API"
   - Instead: "fetch data with timeout and retry"

4. **Don't Overcomplicate**
   - Avoid: Multiple patterns in one
   - Instead: One clear purpose

5. **Don't Trust Blindly**
   - Avoid: Copy-paste without review
   - Instead: Understand and validate

### Quality Checklist

Before submitting a prompt:

- [ ] Clear action verb?
- [ ] Data types specified?
- [ ] Input/output defined?
- [ ] Error handling mentioned?
- [ ] Constraints listed?
- [ ] Context provided?
- [ ] Examples if helpful?
- [ ] Concise yet complete?

## Measuring Success

### Good Indicators

- **First attempt accuracy**: Gets close on first try
- **Minimal edits needed**: Few manual changes required
- **Handles edge cases**: Considers error scenarios
- **Follows patterns**: Matches existing code style
- **Complete solutions**: Not just partial code

### When to Refine

- Output is incomplete
- Doesn't handle errors
- Inefficient implementation
- Doesn't match requirements
- Security concerns

### Iteration Example

**Try 1:**
```python
# sort list
```
Result: Basic sort

**Try 2:**
```python
# sort list of dictionaries by age field
```
Result: Better, but no error handling

**Try 3:**
```python
# Sort list of user dictionaries by age field (ascending)
# Handle missing age field (push to end)
# Handle non-numeric age values (skip them)
# Return new sorted list, don't modify original
```
Result: Production-ready solution!

## Next Steps

### Practice

1. Complete [Exercises](../cheatsheets/exercises.md)
2. Try different prompt styles
3. Compare results
4. Learn from outputs

### Learn More

- [Prompt Engineering Cheat Sheet](../cheatsheets/prompt-engineering.md)
- [Copilot Features](../cheatsheets/copilot-features.md)
- [Responsible AI Guide](responsible-ai.md)

### Share

- Document successful patterns
- Share with your team
- Contribute to community
- Teach others

---

**Master prompt engineering to unlock GitHub Copilot's full potential!**

*The better your prompts, the better your code. Practice makes perfect.*
