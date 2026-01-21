Typescript Fundamentals
--------------------------------------------------

### Overview
**Focus:** Type system and configuration

**Format:** Theory + Hands-on exercises

**Mosh Course:** Complete Sections 1-4 (accelerated pace)

### 1\. Introduction & Setup

**Why TypeScript?**

-   Quick discussion: Pain points with JavaScript in large applications
-   TypeScript benefits: type safety, IDE support, refactoring confidence, documentation
-   Real-world examples where TypeScript prevents bugs
-   The TypeScript compilation process

**Environment Setup**

-   Install TypeScript globally: npm install -g typescript
-   Verify installation: tsc --version
-   Set up VS Code with TypeScript extensions
-   Create first TypeScript file and compile: tsc filename.ts

### 2\. Core Type System

**Basic Types & Type Inference**

-   Primitive types: string, number, boolean, null, undefined
-   Array types: number[] vs Array<number>
-   Tuple types
-   any, unknown, never, void
-   Type inference vs explicit annotations
-   Mini Exercise: Annotate variables in a provided code snippet

Exercise
```Typescript
// Basic variables - add type annotations
let username = "john_doe";
let age = 28;
let isActive = true;
let score = null;

// Arrays - add type annotations
let numbers = [1, 2, 3, 4, 5];
let tags = ["typescript", "javascript", "react"];
let mixedData = [1, "two", 3, "four"];

// Objects - add type annotations (consider creating interfaces)
let user = {
  id: 101,
  name: "Alice Smith",
  email: "alice@example.com",
  isAdmin: false
};

let product = {
  id: "prod-123",
  title: "Laptop",
  price: 999.99,
  inStock: true,
  tags: ["electronics", "computers"]
};

// Function parameters and return types - add annotations
function greet(name, greeting) {
  return `${greeting}, ${name}!`;
}

function calculateTotal(prices) {
  return prices.reduce((sum, price) => sum + price, 0);
}

function findUser(id) {
  // Simulated - might return user or null if not found
  return id > 0 ? { id, name: "User " + id } : null;
}

// Complex scenarios
let callback = (message) => console.log(message);

let userData = {
  name: "Bob",
  age: 30,
  address: {
    street: "123 Main St",
    city: "Boston",
    zipCode: "02101"
  },
  hobbies: ["reading", "coding"]
};

// Edge cases
let unknownValue;  // Will be assigned later
let anyValue = JSON.parse('{"key": "value"}');
```
Solution
```Typescript
// Basic variables - add type annotations
let username: string = "john_doe";
let age: number = 28;
let isActive: boolean = true;
let score: number | null = null;

// Arrays - add type annotations
let numbers: number[] = [1, 2, 3, 4, 5];
let tags: string[] = ["typescript", "javascript", "react"];
let mixedData: (number | string)[] = [1, "two", 3, "four"];

// Objects - add type annotations (consider creating interfaces)
interface User {
  id: number;
  name: string;
  email: string;
  isAdmin: boolean;
}

let user: User = {
  id: 101,
  name: "Alice Smith",
  email: "alice@example.com",
  isAdmin: false
};

interface Product {
  id: string;
  title: string;
  price: number;
  inStock: boolean;
  tags: string[];
}

let product: Product = {
  id: "prod-123",
  title: "Laptop",
  price: 999.99,
  inStock: true,
  tags: ["electronics", "computers"]
};

// Function parameters and return types - add annotations
function greet(name: string, greeting: string): string {
  return `${greeting}, ${name}!`;
}

function calculateTotal(prices: number[]): number {
  return prices.reduce((sum, price) => sum + price, 0);
}

function findUser(id: number): { id: number; name: string } | null {
  // Simulated - might return user or null if not found
  return id > 0 ? { id, name: "User " + id } : null;
}

// Complex scenarios
let callback: (message: string) => void = (message) => console.log(message);

interface Address {
  street: string;
  city: string;
  zipCode: string;
}

interface UserData {
  name: string;
  age: number;
  address: Address;
  hobbies: string[];
}

let userData: UserData = {
  name: "Bob",
  age: 30,
  address: {
    street: "123 Main St",
    city: "Boston",
    zipCode: "02101"
  },
  hobbies: ["reading", "coding"]
};

// Edge cases
let unknownValue: string;  // Will be assigned later
let anyValue: any = JSON.parse('{"key": "value"}');
```

