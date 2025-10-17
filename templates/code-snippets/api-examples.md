# API Development Examples

Real-world examples of using GitHub Copilot for API development.

## REST API Endpoint (Express + TypeScript)

### Prompt

```typescript
// Express POST endpoint: /api/users
// Purpose: Create new user account
// 
// Request body: { email, password, firstName, lastName }
// Validation:
//   - email: valid format, unique
//   - password: min 8 chars, must include upper, lower, number
//   - names: non-empty strings
// 
// Process:
//   1. Validate input with Joi schema
//   2. Check if email exists in database
//   3. Hash password with bcrypt (10 rounds)
//   4. Create user in database
//   5. Generate JWT token (expires 24h)
//   6. Return: { user: {id, email, name}, token }
// 
// Error responses:
//   - 400: Validation errors (return field-specific errors)
//   - 409: Email already exists
//   - 500: Server error
// 
// Include TypeScript types for all inputs/outputs
// Use async/await
// Include proper error handling with try-catch
```

### Generated Code Example

```typescript
import { Router, Request, Response } from 'express';
import bcrypt from 'bcrypt';
import jwt from 'jsonwebtoken';
import Joi from 'joi';
import { db } from '../database';

const router = Router();

interface CreateUserRequest {
  email: string;
  password: string;
  firstName: string;
  lastName: string;
}

interface UserResponse {
  user: {
    id: string;
    email: string;
    name: string;
  };
  token: string;
}

const userSchema = Joi.object({
  email: Joi.string().email().required(),
  password: Joi.string().min(8)
    .pattern(/^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)/)
    .required(),
  firstName: Joi.string().min(1).required(),
  lastName: Joi.string().min(1).required(),
});

router.post('/api/users', async (req: Request, res: Response) => {
  try {
    // Validate input
    const { error, value } = userSchema.validate(req.body);
    if (error) {
      return res.status(400).json({
        error: 'Validation failed',
        details: error.details.map(d => ({
          field: d.path[0],
          message: d.message
        }))
      });
    }

    const { email, password, firstName, lastName } = value as CreateUserRequest;

    // Check if email exists
    const existingUser = await db.users.findOne({ email });
    if (existingUser) {
      return res.status(409).json({
        error: 'Email already exists'
      });
    }

    // Hash password
    const hashedPassword = await bcrypt.hash(password, 10);

    // Create user
    const user = await db.users.create({
      email,
      password: hashedPassword,
      firstName,
      lastName,
      createdAt: new Date()
    });

    // Generate JWT token
    const token = jwt.sign(
      { userId: user.id, email: user.email },
      process.env.JWT_SECRET!,
      { expiresIn: '24h' }
    );

    // Return response
    const response: UserResponse = {
      user: {
        id: user.id,
        email: user.email,
        name: `${user.firstName} ${user.lastName}`
      },
      token
    };

    res.status(201).json(response);

  } catch (error) {
    console.error('Error creating user:', error);
    res.status(500).json({
      error: 'Internal server error'
    });
  }
});

export default router;
```

## GraphQL Resolver

### Prompt

```typescript
// GraphQL resolver for User queries and mutations
// 
// Queries:
//   - user(id: ID!): User - get user by ID
//   - users(limit: Int, offset: Int): [User] - list users with pagination
// 
// Mutations:
//   - createUser(input: CreateUserInput!): User
//   - updateUser(id: ID!, input: UpdateUserInput!): User
//   - deleteUser(id: ID!): Boolean
// 
// Types:
//   User: { id, email, firstName, lastName, createdAt }
//   CreateUserInput: { email, password, firstName, lastName }
//   UpdateUserInput: { firstName?, lastName?, email? }
// 
// Authorization: require authentication for all mutations
// Error handling: throw GraphQL errors with appropriate messages
// Use TypeScript with proper types
```

## FastAPI Endpoint (Python)

### Prompt

```python
# FastAPI endpoint for product search
# 
# GET /api/products/search
# Query parameters:
#   - q: str - search query (required)
#   - category: str - filter by category (optional)
#   - min_price: float - minimum price (optional)
#   - max_price: float - maximum price (optional)
#   - limit: int - max results (default 10, max 100)
#   - offset: int - pagination offset (default 0)
# 
# Returns: {
#   products: List[Product],
#   total: int,
#   limit: int,
#   offset: int
# }
# 
# Product schema: id, name, description, price, category, in_stock
# 
# Implementation:
#   - Use SQLAlchemy for database queries
#   - Full-text search on name and description
#   - Apply filters with proper SQL
#   - Include pagination
#   - Add response model with Pydantic
#   - Handle errors (return 400 for invalid params)
```

## WebSocket Handler

### Prompt

