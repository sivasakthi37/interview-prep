# Technical Interview Preparation Guide

## Table of Contents
1. [HTML](#html)
2. [SCSS](#scss)
3. [JavaScript](#javascript)
4. [React](#react)
5. [Node.js](#nodejs)
6. [Data Structures & Algorithms](#dsa)
7. [System Design](#system-design)
8. [MongoDB](#mongodb)
9. [Next.js](#nextjs)

## HTML

### 1. What are semantic and non-semantic tags?
**Answer:**  
Semantic tags clearly describe their meaning and purpose in the HTML document, while non-semantic tags don't tell anything about their content.

**Semantic Tags Examples:**
- `<header>`: Defines a header section
- `<nav>`: Navigation menu
- `<article>`: Independent, self-contained content
- `<section>`: Thematic grouping of content
- `<footer>`: Footer section.

**Non-semantic Tags Examples:**
- `<div>`: Generic container
- `<span>`: Generic inline container

### 2. Difference between div and span
**Answer:**  
- `<div>` is a block-level element that starts on a new line and takes up the full width available
- `<span>` is an inline element that only takes up as much width as necessary.

**Example:**
```html
<div style="background-color: yellow;">
    This is a block element
</div>
<span style="background-color: lightblue;">
    This is an inline element
</span>
```

### 3. Use of meta tags
**Answer:**  
Meta tags provide metadata about the HTML document. They are used for:
- Character encoding
- SEO (Search Engine Optimization)
- Viewport settings
- Description of the webpage

**Example:**
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="This is a sample webpage">
    <meta name="keywords" content="HTML, CSS, JavaScript">
</head>
```

## SCSS

### 1. Why SCSS?
**Answer:**  
SCSS (Sass) extends CSS with additional features that make it more powerful and maintainable:
- Variables
- Nesting
- Mixins
- Functions
- Inheritance

### 2. Advantages of SCSS
**Answer:**  
- Allows use of variables for consistent values
- Supports nesting for better code organization
- Enables code reuse through mixins
- Provides mathematical operations
- Better maintainability
- Modular approach to styling

### 3. Uses of Mixins
**Answer:**  
Mixins are reusable blocks of CSS declarations that can include parameters.

**Example:**
```scss
@mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

@mixin button-style($bg-color, $text-color) {
    background-color: $bg-color;
    color: $text-color;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
}

// Usage
.container {
    @include flex-center;
}

.primary-button {
    @include button-style(#007bff, white);
}
```

## JavaScript

### 1. Closure
**Answer:**  
A closure is a function that has access to variables in its outer (enclosing) lexical scope, even after the outer function has returned.

**Example:**
```javascript
function createCounter() {
    let count = 0;
    return {
        increment: () => ++count,
        getCount: () => count
    };
}

const counter = createCounter();
console.log(counter.getCount()); // 0
console.log(counter.increment()); // 1
```

### 2. Hoisting
**Answer:**  
Hoisting is JavaScript's default behavior of moving declarations to the top of their scope during compilation.

**Example:**
```javascript
console.log(x); // undefined
var x = 5;

// The above code is interpreted as:
var x;
console.log(x);
x = 5;

// Note: let and const are not hoisted
console.log(y); // ReferenceError
let y = 5;
```

### 3. Call, Apply, and Bind
**Answer:**  
Methods to control the `this` value in function execution:
- `call()`: Calls function with given this value and arguments provided individually
- `apply()`: Calls function with given this value and arguments provided as an array
- `bind()`: Creates a new function with fixed this value

**Example:**
```javascript
const person = {
    name: 'John',
    greet: function(greeting) {
        return `${greeting}, ${this.name}!`;
    }
};

const anotherPerson = { name: 'Jane' };

// Call
console.log(person.greet.call(anotherPerson, 'Hello')); // "Hello, Jane!"

// Apply
console.log(person.greet.apply(anotherPerson, ['Hi'])); // "Hi, Jane!"

// Bind
const greetJane = person.greet.bind(anotherPerson);
console.log(greetJane('Hey')); // "Hey, Jane!"
```

### 4. Currying
**Answer:**  
Currying is the process of converting a function that takes multiple arguments into a series of functions that take one argument each.

**Example:**
```javascript
// Normal function
function add(a, b, c) {
    return a + b + c;
}

// Curried version
const curriedAdd = a => b => c => a + b + c;

console.log(curriedAdd(1)(2)(3)); // 6
```

### 5. ES6 Features
**Answer:**  
Key ES6 (ECMAScript 2015) features include:
- Arrow functions
- Template literals
- Destructuring
- Spread/Rest operators
- Classes
- Modules
- Promises
- let/const declarations

**Example:**
```javascript
// Arrow functions
const add = (a, b) => a + b;

// Template literals
const name = 'John';
console.log(`Hello ${name}!`);

// Destructuring
const { firstName, lastName } = person;
const [first, second] = array;

// Spread operator
const newArray = [...oldArray, newItem];
```

### 6. Spread Operator vs Rest Parameter
**Answer:**  
- Spread operator (...) expands elements
- Rest parameter (...) collects elements into an array

**Example:**
```javascript
// Spread operator
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4, 5]; // [1, 2, 3, 4, 5]

// Rest parameter
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}
console.log(sum(1, 2, 3, 4)); // 10
```

### 7. Higher Order Functions
**Answer:**  
Functions that take other functions as arguments or return functions.

**Example:**
```javascript
const numbers = [1, 2, 3, 4, 5];

// map, filter, reduce are higher-order functions
const doubled = numbers.map(num => num * 2);
const evens = numbers.filter(num => num % 2 === 0);
const sum = numbers.reduce((acc, curr) => acc + curr, 0);
```

### 8. Self-Invoking Function (IIFE)
**Answer:**  
Immediately Invoked Function Expression - functions that run as soon as they are defined.

**Example:**
```javascript
(function() {
    console.log('This runs immediately');
})();

// Modern version using arrow function
(() => {
    console.log('This also runs immediately');
})();
```

### 9. This Keyword
**Answer:**  
The value of `this` depends on how and where the function is called:
- In a method, `this` refers to the owner object
- Alone, `this` refers to the global object
- In a function, `this` refers to the global object
- In an event, `this` refers to the element that received the event

**Example:**
```javascript
const person = {
    name: 'John',
    sayHi() {
        console.log(`Hi, I'm ${this.name}`);
    }
};

person.sayHi(); // "Hi, I'm John"
```

### 10. Recursion
**Answer:**  
A function that calls itself until it reaches a base case.

**Example:**
```javascript
function factorial(n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}

console.log(factorial(5)); // 120
```

### 11. Event Loop
**Answer:**  
The event loop continuously checks the call stack and callback queue, pushing callbacks to the stack when it's empty.

**Example:**
```javascript
console.log('Start');

setTimeout(() => {
    console.log('Timeout');
}, 0);

Promise.resolve().then(() => {
    console.log('Promise');
});

console.log('End');

// Output:
// Start
// End
// Promise
// Timeout
```

### 12. Async/Await
**Answer:**  
Async/await is syntactic sugar for promises, making asynchronous code look synchronous.

**Example:**
```javascript
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error:', error);
    }
}
```

### 13. Promises
**Answer:**  
Promises represent the eventual completion (or failure) of an asynchronous operation.

**Example:**
```javascript
const promise = new Promise((resolve, reject) => {
    const success = true;
    if (success) {
        resolve('Operation successful');
    } else {
        reject('Operation failed');
    }
});

promise
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

### 14. Promise.all
**Answer:**  
`Promise.all` takes an array of promises and returns a single promise that resolves when all promises have resolved.

**Example:**
```javascript
const promise1 = Promise.resolve(1);
const promise2 = Promise.resolve(2);
const promise3 = Promise.resolve(3);

Promise.all([promise1, promise2, promise3])
    .then(values => console.log(values)) // [1, 2, 3]
    .catch(error => console.error(error));
```

### 15. Promise Status
**Answer:**  
A Promise can be in one of three states:
- Pending: Initial state
- Fulfilled: Operation completed successfully
- Rejected: Operation failed

### 16. let, var, const Differences
**Answer:**  
- `var`: Function-scoped, can be redeclared, hoisted
- `let`: Block-scoped, cannot be redeclared, not hoisted
- `const`: Block-scoped, cannot be reassigned, not hoisted

**Example:**
```javascript
var x = 1;
var x = 2; // OK

let y = 1;
// let y = 2; // Error: already declared

const z = 1;
// z = 2; // Error: cannot reassign

if (true) {
    let blockScoped = 'only available in this block';
    var functionScoped = 'available outside block';
}
```

## React

### 1. What is State?
**Answer:**  
State is a built-in React object that contains data or information about the component. When state changes, the component re-renders.

**Example:**
```javascript
import React, { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}
```

### 2. React Virtual DOM vs Real DOM
**Answer:**  
- Real DOM: The actual HTML DOM that is directly rendered in the browser
- Virtual DOM: A lightweight copy of the Real DOM kept in memory by React

React uses Virtual DOM to optimize performance by:
1. Creating a virtual copy of the UI
2. Comparing changes between virtual and real DOM (diffing)
3. Only updating the real DOM where necessary

### 3. What is React?
**Answer:**  
React is a JavaScript library for building user interfaces, developed by Facebook. Key features:
- Component-based architecture
- Virtual DOM for performance
- Unidirectional data flow
- JSX syntax
- Rich ecosystem

### 4. How useEffect Works
**Answer:**  
useEffect is a Hook that handles side effects in functional components. It runs after every render unless specified otherwise.

**Example:**
```javascript
import React, { useState, useEffect } from 'react';

function ExampleComponent() {
    const [data, setData] = useState(null);

    // Runs on every render
    useEffect(() => {
        console.log('Component rendered');
    });

    // Runs only on mount (empty dependency array)
    useEffect(() => {
        fetchData();
    }, []);

    // Runs when count changes
    useEffect(() => {
        document.title = `Count: ${count}`;
    }, [count]);

    // Cleanup (componentWillUnmount equivalent)
    useEffect(() => {
        return () => {
            console.log('Component will unmount');
        };
    }, []);
}
```

### 5. React Component Lifecycle
**Answer:**  
React components go through three main phases:
1. Mounting (Birth)
2. Updating (Growth)
3. Unmounting (Death)

**Class Component Lifecycle:**
```javascript
class Example extends React.Component {
    // Mounting
    constructor(props) {
        super(props);
    }
    
    componentDidMount() {
        // After component is mounted
    }

    // Updating
    componentDidUpdate(prevProps, prevState) {
        // After component updates
    }

    // Unmounting
    componentWillUnmount() {
        // Before component is removed
    }
}
```

**Functional Component Equivalent:**
```javascript
function Example() {
    useEffect(() => {
        // componentDidMount
        return () => {
            // componentWillUnmount
        };
    }, []);

    useEffect(() => {
        // componentDidUpdate
    }, [dependencies]);
}
```

### 6. Functional vs Class Components
**Answer:**  
Key differences:

**Functional Components:**
- Simpler syntax
- Use Hooks for state and lifecycle
- Easier to test and debug
- Better performance in most cases
- No 'this' keyword

**Class Components:**
- Use ES6 class syntax
- Have lifecycle methods
- Use 'this' keyword
- Can have local state
- More verbose

### 7. How Props Work
**Answer:**  
Props (properties) are read-only components that are passed from parent to child components.

**Example:**
```javascript
// Parent Component
function Parent() {
    return <Child name="John" age={25} />;
}

// Child Component
function Child(props) {
    return (
        <div>
            <p>Name: {props.name}</p>
            <p>Age: {props.age}</p>
        </div>
    );
}

// Using destructuring
function Child({ name, age }) {
    return (
        <div>
            <p>Name: {name}</p>
            <p>Age: {age}</p>
        </div>
    );
}
```

### 8. Controlled vs Uncontrolled Components
**Answer:**  
**Controlled Components:**
- Form data is controlled by React
- Current value is passed as a prop
- Changes are handled through callbacks

**Uncontrolled Components:**
- Form data is handled by the DOM itself
- Use ref to get form values
- More similar to traditional HTML

**Example:**
```javascript
// Controlled Component
function ControlledForm() {
    const [value, setValue] = useState('');

    return (
        <input
            value={value}
            onChange={(e) => setValue(e.target.value)}
        />
    );
}

// Uncontrolled Component
function UncontrolledForm() {
    const inputRef = useRef();

    const handleSubmit = () => {
        console.log(inputRef.current.value);
    };

    return <input ref={inputRef} />;
}
```

### 9. Custom Hooks
**Answer:**  
Custom Hooks are JavaScript functions that start with 'use' and can call other Hooks. They allow you to extract component logic into reusable functions.

**Example:**
```javascript
// Custom Hook
function useWindowSize() {
    const [size, setSize] = useState({
        width: window.innerWidth,
        height: window.innerHeight
    });

    useEffect(() => {
        const handleResize = () => {
            setSize({
                width: window.innerWidth,
                height: window.innerHeight
            });
        };

        window.addEventListener('resize', handleResize);
        return () => window.removeEventListener('resize', handleResize);
    }, []);

    return size;
}

// Using the Custom Hook
function Component() {
    const { width, height } = useWindowSize();
    return (
        <div>
            Window size: {width} x {height}
        </div>
    );
}
```

### 10. Prop Drilling
**Answer:**  
Prop drilling occurs when props need to be passed through multiple levels of components that don't need the data themselves.

**Solution Approaches:**
1. Context API
2. Redux
3. Component composition

**Example:**
```javascript
// Prop Drilling Problem
function GrandParent() {
    const [user, setUser] = useState({ name: 'John' });
    return <Parent user={user} />;
}

function Parent({ user }) {
    return <Child user={user} />;
}

function Child({ user }) {
    return <GrandChild user={user} />;
}

// Solution using Context
const UserContext = React.createContext();

function GrandParent() {
    const [user, setUser] = useState({ name: 'John' });
    return (
        <UserContext.Provider value={user}>
            <Parent />
        </UserContext.Provider>
    );
}

function GrandChild() {
    const user = useContext(UserContext);
    return <div>{user.name}</div>;
}
```

### React Reconciliation Process
**Answer:**  
React's reconciliation is the process of updating the DOM to match the most recent render of a React component. Here's how it works:

1. **Virtual DOM:**
   - React maintains a virtual representation of the UI (Virtual DOM)
   - When state or props change, React creates a new Virtual DOM tree

2. **Diffing Algorithm:**
   - React compares the new Virtual DOM with the previous one
   - Uses a diffing algorithm to identify what has changed
   - This process is called reconciliation

3. **Key Concepts:**
   - React uses a "diffing" algorithm that runs in O(n) time
   - Components of the same type will generate similar trees
   - Different component types will generate different trees
   - Keys help React identify which items have changed, been added, or removed

4. **Optimization Techniques:**
   - Use `React.memo()` for component memoization
   - Implement `shouldComponentUpdate` lifecycle method
   - Use stable keys for list items
   - Avoid inline object creation in renders

**Example:**
```jsx
// Using React.memo for optimization
const MyComponent = React.memo(function MyComponent(props) {
  return <div>{props.value}</div>;
});

// Using keys in lists
function List({ items }) {
  return (
    <ul>
      {items.map(item => (
        <li key={item.id}>{item.text}</li>
      ))}
    </ul>
  );
}
```

## Node.js

### 1. Is Node.js Synchronous or Asynchronous?
**Answer:**  
Node.js is single-threaded and uses an event-driven, non-blocking I/O model, making it asynchronous by default. However, it also provides synchronous versions of most methods.

**Example:**
```javascript
// Asynchronous
fs.readFile('file.txt', (err, data) => {
    if (err) throw err;
    console.log(data);
});
console.log('This runs first');

// Synchronous
const data = fs.readFileSync('file.txt');
console.log(data);
console.log('This runs second');
```

### 2. Async/Await in Node.js
**Answer:**  
Async/await is a way to handle promises more cleanly, making asynchronous code look and behave more like synchronous code.

**Example:**
```javascript
// Without async/await
function getData() {
    return fetch('https://api.example.com/data')
        .then(response => response.json())
        .then(data => console.log(data))
        .catch(error => console.error(error));
}

// With async/await
async function getData() {
    try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}
```

### 3. Event Loop in Node.js
**Answer:**  
The event loop allows Node.js to perform non-blocking I/O operations despite JavaScript being single-threaded.

**Phases:**
1. Timers (setTimeout, setInterval)
2. Pending callbacks
3. Idle, prepare
4. Poll
5. Check (setImmediate)
6. Close callbacks

**Example:**
```javascript
console.log('1');

setTimeout(() => {
    console.log('2');
}, 0);

setImmediate(() => {
    console.log('3');
});

process.nextTick(() => {
    console.log('4');
});

console.log('5');

// Output:
// 1
// 5
// 4
// 2 or 3
// 3 or 2
```

### 4. Callback Hell
**Answer:**  
Callback hell occurs when multiple asynchronous operations are nested within callbacks, making code hard to read and maintain.

**Example:**
```javascript
// Callback Hell
getData(function(a) {
    getMoreData(a, function(b) {
        getMoreData(b, function(c) {
            getMoreData(c, function(d) {
                getMoreData(d, function(e) {
                    console.log(e);
                });
            });
        });
    });
});

// Solution using Promises
getData()
    .then(a => getMoreData(a))
    .then(b => getMoreData(b))
    .then(c => getMoreData(c))
    .then(d => getMoreData(d))
    .then(e => console.log(e))
    .catch(error => console.error(error));

// Solution using async/await
async function getAllData() {
    try {
        const a = await getData();
        const b = await getMoreData(a);
        const c = await getMoreData(b);
        const d = await getMoreData(c);
        const e = await getMoreData(d);
        console.log(e);
    } catch (error) {
        console.error(error);
    }
}
```

### 5. Event Emitter in Node.js
**Answer:**  
EventEmitter is a class that handles events in Node.js. It's the base for many Node.js classes.

**Example:**
```javascript
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();

// Register event listener
myEmitter.on('event', (data) => {
    console.log('Event occurred:', data);
});

// Emit event
myEmitter.emit('event', 'Hello World');
```

### 6. Promises and Promise.all
**Answer:**  
Promises handle asynchronous operations. Promise.all executes multiple promises concurrently.

**Example:**
```javascript
// Basic Promise
const promise = new Promise((resolve, reject) => {
    // Async operation
    if (success) {
        resolve('Success');
    } else {
        reject('Error');
    }
});

// Promise.all
const promise1 = fetch('/api/data1');
const promise2 = fetch('/api/data2');
const promise3 = fetch('/api/data3');

Promise.all([promise1, promise2, promise3])
    .then(([result1, result2, result3]) => {
        console.log(result1, result2, result3);
    })
    .catch(error => console.error(error));

// Promise.race
Promise.race([promise1, promise2, promise3])
    .then(result => console.log('First to complete:', result))
    .catch(error => console.error(error));
```

## Data Structures & Algorithms

### 1. Implement Binary Search
**Answer:**  
Binary Search is an efficient algorithm for searching a sorted array by repeatedly dividing the search interval in half.

**Example:**
```javascript
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            return mid;
        }
        
        if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;
}

// Example usage:
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
console.log(binarySearch(arr, 5)); // Output: 4
```

## System Design

### 1. How would you design a URL shortening service?
**Answer:**  
A URL shortening service needs to handle:
1. URL shortening
2. URL redirection
3. High availability
4. Data persistence

**Key Components:**
- Hash function for generating short URLs
- Database to store URL mappings
- Load balancer for distribution
- Caching layer for frequent URLs

**Basic Implementation Example:**
```javascript
class URLShortener {
    constructor() {
        this.urlDatabase = new Map();
        this.baseUrl = 'http://short.url/';
    }

    generateHash(url) {
        // Simple hash function (in production, use more robust method)
        return Math.random().toString(36).substring(2, 8);
    }

    shorten(originalUrl) {
        const hash = this.generateHash(originalUrl);
        this.urlDatabase.set(hash, originalUrl);
        return this.baseUrl + hash;
    }

    getOriginalUrl(hash) {
        return this.urlDatabase.get(hash);
    }
}
```

## MongoDB

### 1. Difference between MongoDB and PostgreSQL
**Answer:**  
Key differences:
- **Data Model**:
  - MongoDB: Document-oriented (BSON documents)
  - PostgreSQL: Relational (tables with rows and columns)

- **Schema**:
  - MongoDB: Flexible, schema-less
  - PostgreSQL: Rigid, predefined schema

- **Scaling**:
  - MongoDB: Horizontal scaling (sharding)
  - PostgreSQL: Vertical scaling primarily

- **Query Language**:
  - MongoDB: JSON-like queries
  - PostgreSQL: SQL

- **ACID Compliance**:
  - MongoDB: Partial (since v4.0)
  - PostgreSQL: Full ACID compliance

### 2. Basic Queries in MongoDB
**Answer:**  
Common MongoDB operations:

```javascript
// Find documents
db.collection.find({ age: { $gt: 25 } })

// Insert document
db.collection.insertOne({ name: "John", age: 30 })

// Update document
db.collection.updateOne(
    { name: "John" },
    { $set: { age: 31 } }
)

// Delete document
db.collection.deleteOne({ name: "John" })

// Count documents
db.collection.countDocuments({ age: { $gt: 25 } })

// Sort documents
db.collection.find().sort({ age: 1 }) // 1 for ascending, -1 for descending

// Limit results
db.collection.find().limit(5)
```

### 3. Collections in MongoDB
**Answer:**  
A collection is a group of MongoDB documents. It's the equivalent of a table in relational databases. Collections have the following characteristics:
- Schema-less (documents within a collection can have different fields)
- Documents in a collection are usually related
- Collections are created automatically when first document is inserted

```javascript
// Create collection
db.createCollection("users")

// List collections
db.getCollectionNames()

// Drop collection
db.users.drop()
```

### 4. Inserting Documents
**Answer:**  
Multiple ways to insert documents:

```javascript
// Insert one document
db.users.insertOne({
    name: "John Doe",
    age: 30,
    email: "john@example.com"
})

// Insert multiple documents
db.users.insertMany([
    { name: "Jane Doe", age: 25 },
    { name: "Bob Smith", age: 35 }
])

// Insert with nested documents
db.users.insertOne({
    name: "John",
    address: {
        street: "123 Main St",
        city: "New York",
        country: "USA"
    }
})
```

### 5. findOne() vs find()
**Answer:**  
- `findOne()`: Returns a single document that matches the query
- `find()`: Returns a cursor to all documents that match the query

```javascript
// findOne() returns single document
const user = db.users.findOne({ name: "John" })

// find() returns cursor to all matching documents
const users = db.users.find({ age: { $gt: 25 } })

// find() with multiple conditions
db.users.find({
    age: { $gt: 25 },
    city: "New York"
})
```

### 6. Aggregation in MongoDB
**Answer:**  
Aggregation is a way of processing data records and returning computed results. It collects values from various documents and groups them together.

```javascript
// Basic aggregation pipeline
db.orders.aggregate([
    // Stage 1: Match documents
    { $match: { status: "completed" } },
    
    // Stage 2: Group documents
    { $group: {
        _id: "$customer",
        totalAmount: { $sum: "$amount" },
        count: { $sum: 1 }
    }},
    
    // Stage 3: Sort results
    { $sort: { totalAmount: -1 } }
])

// Complex aggregation example
db.sales.aggregate([
    { $match: { date: { $gte: new Date("2024-01-01") } } },
    { $group: {
        _id: { month: { $month: "$date" } },
        total: { $sum: "$amount" },
        avgPrice: { $avg: "$amount" }
    }},
    { $sort: { "_id.month": 1 } }
])
```

### 7. $lookup Aggregation
**Answer:**  
`$lookup` performs a left outer join to another collection in the same database. It's used to combine documents from multiple collections.

```javascript
// Example of $lookup
db.orders.aggregate([
    {
        $lookup: {
            from: "customers",         // Collection to join
            localField: "customerId",  // Field from orders
            foreignField: "_id",       // Field from customers
            as: "customerInfo"         // Output array field
        }
    }
])

// Complex $lookup example
db.orders.aggregate([
    {
        $lookup: {
            from: "products",
            let: { order_item: "$item" },
            pipeline: [
                {
                    $match: {
                        $expr: { $eq: ["$name", "$$order_item"] }
                    }
                }
            ],
            as: "product_details"
        }
    }
])
```

### 8. Updating Documents
**Answer:**  
Multiple ways to update documents:

```javascript
// Update one document
db.users.updateOne(
    { name: "John" },
    { $set: { age: 31 } }
)

// Update multiple documents
db.users.updateMany(
    { age: { $lt: 18 } },
    { $set: { status: "minor" } }
)

// Upsert (insert if not exists)
db.users.updateOne(
    { email: "john@example.com" },
    { $set: { name: "John", age: 30 } },
    { upsert: true }
)
```

### 9. $set Operator
**Answer:**  
`$set` operator replaces the value of a field with a specified value. It can:
- Modify existing fields
- Add new fields
- Update nested fields

```javascript
// Basic $set
db.users.updateOne(
    { _id: 1 },
    { $set: { status: "active" } }
)

// Multiple field update
db.users.updateOne(
    { _id: 1 },
    {
        $set: {
            age: 31,
            status: "active",
            lastModified: new Date()
        }
    }
)

// Nested field update
db.users.updateOne(
    { _id: 1 },
    {
        $set: {
            "address.city": "New York",
            "address.country": "USA"
        }
    }
)
```

### 10. Deleting Documents
**Answer:**  
Methods to delete documents:

```javascript
// Delete one document
db.users.deleteOne({ name: "John" })

// Delete multiple documents
db.users.deleteMany({ age: { $lt: 18 } })

// Delete all documents
db.users.deleteMany({})

// Remove collection
db.users.drop()
```

### 11. updateOne() vs updateMany()
**Answer:**  
- `updateOne()`: Updates the first document that matches the filter
- `updateMany()`: Updates all documents that match the filter

```javascript
// updateOne example
db.users.updateOne(
    { age: { $gt: 25 } },
    { $set: { status: "adult" } }
) // Updates only first matching document

// updateMany example
db.users.updateMany(
    { age: { $gt: 25 } },
    { $set: { status: "adult" } }
) // Updates all matching documents
```

## Next.js

### 1. SSR vs SSG vs CSR
**Answer:**  
Different rendering strategies in Next.js:

**Server-Side Rendering (SSR)**:
- Pages are rendered on each request
- Best for dynamic data
- Uses `getServerSideProps`

```javascript
// SSR Example
export async function getServerSideProps(context) {
    const res = await fetch('https://api.example.com/data')
    const data = await res.json()
    
    return {
        props: { data }
    }
}
```

**Static Site Generation (SSG)**:
- Pages are pre-rendered at build time
- Best for static content
- Uses `getStaticProps`

```javascript
// SSG Example
export async function getStaticProps() {
    const res = await fetch('https://api.example.com/static-data')
    const data = await res.json()
    
    return {
        props: { data },
        revalidate: 60 // Optional: ISR
    }
}
```

**Client-Side Rendering (CSR)**:
- Pages are rendered in the browser
- Best for private, user-specific content
- Uses React hooks like `useEffect`

```javascript
// CSR Example
import { useEffect, useState } from 'react'

function Page() {
    const [data, setData] = useState(null)
    
    useEffect(() => {
        fetch('https://api.example.com/data')
            .then(res => res.json())
            .then(data => setData(data))
    }, [])
    
    if (!data) return 'Loading...'
    return <div>{data.title}</div>
}
```

### 2. Dynamic Routing
**Answer:**  
Next.js supports dynamic routes using brackets `[]` in the file name.

```javascript
// pages/posts/[id].js
export async function getStaticPaths() {
    return {
        paths: [
            { params: { id: '1' } },
            { params: { id: '2' } }
        ],
        fallback: false
    }
}

export async function getStaticProps({ params }) {
    const res = await fetch(`https://api.example.com/posts/${params.id}`)
    const post = await res.json()
    
    return {
        props: { post }
    }
}

// Catch-all routes [...slug].js
export async function getStaticPaths() {
    return {
        paths: [
            { params: { slug: ['a', 'b'] } }
        ],
        fallback: false
    }
}
```

### 3. getServerSideProps vs getStaticProps
**Answer:**  
Key differences:

**getServerSideProps**:
- Runs on every request
- Always up-to-date data
- Slower performance
- Best for dynamic content

```javascript
// getServerSideProps
export async function getServerSideProps(context) {
    const res = await fetch(`https://api.example.com/data`)
    const data = await res.json()
    
    return {
        props: { data }
    }
}
```

**getStaticProps**:
- Runs at build time
- Better performance
- May have stale data
- Best for static content

```javascript
// getStaticProps
export async function getStaticProps() {
    const res = await fetch('https://api.example.com/data')
    const data = await res.json()
    
    return {
        props: { data },
        revalidate: 60 // Optional ISR
    }
}
```

### 4. Revalidate and ISR
**Answer:**  
Incremental Static Regeneration (ISR) allows you to update static pages after you've built your site.

```javascript
// Basic ISR implementation
export async function getStaticProps() {
    const res = await fetch('https://api.example.com/data')
    const data = await res.json()
    
    return {
        props: { data },
        revalidate: 60 // Regenerate page every 60 seconds
    }
}

// On-demand revalidation (Next.js 12+)
// pages/api/revalidate.js
export default async function handler(req, res) {
    try {
        await res.revalidate('/path-to-revalidate')
        return res.json({ revalidated: true })
    } catch (err) {
        return res.status(500).send('Error revalidating')
    }
}
```

Key features of revalidation:
1. Pages are statically generated at build time
2. Specified time interval for revalidation
3. Background regeneration
4. No downtime during regeneration