**Bonus Challenges**

1.  Create interfaces for the user, product, and userData objects
2.  Add a union type for a variable that could be a string or number
3.  Create a tuple type for coordinates: [latitude, longitude]
4.  Add a type annotation for an array of user objects
5.  Create a type alias for a status that can only be "pending", "approved", or "rejected"

```Typescript
// Example User
const sampleUser = {
  id: "user-001",
  email: "john.doe@example.com",
  firstName: "John",
  lastName: "Doe",
  password: "hashed_password_here",
  role: "customer",
  createdAt: "2025-01-15",
  phone: "+1-555-0123",
  shippingAddress: {
    street: "123 Main St",
    city: "Boston",
    state: "MA",
    zipCode: "02101",
    country: "USA"
  }
};

// Example Product
const sampleProduct = {
  id: "prod-101",
  name: "Wireless Headphones",
  description: "High-quality bluetooth headphones with noise cancellation",
  price: 199.99,
  discountPercentage: 10,
  category: "Electronics",
  tags: ["audio", "wireless", "bluetooth"],
  inStock: true,
  stockQuantity: 50,
  imageUrl: "https://example.com/images/headphones.jpg",
  createdAt: "2024-12-01"
};

// Example Order
const sampleOrder = {
  id: "order-5001",
  userId: "user-001",
  orderDate: "2025-01-20",
  status: "shipped",
  items: [
    {
      productId: "prod-101",
      productName: "Wireless Headphones",
      quantity: 2,
      priceAtPurchase: 199.99
    },
    {
      productId: "prod-202",
      productName: "Phone Case",
      quantity: 1,
      priceAtPurchase: 29.99
    }
  ],
  subtotal: 429.97,
  tax: 34.40,
  shippingCost: 9.99,
  total: 474.36,
  shippingAddress: {
    street: "123 Main St",
    city: "Boston",
    state: "MA",
    zipCode: "02101",
    country: "USA"
  },
  paymentMethod: "credit_card",
  paymentStatus: "paid",
  trackingNumber: "TRACK123456789"
};
```
**Interfaces & Type Aliases**
-   Interface syntax and usage
-   Type aliases with type keyword
-   When to use interface vs type alias
-   Optional properties (?) and readonly properties
-   Extending interfaces

**Hands-on Exercise: Create interfaces for a simple e-commerce model (User, Product, Order)**

