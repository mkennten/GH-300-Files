# GitHub Copilot Practice Exercises

Hands-on exercises to improve your GitHub Copilot skills. Work through these progressively to master AI-assisted development.

## 🎯 Getting Started

### Prerequisites
- GitHub Copilot installed and activated
- Preferred IDE (VS Code, Visual Studio, or JetBrains)
- Basic programming knowledge in at least one language

### How to Use These Exercises
1. Read the exercise description
2. Write the prompt as instructed
3. Review Copilot's suggestion
4. Test the generated code
5. Refine if needed
6. Compare with the solution approach

## 🌟 Level 1: Basic Code Generation

### Exercise 1.1: Simple Function

**Task:** Generate a function to check if a number is prime.

**Your Prompt:**
```python
# Function to check if a number is prime
# Parameter: n (integer)
# Returns: True if prime, False otherwise
```

**Expected Outcome:**
- Function implementation with edge cases
- Handles negative numbers and 0, 1
- Efficient algorithm (at least √n complexity)

**Validation:**
```python
assert is_prime(7) == True
assert is_prime(4) == False
assert is_prime(1) == False
assert is_prime(0) == False
```

---

### Exercise 1.2: Data Validation

**Task:** Create an email validation function.

**Your Prompt:**
```javascript
// Function to validate email address format
// Must include @ symbol and domain
// Return true for valid emails, false otherwise
```

**Try Different Approaches:**
1. Basic validation
2. With regex pattern
3. With detailed error messages

---

### Exercise 1.3: Array Manipulation

**Task:** Generate a function to remove duplicates from an array.

**Your Prompt:**
```typescript
// Function to remove duplicate elements from array
// Preserve original order
// Works with numbers, strings, and objects
// TypeScript with generic type
```

**Test Cases:**
```typescript
removeDuplicates([1, 2, 2, 3]) // [1, 2, 3]
removeDuplicates(['a', 'b', 'a']) // ['a', 'b']
```

---

## 🚀 Level 2: Working with APIs

### Exercise 2.1: API Client

**Task:** Create an API client class for a REST service.

**Your Prompt:**
```javascript
// API Client class for JSONPlaceholder
// Base URL: https://jsonplaceholder.typicode.com
// Methods: get, post, put, delete
// Include error handling and async/await
// Add request timeout of 5 seconds
```

**Features to Include:**
- Error handling
- Timeout configuration
- Response parsing
- HTTP methods

---

### Exercise 2.2: Async Data Fetching

**Task:** Fetch and process data from multiple endpoints.

**Your Prompt:**
```python
# Async function to fetch user data and their posts
# Fetch from: /users/{id} and /users/{id}/posts
# Combine into single object
# Handle network errors gracefully
# Use aiohttp library
```

---

### Exercise 2.3: Rate Limiting

**Task:** Implement a rate-limited API wrapper.

**Your Prompt:**
```typescript
// Rate limiter class that restricts API calls
// Maximum 10 requests per minute
// Queue excess requests
// TypeScript with proper types
```

---

## 💡 Level 3: Test-Driven Development

### Exercise 3.1: Function from Tests

**Task:** Create tests first, then generate implementation.

**Step 1 - Write Tests:**
```javascript
describe('calculateDiscount', () => {
  test('applies 10% discount for orders over $100', () => {
    expect(calculateDiscount(100, 150)).toBe(135);
  });
  
  test('no discount for orders under $100', () => {
    expect(calculateDiscount(100, 50)).toBe(50);
  });
  
  test('handles zero and negative amounts', () => {
    expect(calculateDiscount(100, 0)).toBe(0);
    expect(() => calculateDiscount(100, -50)).toThrow();
  });
});
```

**Step 2 - Your Prompt:**
```javascript
// Implement calculateDiscount function
// Based on the test cases above
```

---

### Exercise 3.2: Test Generation

**Task:** Generate comprehensive tests for existing code.

