# 05. JavaScript ES6+ Features – 50 Interview Questions with Detailed Explanations

---

## 1. let vs var vs const
**Theory:**
`var` is function-scoped and can be hoisted. `let` and `const` are block-scoped. `const` values cannot be reassigned. Using `let` and `const` reduces bugs.

**Code:**
```js
function test(){
  var a=1;
  let b=2;
  const c=3;
}
```

---

## 2. Arrow functions
**Theory:**
Arrow functions provide a concise syntax and do not have their own `this`. They are suitable for callbacks and functional programming.

**Code:**
```js
const add = (a,b) => a+b;
console.log(add(2,3)); // 5
```

---

## 3. Default parameters
**Theory:**
ES6 allows setting default values for function parameters to avoid undefined.

**Code:**
```js
function greet(name='Guest'){ console.log('Hi',name); }
greet(); // Hi Guest
```

---

## 4. Template literals
**Theory:**
Template literals use backticks and support string interpolation, multi-line strings, and embedded expressions.

**Code:**
```js
const name='Vikas';
console.log(`Hello, ${name}`); // Hello, Vikas
```

---

## 5. Destructuring assignment
**Theory:**
Allows extracting values from arrays or objects into variables in a clean way.

**Code:**
```js
const [a,b]=[1,2];
const {x,y}={x:10,y:20};
```

---

## 6. Spread operator
**Theory:**
Spread operator `...` expands arrays or objects into individual elements or properties.

**Code:**
```js
const arr=[1,2];
const arr2=[...arr,3];
console.log(arr2); // [1,2,3]
```

---

## 7. Rest parameters
**Theory:**
Rest operator collects remaining function arguments into an array.

**Code:**
```js
function sum(...nums){ return nums.reduce((a,b)=>a+b,0); }
console.log(sum(1,2,3)); // 6
```

---

## 8. Object property shorthand
**Theory:**
Allows creating object properties when variable names match key names.

**Code:**
```js
const name='Vikas';
const obj={name};
console.log(obj); // {name:'Vikas'}
```

---

## 9. Computed property names
**Theory:**
Dynamic property names in objects using square brackets.

**Code:**
```js
const key='age';
const obj={[key]:30};
console.log(obj.age); // 30
```

---

## 10. Object destructuring with default values
**Theory:**
Assign default values when property is undefined.

**Code:**
```js
const {x=0,y=0}={x:10};
console.log(x,y); // 10,0
```

---

## 11. for...of loop
**Theory:**
Iterates over iterable objects like arrays, strings, maps, sets. Provides values directly.

**Code:**
```js
const arr=[1,2,3];
for(const val of arr){ console.log(val); }
```

---

## 12. for...in loop
**Theory:**
Iterates over enumerable properties (keys) of objects.

**Code:**
```js
const obj={a:1,b:2};
for(const key in obj){ console.log(key,obj[key]); }
```

---

## 13. Classes
**Theory:**
ES6 introduced classes as syntactic sugar over prototypes, making inheritance more intuitive.

**Code:**
```js
class Person{
  constructor(name){ this.name=name; }
  greet(){ console.log('Hi',this.name); }
}
const p=new Person('Vikas');
p.greet();
```

---

## 14. Class inheritance
**Theory:**
Classes can extend other classes using `extends` and `super` to call parent constructor.

**Code:**
```js
class Employee extends Person{
  constructor(name,id){ super(name); this.id=id; }
}
```

---

## 15. Modules: import/export
**Theory:**
ES6 modules allow splitting code into files using `export` and `import` for better maintainability.

**Code:**
```js
// utils.js
export const sum=(a,b)=>a+b;
// main.js
import {sum} from './utils.js';
```

---

## 16. Default exports
**Theory:**
A module can have one default export, simplifying import syntax.

**Code:**
```js
// utils.js
export default function(){ console.log('Hi'); }
// main.js
import greet from './utils.js';
greet();
```

---

## 17. Template literals with expressions
**Theory:**
Template literals allow expressions inside `${}` for dynamic strings.

**Code:**
```js
const a=5,b=10;
console.log(`Sum is ${a+b}`); // Sum is 15
```

---

## 18. Tagged templates
**Theory:**
Tagged templates allow custom string processing by functions.

**Code:**
```js
function tag(strings,...values){ console.log(strings,values); }
const name='Vikas';
tag`Hello ${name}`;
```

---

## 19. Symbol type
**Theory:**
Unique, immutable identifiers. Useful as object keys to prevent conflicts.

**Code:**
```js
const sym=Symbol('id');
const obj={ [sym]:123 };
```

---

## 20. Iterators and generators
**Theory:**
Iterators produce a sequence of values. Generators simplify iterator creation using `function*` and `yield`.