```Typescript
// Example User
const sampleUser = {
  id: "user-001",
  email: "john.doe@example.com",
  firstName: "John",
  lastName: "Doe",
  password: "hashed_password_here",
  role: "customer",
  createdAt: "2025-01-15",
  phone: "+1-555-0123",
  shippingAddress: {
    street: "123 Main St",
    city: "Boston",
    state: "MA",
    zipCode: "02101",
    country: "USA"
  }
};

// Example Product
const sampleProduct = {
  id: "prod-101",
  name: "Wireless Headphones",
  description: "High-quality bluetooth headphones with noise cancellation",
  price: 199.99,
  discountPercentage: 10,
  category: "Electronics",
  tags: ["audio", "wireless", "bluetooth"],
  inStock: true,
  stockQuantity: 50,
  imageUrl: "https://example.com/images/headphones.jpg",
  createdAt: "2024-12-01"
};

// Example Order
const sampleOrder = {
  id: "order-5001",
  userId: "user-001",
  orderDate: "2025-01-20",
  status: "shipped",
  items: [
    {
      productId: "prod-101",
      productName: "Wireless Headphones",
      quantity: 2,
      priceAtPurchase: 199.99
    },
    {
      productId: "prod-202",
      productName: "Phone Case",
      quantity: 1,
      priceAtPurchase: 29.99
    }
  ],
  subtotal: 429.97,
  tax: 34.40,
  shippingCost: 9.99,
  total: 474.36,
  shippingAddress: {
    street: "123 Main St",
    city: "Boston",
    state: "MA",
    zipCode: "02101",
    country: "USA"
  },
  paymentMethod: "credit_card",
  paymentStatus: "paid",
  trackingNumber: "TRACK123456789"
};
```
Solution 
```Typescript
// Address interface used by User and Order
interface Address {
  street: string;
  city: string;
  state: string;
  zipCode: string;
  country: string;
}

// User interface
interface User {
  id: string;
  email: string;
  firstName: string;
  lastName: string;
  password: string;
  role: string;
  createdAt: string;
  phone?: string;
  shippingAddress?: Address;
}

// Product interface
interface Product {
  id: string;
  name: string;
  description: string;
  price: number;
  discountPercentage?: number;
  category: string;
  tags: string[];
  inStock: boolean;
  stockQuantity: number;
  imageUrl: string;
  createdAt: string;
}

// OrderItem interface for items within an order
interface OrderItem {
  productId: string;
  productName: string;
  quantity: number;
  priceAtPurchase: number;
}

// Order interface
interface Order {
  id: string;
  userId: string;
  orderDate: string;
  status: string;
  items: OrderItem[];
  subtotal: number;
  tax: number;
  shippingCost: number;
  total: number;
  shippingAddress: Address;
  paymentMethod: string;
  paymentStatus: string;
  trackingNumber?: string;
}

// Example User
const sampleUser: User = {
  id: "user-001",
  email: "john.doe@example.com",
  firstName: "John",
  lastName: "Doe",
  password: "hashed_password_here",
  role: "customer",
  createdAt: "2025-01-15",
  phone: "+1-555-0123",
  shippingAddress: {
    street: "123 Main St",
    city: "Boston",
    state: "MA",
    zipCode: "02101",
    country: "USA"
  }
};

// Example Product
const sampleProduct = {
  id: "prod-101",
  name: "Wireless Headphones",
  description: "High-quality bluetooth headphones with noise cancellation",
  price: 199.99,
  discountPercentage: 10,
  category: "Electronics",
  tags: ["audio", "wireless", "bluetooth"],
  inStock: true,
  stockQuantity: 50,
  imageUrl: "https://example.com/images/headphones.jpg",
  createdAt: "2024-12-01"
};

// Example Order
const sampleOrder = {
  id: "order-5001",
  userId: "user-001",
  orderDate: "2025-01-20",
  status: "shipped",
  items: [
    {
      productId: "prod-101",
      productName: "Wireless Headphones",
      quantity: 2,
      priceAtPurchase: 199.99
    },
    {
      productId: "prod-202",
      productName: "Phone Case",
      quantity: 1,
      priceAtPurchase: 29.99
    }
  ],
  subtotal: 429.97,
  tax: 34.40,
  shippingCost: 9.99,
  total: 474.36,
  shippingAddress: {
    street: "123 Main St",
    city: "Boston",
    state: "MA",
    zipCode: "02101",
    country: "USA"
  },
  paymentMethod: "credit_card",
  paymentStatus: "paid",
  trackingNumber: "TRACK123456789"
};
```
Union & Intersection Types

-   Union types (type A | type B)
-   Type narrowing with type guards
-   Intersection types (type A & type B)
-   Practical use cases
-   Quick Exercise 1: Format ID

Exericse 1:
- Create a function formatId that accepts either a number or string ID and returns a formatted string.
-   If input is a number, prefix with "ID-" and pad to 6 digits (e.g., 123 → "ID-000123")
-   If input is a string, return uppercase (e.g., "abc123" → "ABC123")

```Typescript
// Your code here
function formatId(id: /* add type */) {
  // Implement with type checking
}

// Test cases
console.log(formatId(123));        // "ID-000123"
console.log(formatId(42));         // "ID-000042"
console.log(formatId("abc123"));   // "ABC123"
console.log(formatId("user-001")); // "USER-001"
```
Solution
```Typescript
function formatId(id: string | number): string {
  if (typeof id === "number") {
    return "ID-" + id.toString().padStart(6, "0");
  } else {
    return id.toUpperCase();
  }
}

// Test cases
console.log(formatId(123));        // "ID-000123"
console.log(formatId(42));         // "ID-000042"
console.log(formatId("abc123"));   // "ABC123"
console.log(formatId("user-001")); // "USER-001"
```
Exercise 2: Calculate Area
-   Create a function calculateArea that accepts either:
-   A number (for a square: side length)
-   An object with width and height (for a rectangle)
-   An object with radius (for a circle)
-   Return the calculated area.

