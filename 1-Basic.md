# 01. JavaScript Basics – 50 Interview Questions with Answers

---

## 1. What are the different data types in JavaScript?
**Answer:** JavaScript has 8 data types: 7 primitive (`string`, `number`, `bigint`, `boolean`, `undefined`, `symbol`, `null`) and 1 non-primitive (`object`).
```js
let str = "Hello";
let num = 42;
let big = 900719925n;
let bool = true;
let sym = Symbol("id");
let und;
let n = null;
let obj = { name: "Vikas" };
```

---

## 2. What is the difference between `==` and `===`?
**Answer:** `==` performs type coercion; `===` checks value and type.
```js
console.log(5 == "5");  // true
console.log(5 === "5"); // false
```

---

## 3. What is the difference between `var`, `let`, and `const`?
**Answer:**
- `var` → function-scoped, hoisted, can be redeclared.
- `let` → block-scoped, can be reassigned.
- `const` → block-scoped, cannot be reassigned.
```js
var a = 1;
let b = 2;
const c = 3;
```

---

## 4. What is hoisting in JavaScript?
**Answer:** Variable and function declarations are moved to the top of scope.
```js
console.log(a); // undefined
var a = 5;
```

---

## 5. Explain the difference between `null` and `undefined`.
**Answer:**
- `undefined` → declared but not assigned.
- `null` → assigned as empty.
```js
let x;
console.log(x);
let y = null;
console.log(y);
```

---

## 6. What is the difference between primitive and reference types?
**Answer:**
- Primitive values are stored directly.
- Reference types store memory references.
```js
let a = 10;
let b = a;
b = 20;
console.log(a); // 10

let obj1 = { n: 1 };
let obj2 = obj1;
obj2.n = 2;
console.log(obj1.n); // 2
```

---

## 7. What are template literals?
**Answer:** Strings with backticks supporting interpolation.
```js
let name = "Vikas";
console.log(`Hello, ${name}!`);
```

---

## 8. What are truthy and falsy values?
**Answer:**
- Falsy: `false`, `0`, `""`, `null`, `undefined`, `NaN`
```js
if ("") console.log("truthy"); else console.log("falsy");
```

---

## 9. What is type coercion?
**Answer:** Automatic conversion between types.
```js
console.log("5" * 2); // 10
```

---

## 10. How does JavaScript handle floating-point precision?
**Answer:** Uses IEEE 754 double precision.
```js
console.log(0.1 + 0.2);
```

---

## 11. What is the difference between `undefined` and `not defined`?
**Answer:** `undefined` exists but uninitialized; `not defined` never declared.
```js
let x;
console.log(x);
console.log(y); // ReferenceError
```

---

## 12. What is NaN?
**Answer:** Not-a-Number result from invalid number operations.
```js
console.log("abc" / 2);
```

---

## 13. How do you check if a value is NaN?
**Answer:** Use `Number.isNaN()`.
```js
console.log(Number.isNaN("abc" / 2));
```

---

## 14. What are default parameters?
**Answer:** Function parameters with defaults.
```js
function greet(name = "Guest") {
  return `Hello, ${name}`;
}
```

---

## 15. What are arrow functions?
**Answer:** Shorter syntax, lexical `this`.
```js
const add = (a, b) => a + b;
```

---

## 16. Difference between function declaration and function expression?
**Answer:** Declarations are hoisted, expressions are not.
```js
foo();
function foo() { console.log("Hi"); }
```

---

## 17. What is the `typeof` operator?
**Answer:** Returns type of operand.
```js
console.log(typeof null); // object
```

---

## 18. Difference between `for..in` and `for..of`?
**Answer:**
- `for..in` iterates keys.
- `for..of` iterates values.
```js
for (let k in {a:1}) console.log(k);
for (let v of [1,2]) console.log(v);
```

---

## 19. What are rest and spread operators?
**Answer:**
- Rest collects values.
- Spread expands values.
```js
function sum(...nums){ return nums.reduce((a,b)=>a+b); }
console.log(sum(1,2,3));
```

---

