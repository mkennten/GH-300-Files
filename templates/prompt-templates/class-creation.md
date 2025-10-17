# Class Creation Prompt Templates

Templates for generating classes and objects with GitHub Copilot.

## Basic Class Template

```
# [ClassName] class for [PURPOSE]
# Properties:
#   - [property1]: [type] - [description]
#   - [property2]: [type] - [description]
# Methods:
#   - [method1]([params]): [return] - [description]
#   - [method2]([params]): [return] - [description]
```

### Example

```python
# User class for authentication system
# Properties:
#   - id: int - unique user identifier
#   - username: str - user's username
#   - email: str - user's email address
#   - created_at: datetime - account creation timestamp
# Methods:
#   - validate_email(): bool - check if email is valid
#   - to_dict(): dict - convert to dictionary
#   - from_dict(data): User - create User from dictionary
```

## Data Model Class Template

```
# Data model class: [ClassName]
# Represents: [WHAT_IT_REPRESENTS]
# 
# Fields:
#   - [field1]: [type] - [description] [constraints]
#   - [field2]: [type] - [description] [constraints]
# 
# Methods:
#   - __init__(): initialize with parameters
#   - __str__(): string representation
#   - __repr__(): developer representation
#   - [custom_method]: [description]
# 
# Validation:
#   - [validation_rule_1]
#   - [validation_rule_2]
```

### Example

```python
# Data model class: Product
# Represents: product in e-commerce catalog
# 
# Fields:
#   - id: str - unique product ID (UUID format)
#   - name: str - product name (max 200 chars)
#   - price: Decimal - price (must be positive, 2 decimal places)
#   - category: str - product category
#   - stock: int - available quantity (non-negative)
# 
# Methods:
#   - __init__(): initialize with parameters
#   - __str__(): return name and price
#   - __repr__(): developer-friendly representation
#   - is_in_stock(): bool - check if available
# 
# Validation:
#   - price must be positive
#   - stock cannot be negative
#   - name cannot be empty
```

## Service Class Template

```
# Service class: [ClassName]
# Responsibility: [WHAT_IT_DOES]
# Dependencies: [DEPENDENCIES]
# 
# Public methods:
#   - [method1]: [description]
#   - [method2]: [description]
# 
# Private methods:
#   - [helper_method]: [description]
# 
# Error handling: [APPROACH]
```

### Example

```typescript
// Service class: UserService
// Responsibility: manage user CRUD operations
// Dependencies: UserRepository, EmailService, Logger
// 
// Public methods:
//   - createUser(data): Promise<User> - create new user
//   - getUserById(id): Promise<User> - retrieve user
//   - updateUser(id, data): Promise<User> - update user
//   - deleteUser(id): Promise<void> - soft delete user
// 
// Private methods:
//   - validateUserData(data): void - validate input
//   - hashPassword(password): string - hash password
// 
// Error handling: throw custom errors, log all operations
```

## Repository Pattern Template

```
# Repository class: [EntityName]Repository
# Purpose: data access layer for [Entity]
# Database: [DATABASE_TYPE]
# 
# CRUD operations:
#   - create([entity]): [ReturnType]
#   - findById(id): [ReturnType]
#   - findAll(filters): [ReturnType]
#   - update(id, data): [ReturnType]
#   - delete(id): [ReturnType]
# 
# Additional queries:
#   - [custom_query_1]
#   - [custom_query_2]
# 
# Use transactions where appropriate
```

### Example

```java
// Repository class: OrderRepository
// Purpose: data access layer for Order entity
// Database: PostgreSQL via JPA
// 
// CRUD operations:
//   - create(Order): Order
//   - findById(Long): Optional<Order>
//   - findAll(Pageable): Page<Order>
//   - update(Long, Order): Order
//   - delete(Long): void
// 
// Additional queries:
//   - findByUserId(Long): List<Order>
//   - findByDateRange(Date, Date): List<Order>
//   - findPendingOrders(): List<Order>
// 
// Use transactions where appropriate
// Include proper exception handling
```

## Builder Pattern Template

```
# Builder class for [ClassName]
# Purpose: construct complex [Object] step by step
# 
# Builder methods:
#   - with[Property1]([type]): self - set property1
#   - with[Property2]([type]): self - set property2
# 
# Build method:
#   - build(): [ClassName] - construct final object
# 
# Validation:
#   - validate required fields in build()
#   - provide sensible defaults
```

### Example

```typescript
// Builder class for User
// Purpose: construct complex User object step by step
// 
// Builder methods:
//   - withUsername(string): this - set username
//   - withEmail(string): this - set email
//   - withRole(string): this - set role
//   - withPermissions(string[]): this - set permissions
// 
// Build method:
//   - build(): User - construct final object
// 
// Validation:
//   - username and email are required
//   - default role is 'user' if not specified
//   - validate email format in build()
```

## Singleton Pattern Template

```
# Singleton class: [ClassName]
# Purpose: [WHY_SINGLETON_NEEDED]
# 
# Private constructor
# Static getInstance() method
# 
# Properties:
#   - [property1]: [type]
# 
# Methods:
#   - [method1]: [description]
# 
# Thread-safe implementation
```