```Typescript
// Your code here
function calculateArea(shape: /* add union type */) {
  // Implement with type guards
}

// Test cases
console.log(calculateArea(5));                          // 25 (square)
console.log(calculateArea({ width: 10, height: 5 }));   // 50 (rectangle)
console.log(calculateArea({ radius: 3 }));              // ~28.27 (circle)
```
Solution
```Typescript
type Square = number;
type Rectangle = { width: number; height: number };
type Circle = { radius: number };

function calculateArea(shape: Square | Rectangle | Circle): number {
  if (typeof shape === "number") {
    // Square
    return shape * shape;
  } else if ("radius" in shape) {
    // Circle
    return Math.PI * shape.radius * shape.radius;
  } else {
    // Rectangle
    return shape.width * shape.height;
  }
}

// Test cases
console.log(calculateArea(5));                          // 25
console.log(calculateArea({ width: 10, height: 5 }));   // 50
console.log(calculateArea({ radius: 3 }));              // 28.274333882308138
```
Solution with interface
```Typescript
interface Rectangle {
  width: number;
  height: number;
}

interface Circle {
  radius: number;
}

type Shape = number | Rectangle | Circle;

function calculateArea(shape: Shape): number {
  if (typeof shape === "number") {
    return shape * shape;
  } else if ("radius" in shape) {
    return Math.PI * shape.radius ** 2;
  } else {
    return shape.width * shape.height;
  }
}
```
**Quick Exercise 3: Process Response**
-   Create a function processApiResponse that handles different response types:
-   Success: { success: true, data: any }
-   Error: { success: false, error: string }
-   Return either the data or throw an error with the error message.
```Typescript
// Your code here
function processApiResponse(response: /* add union type */) {
  // Implement with type narrowing
}

// Test cases
const successResponse = { success: true, data: { user: "John" } };
const errorResponse = { success: false, error: "Not found" };

console.log(processApiResponse(successResponse)); // { user: "John" }
// processApiResponse(errorResponse); // Throws error: "Not found"
```
```Typescript
type SuccessResponse = {
  success: true;
  data: any;
};

type ErrorResponse = {
  success: false;
  error: string;
};

type ApiResponse = SuccessResponse | ErrorResponse;

function processApiResponse(response: ApiResponse): any {
  if (response.success) {
    return response.data;
  } else {
    throw new Error(response.error);
  }
}

// Test cases
const successResponse = { success: true, data: { user: "John" } };
const errorResponse = { success: false, error: "Not found" };

console.log(processApiResponse(successResponse)); // { user: "John" }

try {
  processApiResponse(errorResponse);
} catch (error) {
  console.log(error); // Error: Not found
}
```
Solution with generic data type
```Typescript
type SuccessResponse<T> = {
  success: true;
  data: T;
};

type ErrorResponse = {
  success: false;
  error: string;
};

type ApiResponse<T> = SuccessResponse<T> | ErrorResponse;

function processApiResponse<T>(response: ApiResponse<T>): T {
  if (response.success) {
    return response.data;
  } else {
    throw new Error(response.error);
  }
}

// Now with type safety for the data!
interface User {
  user: string;
}

const successResponse: ApiResponse<User> = { 
  success: true, 
  data: { user: "John" } 
};

const result = processApiResponse(successResponse); 
// result is typed as User
console.log(result.user); // TypeScript knows this is safe
```
**Quick Exercise 4: Convert Temperature**
-   Create a function that converts temperature between Celsius and Fahrenheit.
-   Accept either a number (assumes Celsius) OR an object { value: number, unit: 'C' | 'F' }
-   Return an object with both conversions
```Typescript
// Your code here
function convertTemperature(temp: /* add union type */) {
  // Implement conversion logic
}

// Test cases
console.log(convertTemperature(0));                    // { celsius: 0, fahrenheit: 32 }
console.log(convertTemperature({ value: 100, unit: 'C' })); // { celsius: 100, fahrenheit: 212 }
console.log(convertTemperature({ value: 32, unit: 'F' }));  // { celsius: 0, fahrenheit: 32 }
```
Solution
```Typescript
function safeParse(input: string | object): object | null {
  if (typeof input === "string") {
    try {
      return JSON.parse(input);
    } catch (error) {
      return null;
    }
  } else {
    return input;
  }
}

// Test cases
console.log(safeParse('{"name": "John"}')); // { name: "John" }
console.log(safeParse({ name: "Jane" }));   // { name: "Jane" }
console.log(safeParse('invalid json'));     // null
console.log(safeParse('null'));             // null
console.log(safeParse('[1, 2, 3]'));        // [1, 2, 3]
```
**Quick Exercise 5: Safe Parse**
-   Create a function safeParse that accepts a string or an already-parsed object, and returns the parsed object.
-   If string: parse as JSON
-   If object: return as-is
-   Handle parse errors gracefully
```Typescript
function safeParse(input: /* add union type */): object | null {
  // Implement
}

// Test cases
console.log(safeParse('{"name": "John"}')); // { name: "John" }
console.log(safeParse({ name: "Jane" }));   // { name: "Jane" }
console.log(safeParse('invalid json'));     // null
```
Solution
```Typescript
function safeParse(input: string | object): object | null {
  if (typeof input === "string") {
    try {
      return JSON.parse(input);
    } catch (error) {
      return null;
    }
  } else {
    return input;
  }
}

// Test cases
console.log(safeParse('{"name": "John"}')); // { name: "John" }
console.log(safeParse({ name: "Jane" }));   // { name: "Jane" }
console.log(safeParse('invalid json'));     // null
console.log(safeParse('null'));             // null
console.log(safeParse('[1, 2, 3]'));        // [1, 2, 3]
```
Solution with generic data type.ts
```Typescript
function safeParse<T = any>(input: string | T): T | null {
  if (typeof input === "string") {
    try {
      return JSON.parse(input) as T;
    } catch (error) {
      console.error("Failed to parse JSON:", error);
      return null;
    }
  } else {
    return input;
  }
}

// With type inference
interface User {
  name: string;
  age: number;
}

const user = safeParse<User>('{"name": "John", "age": 30}');
if (user) {
  console.log(user.name); // TypeScript knows user is User type
}
```