## 20. Difference between `slice` and `splice`?
**Answer:**
- `slice` returns new array.
- `splice` modifies original.
```js
let arr = [1,2,3];
console.log(arr.slice(1));
arr.splice(1,1);
```

---

## 21. What is event bubbling?
**Answer:** Propagation of events from child to parent.

---

## 22. What is event capturing?
**Answer:** Event flows from parent to child.

---

## 23. Difference between synchronous and asynchronous code?
**Answer:**
- Sync executes line by line.
- Async doesn’t block execution.

---

## 24. What is the global object in browsers?
**Answer:** `window`.

---

## 25. What are Immediately Invoked Function Expressions (IIFE)?
**Answer:** Functions that run immediately.
```js
(function(){ console.log("IIFE"); })();
```

---

## 26. What is strict mode?
**Answer:** A mode that catches errors and forbids unsafe actions.
```js
'use strict';
x = 3.14; // Error
```

---

## 27. What is the difference between shallow and deep copy?
**Answer:**
- Shallow → copies top-level properties.
- Deep → copies nested objects too.

---

## 28. How do you clone an object?
**Answer:**
```js
let obj = { a:1 };
let copy = { ...obj };
```

---

## 29. Difference between function scope and block scope?
**Answer:**
- `var` → function scoped.
- `let/const` → block scoped.

---

## 30. What are closures?
**Answer:** Functions that capture variables from outer scope.
```js
function outer(){
  let count = 0;
  return function(){ count++; return count; }
}
```

---

## 31. What is the call stack?
**Answer:** A stack data structure storing function execution context.

---

## 32. Difference between stack and heap?
**Answer:**
- Stack → primitive values.
- Heap → objects.

---

## 33. What is memoization?
**Answer:** Caching results of function calls.

---

## 34. What is the difference between `map` and `forEach`?
**Answer:**
- `map` returns new array.
- `forEach` executes callback only.

---

## 35. What is the difference between `localStorage` and `sessionStorage`?
**Answer:**
- `localStorage` persists until cleared.
- `sessionStorage` lasts per tab session.

---

## 36. What is JSON?
**Answer:** JavaScript Object Notation, lightweight data format.

---

## 37. How do you parse and stringify JSON?
**Answer:**
```js
let obj = JSON.parse('{"a":1}');
let str = JSON.stringify({a:1});
```

---

## 38. What is the difference between function arguments and parameters?
**Answer:** Parameters are declared; arguments are passed values.

---

## 39. What are template engines?
**Answer:** Libraries that generate HTML using templates.

---

## 40. What is the difference between GET and POST?
**Answer:**
- GET sends data via URL.
- POST sends data in body.

---

## 41. What is the difference between cookies and localStorage?
**Answer:** Cookies send data with requests; localStorage is client-side only.

---

## 42. What is a promise?
**Answer:** An object representing eventual completion/failure of async task.

---

## 43. Difference between microtask and macrotask?
**Answer:**
- Microtasks → promises.
- Macrotasks → setTimeout, setInterval.

---

## 44. What is the difference between `apply`, `call`, and `bind`?
**Answer:**
- `call` → invoke with args.
- `apply` → invoke with args array.
- `bind` → returns new function.

---

## 45. What is currying?
**Answer:** Transforming a function with multiple arguments into a series of functions.

---

## 46. Difference between ES5 and ES6?
**Answer:** ES6 introduced `let`, `const`, arrow functions, classes, promises, modules.

---

## 47. What are symbols?
**Answer:** Unique, immutable values often used as object keys.

---

## 48. What is BigInt?
**Answer:** A data type for arbitrarily large integers.
```js
let big = 1234567890123456789012345678901234567890n;
```

---

## 49. Difference between shallow equality and deep equality?
**Answer:**
- Shallow compares references.
- Deep compares values recursively.

---

## 50. What is the difference between `== undefined` and `=== undefined`?
**Answer:** `== undefined` checks for both null and undefined, `===` checks strictly undefined.
```js
let a;
console.log(a == undefined);  // true
console.log(a === undefined); // true
```
