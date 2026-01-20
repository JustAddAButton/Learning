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