### 3. Advanced Concepts & Configuration

**Generics Fundamentals**
-   What are generics and why use them?
-   Generic functions: function identity<T>(arg: T): T
-   Generic interfaces and classes
-   Constraints with extends

**Exercise 1: Basic Generic Fetcher**
-   Create a generic fetchData function that:
-   Accepts a URL string
-   Returns a Promise of the generic type T
-   Uses the Fetch API
-   Handles JSON parsing
```Typescript
// Your code here
async function fetchData /* add generic syntax */(url: string) /* add return type */ {
  // Implement fetch logic
}

// Test cases
interface User {
  id: number;
  name: string;
  email: string;
}

interface Post {
  id: number;
  title: string;
  body: string;
  userId: number;
}

// Usage
const user = await fetchData<User>('https://api.example.com/users/1');
const posts = await fetchData<Post[]>('https://api.example.com/posts');
```
Solution
```Typescript
async function fetchData<T>(url: string): Promise<T> {
  const response = await fetch(url);
  
  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  }
  
  const data = await response.json();
  return data as T;
}

// Test cases
interface User {
  id: number;
  name: string;
  email: string;
}

interface Post {
  id: number;
  title: string;
  body: string;
  userId: number;
}

// Usage examples
async function examples() {
  const user = await fetchData<User>('https://jsonplaceholder.typicode.com/users/1');
  console.log(user.name); // TypeScript knows user has name property
  
  const posts = await fetchData<Post[]>('https://jsonplaceholder.typicode.com/posts');
  console.log(posts[0].title); // TypeScript knows posts is array of Post
}
```
**Exercise 2: Fetcher with Options**
-   Extend the fetcher to accept generic options and handle different HTTP methods.
```Typescript
// Your code here
interface FetchOptions {
  // Define options: method, headers, body, etc.
}

async function fetchData /* add generics */(
  url: string,
  options?: FetchOptions
) /* return type */ {
  // Implement
}

// Test cases
const newUser = await fetchData<User>('https://api.example.com/users', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name: 'John', email: 'john@example.com' })
});

const users = await fetchData<User[]>('https://api.example.com/users', {
  method: 'GET'
});
```
Solution
```Typescript
interface FetchOptions {
  method?: 'GET' | 'POST' | 'PUT' | 'DELETE' | 'PATCH';
  headers?: Record<string, string>;
  body?: string;
}

async function fetchData<T>(
  url: string,
  options?: FetchOptions
): Promise<T> {
  const config: RequestInit = {
    method: options?.method || 'GET',
    headers: {
      'Content-Type': 'application/json',
      ...options?.headers
    }
  };
  
  if (options?.body) {
    config.body = options.body;
  }
  
  const response = await fetch(url, config);
  
  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  }
  
  const data = await response.json();
  return data as T;
}

// Test cases
interface User {
  id?: number;
  name: string;
  email: string;
}

async function examples() {
  // GET request
  const users = await fetchData<User[]>('https://jsonplaceholder.typicode.com/users');
  
  // POST request
  const newUser = await fetchData<User>('https://jsonplaceholder.typicode.com/users', {
    method: 'POST',
    body: JSON.stringify({ name: 'John Doe', email: 'john@example.com' })
  });
  
  // PUT request
  const updatedUser = await fetchData<User>('https://jsonplaceholder.typicode.com/users/1', {
    method: 'PUT',
    body: JSON.stringify({ id: 1, name: 'Jane Doe', email: 'jane@example.com' })
  });
}
```
**Exercise 3: Fetcher with Options**
-   Create a generic API response wrapper that includes metadata.
```Typescript
// Your code here
interface ApiResponse /* add generic */ {
  // Define structure: data, status, message, etc.
}

async function fetchWithMetadata /* add generics */(
  url: string
) /* return type */ {
  // Implement with response wrapper
}

// Test cases
const response = await fetchWithMetadata<User>('https://api.example.com/users/1');
console.log(response.data.name);
console.log(response.status);
console.log(response.timestamp);
```
Solution
```Typescript
interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
  timestamp: Date;
  success: boolean;
}

async function fetchWithMetadata<T>(url: string): Promise<ApiResponse<T>> {
  const startTime = new Date();
  
  try {
    const response = await fetch(url);
    const data = await response.json();
    
    return {
      data: data as T,
      status: response.status,
      message: response.ok ? 'Success' : 'Request failed',
      timestamp: startTime,
      success: response.ok
    };
  } catch (error) {
    return {
      data: null as T,
      status: 500,
      message: error instanceof Error ? error.message : 'Unknown error',
      timestamp: startTime,
      success: false
    };
  }
}

// Test cases
interface User {
  id: number;
  name: string;
  email: string;
}

async function examples() {
  const response = await fetchWithMetadata<User>('https://jsonplaceholder.typicode.com/users/1');
  
  if (response.success) {
    console.log(response.data.name);     // TypeScript knows data is User
    console.log(response.status);         // 200
    console.log(response.timestamp);      // Date object
  } else {
    console.log(response.message);        // Error message
  }
  
  // Array response
  const usersResponse = await fetchWithMetadata<User[]>('https://jsonplaceholder.typicode.com/users');
  console.log(usersResponse.data.length);  // TypeScript knows data is User[]
}
```
**Exercise 4: Generic Data Store**
-   Create a generic in-memory data store with CRUD operations.
```Typescript
// Your code here
class DataStore /* add generics */ {
  // Implement generic storage
  
  // Methods to implement:
  // - getAll()
  // - getById(id)
  // - add(item)
  // - update(id, item)
  // - delete(id)
}

// Test cases
interface Product {
  id: number;
  name: string;
  price: number;
}

const productStore = new DataStore<Product>();
productStore.add({ id: 1, name: 'Laptop', price: 999 });
const product = productStore.getById(1);
```
Solution
```Typescript
class DataStore<T extends { id: number | string }> {
  private items: Map<number | string, T> = new Map();
  
  getAll(): T[] {
    return Array.from(this.items.values());
  }
  
  getById(id: number | string): T | undefined {
    return this.items.get(id);
  }
  
  add(item: T): T {
    this.items.set(item.id, item);
    return item;
  }
  
  update(id: number | string, updates: Partial<T>): T | undefined {
    const item = this.items.get(id);
    if (!item) return undefined;
    
    const updatedItem = { ...item, ...updates };
    this.items.set(id, updatedItem);
    return updatedItem;
  }
  
  delete(id: number | string): boolean {
    return this.items.delete(id);
  }
  
  find(predicate: (item: T) => boolean): T | undefined {
    return this.getAll().find(predicate);
  }
  
  filter(predicate: (item: T) => boolean): T[] {
    return this.getAll().filter(predicate);
  }
  
  clear(): void {
    this.items.clear();
  }
  
  get count(): number {
    return this.items.size;
  }
}

// Test cases
interface Product {
  id: number;
  name: string;
  price: number;
  inStock: boolean;
}

interface User {
  id: string;
  name: string;
  email: string;
  role: 'admin' | 'user';
}

// Usage examples
const productStore = new DataStore<Product>();

// Add products
productStore.add({ id: 1, name: 'Laptop', price: 999, inStock: true });
productStore.add({ id: 2, name: 'Mouse', price: 29, inStock: false });
productStore.add({ id: 3, name: 'Keyboard', price: 79, inStock: true });

// Get by ID
const product = productStore.getById(1);
console.log(product?.name); // "Laptop"

// Update
productStore.update(2, { inStock: true });

// Filter
const inStockProducts = productStore.filter(p => p.inStock);
console.log(inStockProducts.length); // 3

// Find
const expensiveProduct = productStore.find(p => p.price > 500);
console.log(expensiveProduct?.name); // "Laptop"

// Get all
const allProducts = productStore.getAll();
console.log(allProducts.length); // 3

// Delete
productStore.delete(2);
console.log(productStore.count); // 2

// User store with string IDs
const userStore = new DataStore<User>();
userStore.add({ id: 'user-001', name: 'Alice', email: 'alice@example.com', role: 'admin' });
```
**Exercise 5: Constrained Generics**
-   Create a fetcher that only works with objects that have an id property.
```Typescript
// Your code here
interface HasId {
  // Define constraint
}

async function fetchById /* add constrained generic */(
  url: string,
  id: number
) /* return type */ {
  // Implement with id constraint
}

// Should work
interface User extends HasId {
  name: string;
}

// Should work
const user = await fetchById<User>('https://api.example.com/users', 1);

// Should NOT compile
interface BadType {
  name: string; // No id property
}
// const bad = await fetchById<BadType>('...', 1); // Error!
```
Solution
```Typescript
interface HasId {
  id: number | string;
}

async function fetchById<T extends HasId>(
  url: string,
  id: number | string
): Promise<T> {
  const fullUrl = `${url}/${id}`;
  const response = await fetch(fullUrl);
  
  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  }
  
  const data = await response.json();
  return data as T;
}

// Valid - has id property
interface User extends HasId {
  name: string;
  email: string;
}

interface Product extends HasId {
  name: string;
  price: number;
}

async function examples() {
  // ✅ Works - User extends HasId
  const user = await fetchById<User>('https://jsonplaceholder.typicode.com/users', 1);
  console.log(user.id);    // TypeScript knows id exists
  console.log(user.name);  // TypeScript knows name exists
  
  // ✅ Works - Product extends HasId
  const product = await fetchById<Product>('https://api.example.com/products', 123);
  console.log(product.id);
  console.log(product.price);
}

// ❌ Won't compile - BadType doesn't have id property
interface BadType {
  name: string;
}

// Uncommenting this will cause a TypeScript error:
// const bad = await fetchById<BadType>('...', 1); 
// Error: Type 'BadType' does not satisfy the constraint 'HasId'
```
Solution (Advanced)
```Typescript
// Multiple constraints
interface Identifiable {
  id: number | string;
}

interface Timestamped {
  createdAt: Date;
  updatedAt: Date;
}

// Function that requires BOTH constraints
function logEntity<T extends Identifiable & Timestamped>(entity: T): void {
  console.log(`ID: ${entity.id}`);
  console.log(`Created: ${entity.createdAt}`);
  console.log(`Updated: ${entity.updatedAt}`);
}

interface Article extends Identifiable, Timestamped {
  title: string;
  content: string;
}

const article: Article = {
  id: 1,
  title: 'TypeScript Generics',
  content: 'Learning about generics...',
  createdAt: new Date('2025-01-01'),
  updatedAt: new Date('2025-01-07')
};

logEntity(article); // ✅ Works - has both id and timestamps
```

