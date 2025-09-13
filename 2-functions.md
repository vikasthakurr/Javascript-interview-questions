# 02. JavaScript Functions – 50 Interview Questions with Detailed Explanations

---

## 1. What is a function in JavaScript?
**Theory:**
A function is a reusable block of code designed to perform a specific task. Functions allow programmers to break down complex problems into smaller, manageable pieces. They can accept inputs, perform computations, and return outputs. Functions also promote modularity, code reusability, and maintainability. Functions are foundational in JavaScript and are used in both procedural and functional programming paradigms.

**Code:**
```js
function greet(name) {
  return `Hello, ${name}`;
}
console.log(greet("Vikas"));
```

---

## 2. Difference between Function Declaration and Function Expression
**Theory:**
Function declarations are hoisted to the top of their scope, which means they can be invoked before their definition in the code. Function expressions are stored in variables and are not hoisted; they can only be invoked after they are assigned. This difference impacts the order in which functions can be used and helps developers manage code execution and scope effectively.

**Code:**
```js
// Function Declaration
function add(a, b) {
  return a + b;
}
console.log(add(2, 3)); // 5

// Function Expression
const multiply = function(a, b) {
  return a * b;
}
console.log(multiply(2, 3)); // 6
```

---

## 3. Arrow Functions
**Theory:**
Arrow functions provide a concise syntax for writing functions and lexically bind the `this` keyword. Unlike traditional functions, they do not have their own `this`, `arguments`, or `super`, making them suitable for use in scenarios where the context of `this` should remain consistent. They are commonly used for callbacks, array methods, and functional programming.

**Code:**
```js
const square = x => x * x;
console.log(square(5)); // 25
```

---

## 4. Parameters vs Arguments
**Theory:**
Parameters are the variables defined in the function declaration and act as placeholders for the data the function will process. Arguments are the actual values passed into the function when it is invoked. Understanding this distinction is critical for writing flexible and reusable functions that can handle different input values dynamically.

**Code:**
```js
function greet(name) { // name is parameter
  console.log(`Hello ${name}`);
}
greet("Vikas"); // Vikas is argument
```

---

## 5. Default Parameters
**Theory:**
Default parameters allow functions to initialize parameters with default values if no argument or `undefined` is passed. This reduces the need for conditional checks inside functions and ensures that functions behave consistently even when some inputs are missing.

**Code:**
```js
function greet(name = "Guest") {
  console.log(`Hello, ${name}`);
}
greet(); // Hello, Guest
```

---

## 6. Rest Parameters
**Theory:**
Rest parameters allow functions to accept an indefinite number of arguments as an array. This feature is helpful for functions that need to handle variable numbers of inputs, such as summing numbers or processing dynamic data sets. It simplifies code and enhances flexibility.

**Code:**
```js
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3, 4)); // 10
```

---

## 7. Function Scope vs Block Scope
**Theory:**
Function scope confines variables declared with `var` to the function they are defined in. Block scope, introduced by `let` and `const`, restricts variable visibility to the block (like `if` or `for`) they are declared in. Understanding these scopes is essential to prevent accidental overwrites and to maintain predictable behavior in large codebases.

**Code:**
```js
function test() {
  var x = 1;
  if (true) {
    var x = 2; // modifies outer x
    let y = 3; // block-scoped
  }
  console.log(x); // 2
  // console.log(y); // Error
}
test();
```

---

## 8. IIFE (Immediately Invoked Function Expression)
**Theory:**
An IIFE is a function that is executed immediately after it is defined. It is often used to create a private scope, avoiding polluting the global namespace. Variables and functions inside an IIFE cannot be accessed from outside, providing data encapsulation and preventing conflicts in larger applications.

**Code:**
```js
(function() {
  console.log("IIFE executed");
})();
```

---

## 9. Closures
**Theory:**
A closure is a function that retains access to its outer function’s variables even after the outer function has finished executing. Closures are widely used in JavaScript for data privacy, creating function factories, and maintaining state in asynchronous programming. They are a foundational concept for understanding scope and memory in JS.