```javascript
// WebSocket handler for real-time chat
// 
// Events:
//   Client -> Server:
//     - 'join': { roomId, userId, username }
//     - 'message': { roomId, userId, text, timestamp }
//     - 'typing': { roomId, userId, isTyping }
//   
//   Server -> Client:
//     - 'user_joined': { userId, username }
//     - 'user_left': { userId }
//     - 'message': { messageId, userId, username, text, timestamp }
//     - 'typing': { userId, username, isTyping }
// 
// Features:
//   - Track users in each room
//   - Broadcast messages to room participants only
//   - Handle disconnections (notify room)
//   - Store message history in Redis
//   - Rate limiting: 10 messages per minute per user
// 
// Use Socket.io
// Include error handling
// Add authentication middleware
```

## gRPC Service

### Prompt

```go
// gRPC service implementation for UserService
// 
// Proto definition:
// service UserService {
//   rpc GetUser(GetUserRequest) returns (User);
//   rpc ListUsers(ListUsersRequest) returns (ListUsersResponse);
//   rpc CreateUser(CreateUserRequest) returns (User);
//   rpc UpdateUser(UpdateUserRequest) returns (User);
//   rpc DeleteUser(DeleteUserRequest) returns (Empty);
// }
// 
// Implementation requirements:
//   - Connect to PostgreSQL database
//   - Use context for cancellation
//   - Add request validation
//   - Include error handling with proper gRPC status codes
//   - Add logging for all operations
//   - Use prepared statements for SQL
//   - Include transaction support for CreateUser
// 
// Messages use protobuf types defined in user.proto
```

## Microservice Communication

### Prompt

```python
# Microservice client for Order Service
# 
# Service endpoints:
#   - POST /orders - create order
#   - GET /orders/{id} - get order details
#   - PUT /orders/{id}/status - update order status
#   - GET /orders/user/{userId} - list user's orders
# 
# Features:
#   - Use requests library with session
#   - Include circuit breaker pattern (fail after 3 errors, retry after 60s)
#   - Add request timeout (5 seconds)
#   - Implement retry logic (3 attempts with exponential backoff)
#   - Include authentication headers (Bearer token)
#   - Comprehensive error handling
#   - Logging for all requests
# 
# Return: OrderServiceClient class with async methods
# Use dataclasses for request/response models
# Include type hints
```

## API Rate Limiter

### Prompt

```typescript
// Express middleware for API rate limiting
// 
// Configuration:
//   - 100 requests per IP per 15 minutes
//   - Store counts in Redis
//   - Use sliding window algorithm
//   - Different limits for authenticated users (1000 req/15min)
// 
// Response headers:
//   - X-RateLimit-Limit: total allowed
//   - X-RateLimit-Remaining: requests remaining
//   - X-RateLimit-Reset: timestamp when limit resets
// 
// When limit exceeded:
//   - Return 429 status
//   - Include Retry-After header
//   - Response body: { error, retryAfter, limit }
// 
// Options:
//   - Skip rate limiting for whitelisted IPs
//   - Custom limits per endpoint (pass as middleware option)
//   - Bypass for admin users
// 
// Use ioredis for Redis connection
// TypeScript with proper types
```

## API Documentation Generation

### Prompt

```python
# Generate OpenAPI 3.0 documentation for FastAPI app
# 
# Endpoints to document:
#   - GET /api/products - list products
#   - GET /api/products/{id} - get product details
#   - POST /api/products - create product (requires auth)
#   - PUT /api/products/{id} - update product (requires auth)
#   - DELETE /api/products/{id} - delete product (requires admin)
# 
# Include:
#   - Request/response schemas with examples
#   - Authentication requirements (Bearer JWT)
#   - Error response schemas (400, 401, 403, 404, 500)
#   - Pagination parameters for list endpoint
#   - Search and filter parameters
# 
# Add tags: Products, Authentication
# Include detailed descriptions for each endpoint
# Add security schemes for JWT authentication
# Use Pydantic models for schema generation
```

---

## Tips for API Development with Copilot

1. **Be specific about framework**: Mention Express, FastAPI, etc.
2. **Include auth requirements**: Specify JWT, OAuth, etc.
3. **Define response formats**: JSON structure with types
4. **Specify error handling**: Status codes and error messages
5. **Mention dependencies**: Libraries and tools to use
6. **Include validation**: Input validation rules
7. **Add performance requirements**: Caching, rate limiting
8. **Specify testing**: Unit tests, integration tests

## Related Resources

- [Function Generation Templates](../prompt-templates/function-generation.md)
- [Class Creation Templates](../prompt-templates/class-creation.md)
- [Copilot Features](../../cheatsheets/copilot-features.md)
- [Prompt Engineering Guide](../../guides/prompt-engineering-guide.md)