### 4. tsconfig.json Deep Dive

-   Creating tsconfig: tsc --init
-   Essential compiler options:
    -   target, module, lib
    -   strict and strictness flags
    -   outDir, rootDir
    -   moduleResolution, esModuleInterop

-   Practical configurations for different project types
-   Activity: Analyze and modify a tsconfig.json file

Homework Assignment

1.  Build Typed Utility Functions (1-2 hours)

    -   Create 5+ utility functions with full type safety
    -   Examples: debounce, deep clone, array chunking, object merge

3.  Data Models Project (1-2 hours)

    -   Design TypeScript interfaces for a domain (blog, social media, or inventory system)
    -   Include relationships between models
    -   Use generics for at least one reusable component

    -   Example using food recipe management system

**utility-functions.ts**
```Typescript
    // 1. Debounce: For search/filtering recipes
function debounce<T extends (...args: any[]) => void>(fn: T, delay: number): (...args: Parameters<T>) => void {
  let timer: ReturnType<typeof setTimeout> | null = null;
  return (...args: Parameters<T>) => {
    if (timer) clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}

// 2. Deep Clone: For duplicating recipe objects
function deepClone<T>(obj: T): T {
  return JSON.parse(JSON.stringify(obj));
}

// 3. Array Chunking: For paginating ingredients or steps
function chunkArray<T>(arr: T[], size: number): T[][] {
  const result: T[][] = [];
  for (let i = 0; i < arr.length; i += size) {
    result.push(arr.slice(i, i + size));
  }
  return result;
}

// 4. Object Merge: For combining ingredient lists
function mergeObjects<T, U>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

// 5. Filter Recipes by Tag
function filterRecipesByTag(recipes: Recipe[], tag: string): Recipe[] {
  return recipes.filter(recipe => recipe.tags.includes(tag));
}
```