**Given Code:**
```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

**Your Prompt:**
```python
# Generate pytest tests for fibonacci function
# Include: normal cases, edge cases, performance tests
# Use parametrize for multiple test cases
```

---

## 🎨 Level 4: Refactoring

### Exercise 4.1: Code Improvement

**Task:** Refactor legacy code using Copilot Chat.

**Given Code:**
```javascript
function getUserData(id) {
  var result;
  var xhr = new XMLHttpRequest();
  xhr.open('GET', '/api/users/' + id, false);
  xhr.send();
  if (xhr.status === 200) {
    result = JSON.parse(xhr.responseText);
  } else {
    result = null;
  }
  return result;
}
```

**Your Chat Prompt:**
```
"Refactor this to use async/await with fetch API.
Add error handling and TypeScript types."
```

---

### Exercise 4.2: Pattern Application

**Task:** Apply design patterns to existing code.

**Your Chat Prompt:**
```
"Refactor this code to use the Strategy pattern
for different payment methods: credit card, PayPal, crypto"
```

**Starter Code:**
```javascript
function processPayment(method, amount) {
  if (method === 'creditcard') {
    // credit card logic
  } else if (method === 'paypal') {
    // paypal logic
  } else if (method === 'crypto') {
    // crypto logic
  }
}
```

---

### Exercise 4.3: Extract Functions

**Task:** Use inline chat to extract helper functions.

**Given Code:**
```python
def process_order(order):
    # validate order
    if not order.get('id') or not order.get('customer'):
        raise ValueError('Invalid order')
    
    # calculate total
    total = sum(item['price'] * item['quantity'] 
                for item in order['items'])
    
    # apply discount
    if total > 100:
        total *= 0.9
    
    # save to database
    db.orders.insert_one({
        'order_id': order['id'],
        'total': total,
        'status': 'processed'
    })
```

**Your Inline Chat:**
```
"Extract validation, calculation, and database logic
into separate functions"
```

---

## 🛠️ Level 5: Real-World Scenarios

### Exercise 5.1: Authentication System

**Task:** Build a complete authentication module.

**Your Prompt:**
```javascript
// User authentication module with:
// - Registration with email validation
// - Password hashing (bcrypt)
// - JWT token generation
// - Login with rate limiting
// - Password reset functionality
// Include TypeScript types and error handling
```

---

### Exercise 5.2: Data Processing Pipeline

**Task:** Create a data transformation pipeline.

**Your Prompt:**
```python
# Data processing pipeline class:
# 1. Read CSV file
# 2. Clean data (remove nulls, trim whitespace)
# 3. Transform columns (normalize, convert types)
# 4. Validate against schema
# 5. Export to JSON and SQLite
# Use pandas and include error handling
```

---

### Exercise 5.3: Microservice Endpoint

**Task:** Generate a complete REST endpoint.

**Your Prompt:**
```java
// Spring Boot REST controller for Product management
// Endpoints: GET, POST, PUT, DELETE
// Include:
// - Request validation
// - Exception handling
// - Logging
// - OpenAPI documentation annotations
// - Unit tests
```

---

## 🎯 Level 6: Prompt Engineering Mastery

### Exercise 6.1: Progressive Enhancement

**Task:** Start with basic prompt, then enhance iteratively.

**Iteration 1:**
```javascript
// Sort array of numbers
```

**Iteration 2:**
```javascript
// Sort array of numbers in ascending order
// Handle null and undefined values
```

**Iteration 3:**
```javascript
// Sort array of numbers in ascending order
// Handle null and undefined values (push to end)
// Support custom comparator function
// Use stable sort algorithm
// TypeScript with generics
```

**Goal:** Observe how additional context improves results.

---

### Exercise 6.2: Context Provision

**Task:** Provide context for better suggestions.

**Without Context:**
```python
# Create User class
```

**With Context:**
```python
# Database models for e-commerce application
from sqlalchemy import Column, Integer, String, DateTime
from sqlalchemy.orm import relationship

class Order(Base):
    __tablename__ = 'orders'
    id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey('users.id'))
    created_at = Column(DateTime)

# Create User class following the same pattern
# Include: id, email, username, created_at, orders relationship
```

---

### Exercise 6.3: Example-Driven Generation

**Task:** Use examples to guide generation.

**Your Prompt:**
```javascript
// Format dates in human-readable format
// Examples:
// - "2024-01-01" -> "January 1, 2024"
// - "2024-12-25" -> "December 25, 2024"
// - Handle invalid dates gracefully
```

---

## 🧪 Level 7: Testing and Debugging

### Exercise 7.1: Bug Detection

**Task:** Use Copilot to find bugs.

**Buggy Code:**
```python
def calculate_average(numbers):
    total = 0
    for num in numbers:
        total += num
    return total / len(numbers)