**Code:**
```js
function outer() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## 10. Higher-Order Functions
**Theory:**
Higher-order functions are functions that either take other functions as arguments, return functions, or both. They enable abstraction, reusability, and functional programming patterns. Examples include `map`, `filter`, and `reduce`.

**Code:**
```js
function greet(fn) {
  console.log(fn());
}
function hello() {
  return "Hello World";
}
greet(hello);
```

---

## 11. Callback Functions
**Theory:**
A callback function is a function passed to another function as an argument to be executed later. Callbacks are essential for handling asynchronous operations like HTTP requests, timers, and event listeners, enabling non-blocking code execution.

**Code:**
```js
function fetchData(callback) {
  setTimeout(() => {
    callback("Data received");
  }, 1000);
}
fetchData(console.log);
```

---

## 12. Function Currying
**Theory:**
Currying is a functional programming technique where a function with multiple parameters is transformed into a sequence of functions each taking a single parameter. Currying allows partial application of functions and helps create more reusable and composable code.

**Code:**
```js
function multiply(a) {
  return function(b) {
    return a * b;
  };
}
const double = multiply(2);
console.log(double(5)); // 10
```

---

## 13. Function Composition
**Theory:**
Function composition combines multiple functions to produce a new function where the output of one function is the input of the next. It is a key concept in functional programming and promotes modular, reusable code.

**Code:**
```js
const add = x => x + 2;
const multiply = x => x * 3;
const compose = (f, g) => x => f(g(x));
console.log(compose(add, multiply)(5)); // 17
```

---

## 14. Call, Apply, Bind
**Theory:**
These methods allow developers to control the `this` context of functions:
- `call`: Executes the function immediately with the specified `this` and arguments.
- `apply`: Similar to call, but accepts arguments as an array.
- `bind`: Returns a new function with the specified `this`, which can be invoked later.

**Code:**
```js
const person = {name: "Vikas"};
function greet(greeting) {
  console.log(`${greeting}, ${this.name}`);
}
greet.call(person, "Hi");
greet.apply(person, ["Hello"]);
const bound = greet.bind(person);
bound("Hey");

# 02. JavaScript Functions – 50 Interview Questions with Detailed Explanations (Continued)

---

## 15. Anonymous Functions
**Theory:**
Anonymous functions are functions without a name. They are often used as arguments to other functions or as immediately invoked function expressions (IIFE). They are commonly employed in callbacks, event handlers, and asynchronous operations where defining a named function is unnecessary.

**Code:**
```js
setTimeout(function() { console.log("Anonymous function executed"); }, 1000);
```

---

## 16. Named Function Expressions
**Theory:**
Named function expressions are function expressions that include a name. This is useful for recursion and debugging, as the function’s name appears in stack traces, making error tracking easier.

**Code:**
```js
const factorial = function fact(n) {
  return n <= 1 ? 1 : n * fact(n - 1);
}
console.log(factorial(5)); // 120
```

---

## 17. Function Hoisting
**Theory:**
Function declarations are hoisted to the top of their scope, which allows calling them before they are defined in the code. Function expressions are not hoisted, so they can only be called after their definition. Understanding hoisting is crucial for avoiding reference errors and writing predictable code.

**Code:**
```js
console.log(foo()); // Works
function foo() { return "hi"; }

// console.log(bar()); // Error
const bar = function() { return "hi"; };
```

---

## 18. Generator Functions
**Theory:**
Generators are special functions that can pause execution and resume later using the `yield` keyword. They allow for lazy evaluation, memory efficiency, and the creation of iterable sequences. Generators are powerful in scenarios like handling large data streams and asynchronous programming.

**Code:**
```js
function* gen() {
  yield 1;
  yield 2;
}
const g = gen();
console.log(g.next().value); // 1
console.log(g.next().value); // 2
```

---

## 19. Async Functions
**Theory:**
Async functions simplify working with promises and asynchronous code. Using `async` and `await`, asynchronous operations can be written in a synchronous style, improving readability and maintainability. Async functions always return a promise.

**Code:**
```js
async function fetchData() {
  return await Promise.resolve("Data");
}
fetchData().then(console.log); // Data
```

---

## 20. Function Overloading
**Theory:**
JavaScript does not support traditional function overloading like other languages. Developers can simulate overloading by checking the number and type of arguments inside the function, allowing flexibility in function behavior.

**Code:**
```js
function add(a, b) {
  if (b === undefined) return a;
  return a + b;
}
console.log(add(5)); // 5
console.log(add(5, 10)); // 15
```

---

## 21. IIFE with Parameters
**Theory:**
IIFE can accept parameters, allowing immediate computation with given values. This is useful for initializing variables or setting up configurations without polluting the global scope.

**Code:**
```js
(function(a, b) { console.log(a + b); })(2, 3); // 5
```

---