**data models.ts**
```Typescript
// Ingredient model
interface Ingredient {
  id: string;
  name: string;
  quantity: string;
}

// Step model
interface Step {
  order: number;
  instruction: string;
}

// Recipe model
interface Recipe {
  id: string;
  title: string;
  ingredients: Ingredient[];
  steps: Step[];
  tags: string[];
  author: User;
}

// User model
interface User {
  id: string;
  name: string;
  favoriteRecipes: Recipe[];
}

// Generic reusable component: PaginatedList
interface PaginatedList<T> {
  items: T[];
  page: number;
  pageSize: number;
  total: number;
}

// Example usage of PaginatedList with recipes
const paginatedRecipes: PaginatedList<Recipe> = {
  items: [], // array of recipes
  page: 1,
  pageSize: 10,
  total: 100
};

// Relationship example: User with favorite recipes
const user: User = {
  id: "u1",
  name: "Chef Jamie",
  favoriteRecipes: []
};
```

### Key Takeaways

By the end of this workshop, we should be able to:

-   ✓ Explain TypeScript's value proposition
-   ✓ Use basic and advanced types confidently
-   ✓ Choose between interfaces and type aliases appropriately
-   ✓ Apply union/intersection types for flexible APIs
-   ✓ Write basic generic functions
-   ✓ Configure a TypeScript project with tsconfig.json