```

**Your Chat:**
```
"What bugs exist in this function?
What inputs could cause it to fail?"
```

---

### Exercise 7.2: Performance Optimization

**Task:** Optimize slow code.

**Slow Code:**
```javascript
function findDuplicates(arr) {
  const duplicates = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] === arr[j] && !duplicates.includes(arr[i])) {
        duplicates.push(arr[i]);
      }
    }
  }
  return duplicates;
}
```

**Your Chat:**
```
"Optimize this function for arrays with 10,000+ elements.
Reduce time complexity."
```

---

### Exercise 7.3: Test Coverage

**Task:** Achieve high test coverage.

**Your Prompt:**
```typescript
// Generate comprehensive test suite for this class
// Target 90%+ code coverage
// Include: unit tests, integration tests, edge cases

class ShoppingCart {
  // existing implementation
}
```

---

## 🏆 Level 8: Advanced Challenges

### Exercise 8.1: Multi-File Project

**Task:** Generate a complete feature across multiple files.

**Your Prompts:**

```typescript
// File: types.ts
// Define TypeScript interfaces for blog post system
// Include: Post, Author, Comment, Category
```

```typescript
// File: validators.ts
// Create validation functions for the types above
// Use Zod or Joi for schema validation
```

```typescript
// File: service.ts
// Implement PostService class
// CRUD operations using the types and validators
```

```typescript
// File: api.ts
// Create Express routes
// Use the PostService
// Include error handling middleware
```

---

### Exercise 8.2: Documentation Generation

**Task:** Generate comprehensive documentation.

**Your Prompt:**
```python
# Generate complete API documentation for this Flask app
# Include: endpoints, request/response examples, error codes
# Format as OpenAPI 3.0 specification

@app.route('/api/users', methods=['GET', 'POST'])
def users():
    # implementation
    pass
```

---

### Exercise 8.3: Migration Project

**Task:** Migrate code between frameworks.

**Your Chat:**
```
"Convert this React class component to a Vue 3
Composition API component. Maintain all functionality
including lifecycle methods and state management."
```

---

## 📊 Self-Assessment

After completing exercises, evaluate your skills:

### Beginner (Levels 1-2)
- [ ] Can generate basic functions
- [ ] Understands how to write clear prompts
- [ ] Can validate generated code
- [ ] Comfortable with one programming language

### Intermediate (Levels 3-5)
- [ ] Uses TDD approach with Copilot
- [ ] Can refactor code effectively
- [ ] Generates production-ready code
- [ ] Works across multiple languages

### Advanced (Levels 6-7)
- [ ] Masters prompt engineering techniques
- [ ] Optimizes code performance
- [ ] Achieves high test coverage
- [ ] Debugs efficiently with Copilot

### Expert (Level 8)
- [ ] Generates multi-file projects
- [ ] Creates comprehensive documentation
- [ ] Migrates between frameworks
- [ ] Teaches others Copilot best practices

## 💡 Tips for Success

1. **Start Simple**: Don't jump to advanced exercises
2. **Compare Results**: Try different prompt variations
3. **Learn from Output**: Study the generated code
4. **Iterate**: Refine prompts based on results
5. **Test Everything**: Always validate generated code
6. **Read Documentation**: Understand what Copilot suggests
7. **Practice Daily**: Build muscle memory
8. **Share Knowledge**: Help others learn

## 🔄 Next Steps

1. **Complete All Exercises**: Work through progressively
2. **Create Your Own**: Design exercises for your domain
3. **Apply to Projects**: Use Copilot in real work
4. **Join Community**: Share experiences and tips
5. **Stay Updated**: Learn about new features

## 📚 Additional Resources

- [Copilot Basics](copilot-basics.md)
- [Prompt Engineering](prompt-engineering.md)
- [Copilot Features](copilot-features.md)
- [Getting Started Guide](../guides/getting-started.md)
- [Prompt Engineering Guide](../guides/prompt-engineering-guide.md)

---

*Practice makes perfect! Work through these exercises to become a Copilot expert.*