## 22. Closures with Loops
**Theory:**
When creating functions inside loops, closures capture the variable at the time of definition. Using `let` ensures each iteration has its own scope, avoiding common pitfalls with `var`.

**Code:**
```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
```

---

## 23. Pure Functions
**Theory:**
Pure functions always return the same output for the same input and do not cause side effects. They are predictable, easier to test, and crucial for functional programming and concurrency.

**Code:**
```js
function add(a, b) { return a + b; }
console.log(add(2,3)); // 5
```

---

## 24. Impure Functions
**Theory:**
Impure functions may rely on external state or modify variables outside their scope, causing side effects. They are less predictable but sometimes necessary for tasks like logging or interacting with APIs.

**Code:**
```js
let count = 0;
function increment() { count++; return count; }
console.log(increment()); // 1
```

---

## 25. Recursion
**Theory:**
A recursive function calls itself to solve smaller instances of a problem until a base condition is met. Recursion is widely used in algorithms such as factorials, Fibonacci series, and tree traversals.

**Code:**
```js
function factorial(n) { return n <= 1 ? 1 : n * factorial(n - 1); }
console.log(factorial(5)); // 120
```

---

## 26. Function Returning Function
**Theory:**
Functions can return other functions, enabling higher-order operations, partial application, and dynamic function generation.

**Code:**
```js
function greet(msg) { return function(name) { console.log(msg + ' ' + name); }; }
const hello = greet('Hi');
hello('Vikas'); // Hi Vikas
```

---

## 27. Arrow vs Function Expression
**Theory:**
Arrow functions do not have their own `this` context and cannot be used as constructors. Traditional function expressions have their own `this` and can be instantiated. Choosing the right type affects scoping and object behavior.

**Code:**
```js
const obj = {
  name: 'Vikas',
  regular: function() { console.log(this.name); },
  arrow: () => console.log(this.name)
};
obj.regular(); // Vikas
obj.arrow(); // undefined (or global context)
```

---

## 28. Function as Object Method
**Theory:**
Functions can be assigned as object properties, becoming methods. They can access object data using `this` and encapsulate behaviors within objects.

**Code:**
```js
const obj = { greet() { console.log('Hello'); } };
obj.greet(); // Hello
```

---

## 29. Function Length Property
**Theory:**
The `length` property of a function indicates the number of expected parameters, which helps in introspection and dynamic function handling.

**Code:**
```js
function add(a, b, c) {}
console.log(add.length); // 3
```

---

## 30. Function Name Property
**Theory:**
The `name` property provides the identifier of the function, useful for debugging, logging, and introspection in larger applications.