**Code:**
```js
function* gen(){ yield 1; yield 2; }
const g=gen();
console.log(g.next()); // {value:1,done:false}


## 21. Set data structure
**Theory:**
`Set` stores unique values of any type. Useful for eliminating duplicates and membership checks.

**Code:**
```js
const s = new Set([1,2,2,3]);
console.log(s); // Set {1,2,3}
```

---

## 22. Map data structure
**Theory:**
`Map` stores key-value pairs, preserving insertion order. Keys can be any type.

**Code:**
```js
const m = new Map();
m.set('a',1);
m.set({},2);
```

---

## 23. WeakMap
**Theory:**
`WeakMap` keys must be objects, and references are weak, allowing garbage collection.

**Code:**
```js
const wm = new WeakMap();
const obj = {};
wm.set(obj,'data');
```

---

## 24. WeakSet
**Theory:**
`WeakSet` stores objects only and allows garbage collection if no other references exist.

**Code:**
```js
const ws = new WeakSet();
const obj = {};
ws.add(obj);
```

---

## 25. Default + Rest in functions
**Theory:**
Functions can have default parameters and rest parameters together for flexibility.

**Code:**
```js
function f(a=1,...rest){ console.log(a,rest); }
f(2,3,4); // 2 [3,4]
```

---

## 26. Optional chaining (?.)
**Theory:**
Prevents errors when accessing nested properties that may not exist.

**Code:**
```js
const obj={a:{b:2}};
console.log(obj?.a?.b); // 2
console.log(obj?.c?.b); // undefined
```

---

## 27. Nullish coalescing (??)
**Theory:**
Returns the right-hand value only if the left-hand is null or undefined.

**Code:**
```js
const x = null;
console.log(x ?? 5); // 5
```

---

## 28. BigInt
**Theory:**
Represents integers beyond `Number.MAX_SAFE_INTEGER` for precision.

**Code:**
```js
const big = 123456789012345678901234567890n;
```

---

## 29. String methods: includes, startsWith, endsWith
**Theory:**
Enhanced string search and matching methods for readability.

**Code:**
```js
const str='hello';
console.log(str.includes('ell')); // true
console.log(str.startsWith('he')); // true
console.log(str.endsWith('lo')); // true
```

---

## 30. String padding: padStart, padEnd
**Theory:**
Adds padding to strings to achieve fixed length formatting.

**Code:**
```js
console.log('5'.padStart(3,'0')); // '005'
```

---

## 31. Object.assign
**Theory:**
Copies enumerable own properties from source objects to a target object.

**Code:**
```js
const target={};
const source={a:1};
Object.assign(target,source);
console.log(target); // {a:1}
```

---

## 32. Object.entries and Object.values
**Theory:**
`Object.entries` returns [key,value] pairs. `Object.values` returns values array.

**Code:**
```js
const obj={a:1,b:2};
console.log(Object.entries(obj)); // [['a',1],['b',2]]
console.log(Object.values(obj)); // [1,2]
```

---

## 33. Dynamic import()
**Theory:**
Allows importing modules asynchronously, useful for code splitting.

**Code:**
```js
import('./module.js').then(mod=>mod.func());
```

---

## 34. Promise basics
**Theory:**
`Promise` represents a future value, providing `then` and `catch` for asynchronous handling.

**Code:**
```js
const p = new Promise((res,rej)=> res(1));
p.then(console.log); // 1
```

---

## 35. async/await
**Theory:**
Simplifies asynchronous code, making it look synchronous while handling Promises.

**Code:**
```js
async function f(){
  const res = await Promise.resolve(1);
  console.log(res);
}
f();
```

---

## 36. Promise.all
**Theory:**
Waits for all promises to resolve or rejects if any fail.

**Code:**
```js
Promise.all([Promise.resolve(1),Promise.resolve(2)]).then(console.log); // [1,2]
```

---

## 37. Promise.race
**Theory:**
Returns the first resolved or rejected promise.

**Code:**
```js
Promise.race([Promise.resolve(1),new Promise(r=>setTimeout(()=>r(2),100))]).then(console.log); // 1
```

---

## 38. GlobalThis
**Theory:**
Provides a standard way to access global object across environments.

**Code:**
```js
console.log(globalThis); // window in browser, global in Node
```

---

## 39. Optional catch binding
**Theory:**
Catch block can omit the error parameter if not needed.

**Code:**
```js
try { throw 'err'; } catch { console.log('error caught'); }
```

---

## 40. Import.meta
**Theory:**
Provides metadata about the current module, such as its URL.

**Code:**
```js
console.log(import.meta.url);


## 41. Nullish coalescing vs OR operator
Symbols prevent key conflicts and are not enumerable by default.


**Code:**
```js
const sym = Symbol('id');
const obj = { [sym]: 123 };
console.log(obj[sym]); // 123
```


---


## 45. Set practical example
**Theory:**
Eliminate duplicate elements from an array.


**Code:**
```js
const arr=[1,2,2,3];
const unique=[...new Set(arr)];
console.log(unique); // [1,2,3]
```


---


## 46. Map practical example
**Theory:**
Store key-value pairs with complex object keys.


**Code:**
```js
const m=new Map();
const key={};
m.set(key,'value');
console.log(m.get(key)); // value
```


---


## 47. WeakMap practical example
**Theory:**
Use WeakMap to associate metadata with objects without preventing garbage collection.


**Code:**
```js
const wm = new WeakMap();
let obj={};
wm.set(obj,'meta');
obj=null; // eligible for GC
```


---


## 48. Destructuring function parameters
**Theory:**
Extract values from objects passed as arguments for cleaner code.


**Code:**
```js
function greet({name,age}){ console.log(name,age); }
greet({name:'Vikas',age:30});
```


---


## 49. Dynamic import practical example
**Theory:**
Load modules conditionally or on demand to improve performance.


**Code:**
```js
if(condition){ import('./module.js').then(m=>m.func()); }
```


---


## 50. Generator practical example
**Theory:**
Generators simplify implementing iterators for complex sequences.


**Code:**
```js
function* gen(){ for(let i=0;i<3;i++) yield i; }
const g=gen();
console.log(g.next().value); // 0
console.log(g.next().value); // 1