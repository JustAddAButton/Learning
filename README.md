# Learning



```
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

code
