## **1. Basics: Variables, Data Types, and Input/Output**

### **Code Example: Variables and Output**
```javascript
// Log a message to the console
console.log("Hello, JavaScript!");

// Declare variables
let name = "Alice";  // Mutable variable
const age = 25;      // Immutable variable
var city = "New York";  // Legacy declaration

// Output variables
console.log(`Name: ${name}, Age: ${age}, City: ${city}`);
```

### **Key Concepts**
- `let` (block-scoped), `const` (constants), and `var` (legacy, function-scoped).
- Use `console.log()` to output to the console.
- **String Interpolation**: Use backticks (`) and `${}`.

---

## **2. Conditional Statements**

### **Code Example: If/Else**
```javascript
let score = 85;

if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 75) {
  console.log("Grade: B");
} else if (score >= 60) {
  console.log("Grade: C");
} else {
  console.log("Grade: F");
}
```

### **Key Concepts**
- JavaScript uses `if`, `else if`, and `else` for conditional logic.
- Comparisons use operators like `==`, `===` (strict equality), `!=`, `!==`, `<`, `>`.

---

## **3. Loops**

### **Code Example: For and While**
```javascript
// For loop
for (let i = 1; i <= 5; i++) {
  console.log(`Count: ${i}`);
}

// While loop
let counter = 5;
while (counter > 0) {
  console.log(`Countdown: ${counter}`);
  counter--;
}
```

### **Key Concepts**
- `for` and `while` loops repeat tasks.
- Use `break` to exit a loop early, and `continue` to skip to the next iteration.

---

## **4. Functions**

### **Code Example: Regular and Arrow Functions**
```javascript
// Regular function
function greet(name) {
  return `Hello, ${name}!`;
}

// Arrow function
const add = (a, b) => a + b;

console.log(greet("Alice"));  // Output: Hello, Alice!
console.log(add(3, 4));       // Output: 7
```

### **Key Concepts**
- Functions can be declared with `function` or as arrow functions (`=>`).
- Arrow functions are shorter but lack `this` binding.

---

## **5. Arrays and Objects**

### **Code Example: Arrays**
```javascript
let fruits = ["apple", "banana", "cherry"];
fruits.push("orange");  // Add an item
console.log(fruits[1]);  // Access by index
console.log(fruits.length);  // Get array length
```

### **Code Example: Objects**
```javascript
let person = {
  name: "Alice",
  age: 25,
  city: "New York",
};

console.log(person.name);  // Access properties
person.age = 26;  // Update a property
console.log(person);
```

### **Key Concepts**
- **Arrays**: Ordered collections of items.
- **Objects**: Key-value pairs for storing related data.

---

## **6. Classes and OOP**

### **Code Example: Classes**
```javascript
class Dog {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  bark() {
    return `${this.name} says Woof!`;
  }
}

let myDog = new Dog("Buddy", 3);
console.log(myDog.bark());
```

### **Key Concepts**
- Use `class` to define classes.
- `constructor()` initializes properties, and methods define behavior.

---

## **7. Asynchronous JavaScript**

### **Code Example: Promises and Async/Await**
```javascript
// Using Promises
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve("Data fetched!"), 1000);
  });
};

fetchData().then((data) => console.log(data));

// Using Async/Await
const fetchAsyncData = async () => {
  let data = await fetchData();
  console.log(data);
};

fetchAsyncData();
```

### **Key Concepts**
- **Promises**: Handle async tasks with `.then()` and `.catch()`.
- **Async/Await**: Cleaner syntax for working with asynchronous code.

---

## **8. DOM Manipulation**

### **Code Example: Select and Modify Elements**
```javascript
// Select an element
const heading = document.querySelector("h1");

// Change text content
heading.textContent = "Welcome to JavaScript!";

// Add a class
heading.classList.add("highlight");

// Listen for a click
heading.addEventListener("click", () => {
  alert("Heading clicked!");
});
```

### **Key Concepts**
- Use `document.querySelector()` to select elements.
- Manipulate properties like `textContent` and `classList`.
- Add event listeners with `.addEventListener()`.

---

## **9. Error Handling**

### **Code Example: Try/Catch**
```javascript
try {
  let num = parseInt("abc");  // Invalid conversion
  if (isNaN(num)) throw new Error("Not a number!");
  console.log(`Square: ${num * num}`);
} catch (error) {
  console.error(`Error: ${error.message}`);
}
```

### **Key Concepts**
- Use `try` and `catch` to handle errors gracefully.
- `throw` creates custom errors.

---

## **10. Advanced Topics**

### **Array Methods**
```javascript
let numbers = [1, 2, 3, 4, 5];

// Map: Transform each item
let squares = numbers.map((n) => n * n);

// Filter: Keep items that match criteria
let evens = numbers.filter((n) => n % 2 === 0);

// Reduce: Accumulate values
let sum = numbers.reduce((acc, n) => acc + n, 0);

console.log(squares, evens, sum);
```

### **Closures**
```javascript
function counter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

const increment = counter();
console.log(increment());  // 1
console.log(increment());  // 2
```

---

## **11. Destructuring and Rest/Spread Operators**

### **Code Example: Destructuring**
```javascript
// Array destructuring
const [a, b, c] = [1, 2, 3];
console.log(a, b, c); // Output: 1 2 3

