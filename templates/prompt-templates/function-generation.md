# Function Generation Prompt Templates

Templates for generating functions with GitHub Copilot.

## Basic Function Template

```
# Function to [ACTION] [WHAT]
# Parameters: [PARAMETER_NAME] ([TYPE], [DESCRIPTION])
# Returns: [RETURN_TYPE] - [DESCRIPTION]
# [Additional requirements]
```

### Example

```python
# Function to validate email address format
# Parameters: email (string, email address to validate)
# Returns: boolean - True if valid, False otherwise
# Use regex pattern to check format
```

## Detailed Function Template

```
# Function: [FUNCTION_NAME]
# Purpose: [DETAILED_PURPOSE]
# 
# Parameters:
#   - [param1]: [type] - [description]
#   - [param2]: [type] - [description]
# 
# Returns: [type] - [description]
# 
# Behavior:
#   - [behavior_point_1]
#   - [behavior_point_2]
# 
# Constraints:
#   - [constraint_1]
#   - [constraint_2]
# 
# Examples:
#   - [example_input] -> [example_output]
```

### Example

```javascript
// Function: calculateShippingCost
// Purpose: Calculate total shipping cost based on weight, distance, and options
// 
// Parameters:
//   - weight: number - package weight in kilograms
//   - distance: number - shipping distance in kilometers
//   - expressShipping: boolean - whether to use express shipping
// 
// Returns: number - total cost in USD, rounded to 2 decimal places
// 
// Behavior:
//   - Base cost is $5
//   - Add $0.50 per kg
//   - Add $0.10 per km
//   - Double the total if express shipping selected
// 
// Constraints:
//   - weight and distance must be positive numbers
//   - throw Error if invalid parameters
// 
// Examples:
//   - calculateShippingCost(5, 100, false) -> 17.50
//   - calculateShippingCost(2, 50, true) -> 24.00
```

## Async Function Template

```
# Async function to [ACTION]
# Parameters: [PARAMETERS]
# Returns: Promise<[TYPE]>
# Error handling: [APPROACH]
# Timeout: [DURATION] seconds
```

### Example

```typescript
// Async function to fetch user data from API
// Parameters: userId (string)
// Returns: Promise<User> with id, name, email properties
// Error handling: retry 3 times on network errors, throw on 404
// Timeout: 5 seconds
// Use axios library
```

## Pure Function Template

```
# Pure function to [ACTION]
# Input: [DESCRIPTION]
# Output: [DESCRIPTION]
# No side effects
# Deterministic (same input always produces same output)
```

### Example

```python
# Pure function to calculate compound interest
# Input: principal (float), rate (float), time (int), frequency (int)
# Output: final amount (float)
# No side effects
# Deterministic
# Use formula: A = P(1 + r/n)^(nt)
```

## Function with Validation Template

```
# Function to [ACTION] with input validation
# Parameters: [PARAMETERS]
# Validation rules:
#   - [rule_1]
#   - [rule_2]
# Returns: [TYPE] or throws ValidationError
# Error messages should be descriptive
```

### Example

```java
// Function to create user account with input validation
// Parameters: username (String), email (String), age (int)
// Validation rules:
//   - username: 3-20 chars, alphanumeric only
//   - email: valid email format
//   - age: between 18 and 120
// Returns: User object or throws ValidationError
// Error messages should specify which field failed
```

## Higher-Order Function Template

```
# Higher-order function to [PURPOSE]
# Takes: [FUNCTION_PARAMETER] as parameter
# Returns: [RETURN_TYPE]
# Use case: [EXPLANATION]
```

### Example

```javascript
// Higher-order function to create debounced version of any function
// Takes: callback function and delay in milliseconds
// Returns: debounced function that delays execution
// Use case: prevent excessive API calls on user input
```

## Recursive Function Template

```
# Recursive function to [ACTION]
# Base case: [CONDITION]
# Recursive case: [APPROACH]
# Input: [PARAMETERS]
# Output: [RESULT]
# Time complexity: [BIG_O]
```

### Example

```python
# Recursive function to calculate factorial
# Base case: n <= 1 returns 1
# Recursive case: n * factorial(n-1)
# Input: n (positive integer)
# Output: factorial of n
# Time complexity: O(n)
# Include input validation for negative numbers
```

## Function with Error Handling Template

```
# Function to [ACTION] with comprehensive error handling
# Parameters: [PARAMETERS]
# Returns: [SUCCESS_RETURN] on success
# Error cases:
#   - [ERROR_CASE_1]: [ACTION]
#   - [ERROR_CASE_2]: [ACTION]
# Logging: log all errors with context
```

### Example

```typescript
// Function to parse JSON file with comprehensive error handling
// Parameters: filePath (string)
// Returns: parsed object on success
// Error cases:
//   - File not found: throw FileNotFoundError
//   - Invalid JSON: throw ParseError with line number
//   - Permission denied: throw PermissionError
// Logging: log all errors with file path and error details
```

## Utility Function Template

```
# Utility function to [PURPOSE]
# Common use case: [SCENARIO]
# Input: [INPUT_FORMAT]
# Output: [OUTPUT_FORMAT]
# Should be reusable across the application
```

### Example

```python
# Utility function to format currency values
# Common use case: displaying prices in UI
# Input: amount (float or int)
# Output: formatted string like "$1,234.56"
# Should be reusable across the application
# Support negative values with parentheses
```

## Test Helper Function Template

```
# Test helper function to [PURPOSE]
# Used in: [TEST_CONTEXT]
# Creates: [WHAT_IT_CREATES]
# Returns: [RETURN_VALUE]
# Should be idempotent
```

### Example

```javascript
// Test helper function to create mock user data
// Used in: unit tests for user service
// Creates: user object with all required fields
// Returns: User object with random but valid data
// Should be idempotent - calling multiple times creates independent objects
```

---

## Tips for Using These Templates

1. **Copy the template** that matches your needs
2. **Fill in the brackets** with your specific requirements
3. **Add more details** if the task is complex
4. **Include examples** for clarity
5. **Let Copilot generate** the implementation
6. **Review and test** the generated code

## Related Resources

- [Prompt Engineering Guide](../../guides/prompt-engineering-guide.md)
- [Exercises](../../cheatsheets/exercises.md)
- [Copilot Features](../../cheatsheets/copilot-features.md)