### Example

```python
# Singleton class: DatabaseConnection
# Purpose: maintain single database connection pool
# 
# Private constructor
# Static getInstance() method
# 
# Properties:
#   - connection_pool: ConnectionPool
#   - max_connections: int
# 
# Methods:
#   - get_connection(): Connection - get available connection
#   - release_connection(conn): void - return connection to pool
# 
# Thread-safe implementation using threading.Lock
```

## Abstract Base Class Template

```
# Abstract base class: [ClassName]
# Purpose: [INTERFACE_PURPOSE]
# 
# Abstract methods (must be implemented):
#   - [abstract_method1]: [description]
#   - [abstract_method2]: [description]
# 
# Concrete methods (provided):
#   - [concrete_method]: [description]
# 
# Subclasses: [LIST_EXPECTED_SUBCLASSES]
```

### Example

```java
// Abstract base class: PaymentProcessor
// Purpose: define interface for payment processing strategies
// 
// Abstract methods (must be implemented):
//   - processPayment(amount, currency): PaymentResult
//   - refund(transactionId, amount): RefundResult
//   - validatePaymentInfo(info): boolean
// 
// Concrete methods (provided):
//   - logTransaction(transaction): void - log to database
//   - sendReceipt(email, details): void - send email receipt
// 
// Subclasses: CreditCardProcessor, PayPalProcessor, CryptoProcessor
```

## Interface/Protocol Template

```
# Interface: [InterfaceName]
# Purpose: [CONTRACT_DESCRIPTION]
# 
# Methods:
#   - [method1]([params]): [return] - [description]
#   - [method2]([params]): [return] - [description]
# 
# Implementing classes must provide: [REQUIREMENTS]
```

### Example

```typescript
// Interface: CacheProvider
// Purpose: define contract for caching implementations
// 
// Methods:
//   - get(key: string): Promise<any> - retrieve cached value
//   - set(key: string, value: any, ttl?: number): Promise<void>
//   - delete(key: string): Promise<void>
//   - clear(): Promise<void> - clear all cache
//   - has(key: string): Promise<boolean> - check if key exists
// 
// Implementing classes must provide: connection management, error handling
// Expected implementations: RedisCache, MemoryCache, FileCache
```

## Entity/Model Class Template

```
# [Framework] Model: [ModelName]
# Table: [table_name]
# Purpose: [ENTITY_PURPOSE]
# 
# Fields:
#   - [field1]: [type] - [constraints] - [description]
#   - [field2]: [type] - [constraints] - [description]
# 
# Relationships:
#   - [relationship1]: [type] - [description]
#   - [relationship2]: [type] - [description]
# 
# Meta options:
#   - ordering: [ORDER_BY]
#   - indexes: [INDEX_FIELDS]
# 
# Methods:
#   - [custom_method]: [description]
```

### Example

```python
# Django Model: BlogPost
# Table: blog_posts
# Purpose: represent blog post with author and comments
# 
# Fields:
#   - id: AutoField - primary key
#   - title: CharField(max_length=200) - post title
#   - slug: SlugField(unique=True) - URL-friendly title
#   - content: TextField - post content
#   - author: ForeignKey(User) - post author
#   - created_at: DateTimeField(auto_now_add=True)
#   - updated_at: DateTimeField(auto_now=True)
#   - published: BooleanField(default=False)
# 
# Relationships:
#   - comments: one-to-many - post comments
#   - tags: many-to-many - post tags
# 
# Meta options:
#   - ordering: ['-created_at']
#   - indexes: ['slug', 'created_at']
# 
# Methods:
#   - __str__(): return title
#   - get_absolute_url(): return detail page URL
#   - is_published(): check if post is published
```

## Enum Class Template

```
# Enum class: [EnumName]
# Purpose: [WHAT_IT_REPRESENTS]
# 
# Values:
#   - [VALUE1] = [representation] - [meaning]
#   - [VALUE2] = [representation] - [meaning]
# 
# Methods (if needed):
#   - [helper_method]: [description]
```

### Example

```python
# Enum class: OrderStatus
# Purpose: represent possible order states
# 
# Values:
#   - PENDING = 'pending' - order created, awaiting payment
#   - PAID = 'paid' - payment received
#   - PROCESSING = 'processing' - order being prepared
#   - SHIPPED = 'shipped' - order dispatched
#   - DELIVERED = 'delivered' - order completed
#   - CANCELLED = 'cancelled' - order cancelled
#   - REFUNDED = 'refunded' - payment refunded
# 
# Methods:
#   - is_final(): bool - check if status is terminal
#   - can_cancel(): bool - check if order can be cancelled
```

---

## Tips for Using These Templates

1. **Choose the right pattern** for your use case
2. **Fill in all placeholders** with specific details
3. **Add framework-specific decorators** if needed
4. **Include type hints** where applicable
5. **Specify relationships** clearly
6. **Review and refine** generated code

## Related Resources

- [Function Generation Templates](function-generation.md)
- [Prompt Engineering Guide](../../guides/prompt-engineering-guide.md)
- [Copilot Features](../../cheatsheets/copilot-features.md)