// Object destructuring
const user = { name: "Alice", age: 25, city: "New York" };
const { name, city } = user;
console.log(name, city); // Output: Alice New York
```

### **Code Example: Rest and Spread**
```javascript
// Rest operator
const [x, ...rest] = [1, 2, 3, 4];
console.log(rest); // Output: [2, 3, 4]

// Spread operator
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];
console.log(arr2); // Output: [1, 2, 3, 4]
```

### **Key Concepts**
- **Destructuring**: Simplifies extracting values from arrays or objects.
- **Spread (`...`)**: Expands arrays/objects into individual elements.
- **Rest (`...`)**: Groups remaining elements into a new array.

---

## **12. Event Delegation**

### **Code Example: Efficient Event Handling**
```javascript
document.querySelector("#parent").addEventListener("click", (e) => {
  if (e.target && e.target.matches("button.classname")) {
    console.log("Button clicked:", e.target.textContent);
  }
});
```

### **Key Concepts**
- Attach a single event listener to a parent element.
- Detect child element actions using `e.target`.

---

## **13. JavaScript Modules (ES6)**

### **Code Example: Export and Import**
**file: math.js**
```javascript
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

**file: app.js**
```javascript
import { add, subtract } from "./math.js";
console.log(add(5, 3)); // Output: 8
```

### **Key Concepts**
- Use `export` to share variables, functions, or classes.
- Use `import` to bring them into other files.
- Ensures modular, reusable code.

---

## **14. Regular Expressions**

### **Code Example: Matching Patterns**
```javascript
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
const isValid = emailRegex.test("example@test.com");
console.log(isValid); // Output: true
```

### **Key Concepts**
- Use `RegExp` for text matching and manipulation.
- Methods:
  - `test()`: Checks if a pattern exists.
  - `match()`: Extracts matching strings.

---

## **15. Web Storage**

### **Code Example: LocalStorage**
```javascript
// Store data
localStorage.setItem("username", "Alice");

// Retrieve data
console.log(localStorage.getItem("username")); // Output: Alice

// Remove data
localStorage.removeItem("username");
```

### **Key Concepts**
- **localStorage**: Persistent storage.
- **sessionStorage**: Data cleared when the browser tab is closed.

---

## **16. Fetch API**

### **Code Example: Making API Requests**
```javascript
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

### **Key Concepts**
- Use `fetch()` for making HTTP requests.
- Use `.json()` to parse JSON responses.

---

## **17. Higher-Order Functions**

### **Code Example: Passing Functions**
```javascript
const multiply = (n) => n * 2;

const processNumbers = (arr, fn) => arr.map(fn);
console.log(processNumbers([1, 2, 3], multiply)); // Output: [2, 4, 6]
```

### **Key Concepts**
- Functions that take other functions as arguments or return them are higher-order functions.

---

## **18. Closures**

### **Code Example: Remembering State**
```javascript
function counter() {
  let count = 0;
  return () => ++count;
}

const increment = counter();
console.log(increment()); // Output: 1
console.log(increment()); // Output: 2
```

### **Key Concepts**
- A closure allows a function to remember variables from its scope even after it’s returned.

---

## **19. The Event Loop**

### **Code Example: Understanding Asynchronous Behavior**
```javascript
console.log("Start");

setTimeout(() => console.log("Timeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");
```

### **Output Explanation**
- Logs: Start → End → Promise → Timeout
- **Key Concepts**:
  - The event loop prioritizes synchronous code, followed by microtasks (e.g., Promises), then macrotasks (e.g., setTimeout).

---

## **20. Error Handling and Debugging**

### **Code Example: Custom Error**
```javascript
try {
  throw new Error("Something went wrong!");
} catch (error) {
  console.error(error.message); // Output: Something went wrong!
} finally {
  console.log("Cleanup code runs here.");
}
```

### **Key Concepts**
- Use `try`, `catch`, and `finally` to handle errors.
- Debug using browser developer tools (`F12`).

---

## **21. Map and Set**

### **Code Example: Map**
```javascript
const map = new Map();
map.set("key1", "value1");
map.set("key2", "value2");

console.log(map.get("key1")); // Output: value1
```

### **Code Example: Set**
```javascript
const set = new Set();
set.add(1);
set.add(2);
set.add(2); // Duplicate ignored

console.log(set.has(2)); // Output: true
```

### **Key Concepts**
- **Map**: Key-value pairs, similar to objects but with additional features.
- **Set**: Unique values, great for filtering duplicates.

---

## **22. Advanced Array Methods**

### **Code Example: Chaining Methods**
```javascript
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter((n) => n % 2 === 0)
  .map((n) => n * n)
  .reduce((sum, n) => sum + n, 0);

console.log(result); // Output: 20
```

### **Key Concepts**
- Combine methods like `filter()`, `map()`, and `reduce()` for powerful operations.

---

## **23. JSON (JavaScript Object Notation)**

### **Code Example: Parse and Stringify**
```javascript
const jsonString = '{"name": "Alice", "age": 25}';

// Parse JSON
const user = JSON.parse(jsonString);
console.log(user.name); // Output: Alice

// Stringify JSON
const newJson = JSON.stringify(user);
console.log(newJson);
```

---

## **24. JavaScript Best Practices**
1. **Use Strict Mode**:
   ```javascript
   "use strict";
   let x = 10; // Safer coding
   ```
2. **Avoid Global Variables**.
3. **Use `const` and `let`** instead of `var`.

---

### **Resources**
1. [JavaScript MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
2. [JavaScript.info](https://javascript.info/)
3. [Eloquent JavaScript](https://eloquentjavascript.net/)