**Code:**
```js
function test() {}
console.log(test.name); // test


## 31. Function toString
**Theory:**
The `toString()` method returns the source code of the function as a string. This can be useful for debugging, logging, or analyzing functions dynamically. While not commonly used in production, it helps in understanding the structure of a function programmatically.

**Code:**
```js
function test(){ return 1; }
console.log(test.toString());
```

---

## 32. Function Binding Example
**Theory:**
`bind()` allows you to create a new function with a specific `this` context. This is useful when you want to ensure that a function always runs with a certain object as its context, for instance in event handling or callbacks.

**Code:**
```js
const obj = {val: 10};
function show(){ console.log(this.val); }
const boundShow = show.bind(obj);
boundShow(); // 10
```

---

## 33. Recursive Sum of Array
**Theory:**
Recursion can be used to calculate the sum of array elements by breaking the problem into smaller subproblems. This technique helps in understanding problem decomposition and functional programming.

**Code:**
```js
function sum(arr){
  if(arr.length === 0) return 0;
  return arr[0] + sum(arr.slice(1));
}
console.log(sum([1,2,3,4])); // 10
```

---

## 34. Immediately Invoked Async Function
**Theory:**
Async IIFE allows asynchronous code to run immediately without polluting the global scope. Useful for setup scripts and asynchronous initialization.

**Code:**
```js
(async function(){
  const data = await Promise.resolve(5);
  console.log(data);
})();
```

---

## 35. Nested Functions
**Theory:**
Functions defined inside other functions can access variables from the outer function. This is useful for encapsulating logic and creating private helper functions.

**Code:**
```js
function outer(){
  let a = 1;
  function inner(){
    console.log(a);
  }
  inner();
}
outer(); // 1
```

---

## 36. Function Arguments Object
**Theory:**
The `arguments` object is an array-like object accessible inside all non-arrow functions. It contains all arguments passed to the function, allowing flexibility when the number of arguments is unknown.

**Code:**
```js
function test(){
  console.log(arguments);
}
test(1,2,3);
```

---

## 37. Function Default with Expressions
**Theory:**
Default parameters can be expressions or even function calls, providing dynamic default values when no argument is passed.

**Code:**
```js
function greet(name = `Guest`) {
  console.log(name);
}
greet(); // Guest
```

---

## 38. Function with Destructured Parameters
**Theory:**
Functions can destructure object parameters, making code more readable and avoiding repetitive property access.

**Code:**
```js
function display({name, age}){
  console.log(name, age);
}
display({name:"Vikas", age:25});
```

---

## 39. Function Overriding
**Theory:**
JavaScript allows the last function defined with the same name to override previous ones in the same scope. This can lead to unexpected behavior if not managed carefully.

**Code:**
```js
function greet(){ console.log("Hi"); }
function greet(){ console.log("Hello"); }
greet(); // Hello
```

---

## 40. Function Memoization
**Theory:**
Memoization caches the results of expensive function calls to improve performance. It is widely used in recursion and computational-heavy tasks.

**Code:**
```js
const memo = {};
function fib(n){
  if(memo[n]) return memo[n];
  if(n <= 1) return n;
  memo[n] = fib(n-1) + fib(n-2);
  return memo[n];
}
console.log(fib(10)); // 55
```

## 41. Function with Rest and Spread
**Theory:**
Rest and spread operators allow functions to handle variable numbers of arguments and to expand arrays into individual elements. This enhances flexibility and readability.

**Code:**
```js
function sum(...nums){ return nums.reduce((a,b)=>a+b,0); }
const arr = [1,2,3];
console.log(sum(...arr)); // 6
```

---

## 42. Callback Hell and Solutions
**Theory:**
Callback hell occurs when multiple nested callbacks make code hard to read and maintain. Solutions include using promises, async/await, or modularizing functions.

**Code:**
```js
// Using Promise to flatten nested callbacks
fetchData()
  .then(data => processData(data))
  .then(result => console.log(result));
```

---

## 43. Function Parameter Destructuring with Defaults
**Theory:**
Combining destructuring and default parameters makes functions robust against missing or undefined properties.

**Code:**
```js
function createUser({name = 'Guest', age = 18} = {}){
  console.log(name, age);
}
createUser(); // Guest 18
```

---

## 44. Generator Function with Arguments
**Theory:**
Generators can accept input during execution using `next()`. This allows dynamic control of yielded values.

**Code:**
```js
function* gen(){
  const x = yield 'First';
  console.log(x);
}
const g = gen();
g.next();
g.next(42); // 42
```

---

## 45. Function with Closure for Private Variables
**Theory:**
Closures can be used to create private variables that are inaccessible from the global scope, maintaining data privacy and state.

**Code:**
```js
function counter(){
  let count=0;
  return {
    increment: ()=>++count,
    decrement: ()=>--count
  };
}
const c = counter();
c.increment(); // 1
```

---

## 46. Function Returning Object
**Theory:**
Functions can return objects, enabling dynamic creation of structured data and methods.

**Code:**
```js
function createPerson(name, age){
  return {name, age, greet(){ console.log(`Hi, I'm ${name}`); }}
}
const p = createPerson('Vikas',25);
p.greet();
```

---

## 47. Function with Optional Chaining
**Theory:**
Optional chaining in function calls prevents errors when accessing undefined properties or methods, improving code safety.

**Code:**
```js
const obj = {};
obj.sayHi?.(); // undefined, no error
```

---

## 48. Function for Currying with Multiple Arguments
**Theory:**
Currying can handle multiple arguments one by one, creating highly reusable and modular functions.

**Code:**
```js
function add(a){ return b => c => a+b+c; }
console.log(add(1)(2)(3)); // 6
```

---

## 49. Function with Logical Short-Circuit Defaults
**Theory:**
Using logical operators to set default values for parameters provides flexibility in input handling.

**Code:**
```js
function greet(name){
  name = name || 'Guest';
  console.log(`Hello ${name}`);
}
greet(); // Guest
```

---

## 50. Functions as First-Class Citizens
**Theory:**
In JavaScript, functions are first-class citizens, meaning they can be assigned to variables, passed as arguments, returned from other functions, and stored in data structures. This feature allows for highly flexible and functional programming patterns.

**Code:**
```js
const fn = function(){ return 'Hello'; };
const arr = [fn];
console.log(arr[0]()); // Hello