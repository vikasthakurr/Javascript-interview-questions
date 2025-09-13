# 03. JavaScript Objects & Prototypes – 50 Interview Questions with Detailed Explanations

---

## 1. What is an object in JavaScript?
**Theory:**
An object is a collection of key-value pairs where keys are strings (or symbols) and values can be any type, including other objects or functions. Objects allow grouping related data and behaviors together and are fundamental for structuring and organizing code.

**Code:**
```js
const person = { name: 'Vikas', age: 25 };
console.log(person.name); // Vikas
```

---

## 2. Difference between primitive and reference types
**Theory:**
Primitives (string, number, boolean, null, undefined, symbol, bigint) are immutable and stored by value. Objects (arrays, functions, objects) are reference types and stored by reference. Understanding this difference is crucial for memory management and equality checks.

**Code:**
```js
let a = 10, b = a;
b = 20; console.log(a); // 10

let obj1 = {x:1}, obj2 = obj1;
obj2.x = 2; console.log(obj1.x); // 2
```

---

## 3. Accessing object properties
**Theory:**
Properties can be accessed using dot notation or bracket notation. Bracket notation allows dynamic property access.

**Code:**
```js
const obj = { name: 'Vikas' };
console.log(obj.name); // dot
console.log(obj['name']); // bracket
```

---

## 4. Adding and deleting properties
**Theory:**
Properties can be added or deleted at runtime. This dynamic nature of objects allows flexible data manipulation.

**Code:**
```js
const obj = {};
obj.age = 25;
delete obj.age;
console.log(obj.age); // undefined
```

---

## 5. Object.freeze, Object.seal, Object.preventExtensions
**Theory:**
- `Object.freeze` makes an object immutable.
- `Object.seal` prevents adding/removing properties but allows modification.
- `Object.preventExtensions` prevents adding new properties.

**Code:**
```js
const obj = {name: 'Vikas'};
Object.freeze(obj);
obj.name = 'Test';
console.log(obj.name); // Vikas
```

---

## 6. Object.keys, Object.values, Object.entries
**Theory:**
These methods allow retrieving an object’s keys, values, or key-value pairs as arrays, facilitating iteration and transformation.

**Code:**
```js
const obj = {a:1,b:2};
console.log(Object.keys(obj)); // ['a','b']
console.log(Object.values(obj)); // [1,2]
console.log(Object.entries(obj)); // [['a',1],['b',2]]
```

---

## 7. Object Destructuring
**Theory:**
Object destructuring extracts values from objects into variables, improving readability and reducing repetitive code.

**Code:**
```js
const person = {name: 'Vikas', age: 25};
const {name, age} = person;
console.log(name, age); // Vikas 25
```

---

## 8. Nested object destructuring
**Theory:**
Allows extracting nested properties directly into variables, simplifying access to deeply nested data.

**Code:**
```js
const person = {name:'Vikas', address:{city:'Delhi', zip:110001}};
const {address:{city, zip}} = person;
console.log(city, zip); // Delhi 110001
```

---

## 9. Spread operator with objects
**Theory:**
The spread operator (`...`) copies properties from one object to another, useful for cloning or merging objects.

**Code:**
```js
const obj1 = {a:1};
const obj2 = {...obj1, b:2};
console.log(obj2); // {a:1, b:2}
```

---

## 10. Object.assign
**Theory:**
`Object.assign` copies enumerable properties from source objects to a target object. It’s commonly used for cloning or merging objects.

**Code:**
```js
const target = {a:1};
const source = {b:2};
Object.assign(target, source);
console.log(target); // {a:1, b:2}
```

---

## 11. Prototypes in JavaScript
**Theory:**
Every JavaScript object has a prototype. The prototype is an object from which other objects inherit properties and methods. Understanding prototypes is key for memory efficiency and inheritance.

**Code:**
```js
function Person(name){ this.name=name; }
Person.prototype.greet=function(){ console.log('Hi ' + this.name); };
const p = new Person('Vikas');
p.greet(); // Hi Vikas
```

---

## 12. Prototype Chain
**Theory:**
Objects inherit properties from their prototype, which may have its own prototype, forming a chain. JavaScript looks up the chain for property/method access.

**Code:**
```js
const obj = {};
console.log(obj.toString()); // inherited from Object.prototype
```

---

## 13. hasOwnProperty
**Theory:**
Checks if an object has a property directly on itself, not inherited from prototype.

**Code:**
```js
const obj = {a:1};
console.log(obj.hasOwnProperty('a')); // true
console.log(obj.hasOwnProperty('toString')); // false
```

---

## 14. Object.create
**Theory:**
Creates a new object with the specified prototype, useful for inheritance and creating objects without constructor functions.

**Code:**
```js
const proto = { greet(){ console.log('Hi'); } };
const obj = Object.create(proto);
obj.greet(); // Hi
```

---

## 15. Constructor Functions
**Theory:**
Special functions used to create objects with `new` keyword. They define properties and methods shared across instances through prototypes.

**Code:**
```js
function Person(name){ this.name=name; }
const p = new Person('Vikas');
console.log(p.name); // Vikas
```

---

## 16. ES6 Classes
**Theory:**
Classes provide syntactic sugar over constructor functions and prototypes, making object-oriented programming more readable and maintainable.

**Code:**
```js
class Person{
  constructor(name){ this.name=name; }
  greet(){ console.log('Hi ' + this.name); }
}
const p = new Person('Vikas');
p.greet(); // Hi Vikas
```

---

## 17. Getters and Setters
**Theory:**
Getters and setters allow encapsulation and controlled access/modification of object properties.

**Code:**
```js
const obj = {
  firstName:'Vikas',
  lastName:'Kumar',
  get fullName(){ return `${this.firstName} ${this.lastName}`; },
  set fullName(name){ [this.firstName, this.lastName] = name.split(' '); }
};
console.log(obj.fullName); // Vikas Kumar
obj.fullName = 'John Doe';
console.log(obj.firstName); // John
```

---

## 18. Object Descriptors
**Theory:**
Object properties have descriptors controlling writability, enumerability, and configurability. `Object.defineProperty` allows fine-grained control over properties.

**Code:**
```js
const obj = {};
Object.defineProperty(obj, 'x', { value: 42, writable:false });
console.log(obj.x); // 42
```

---

## 19. Object Immutability Techniques
**Theory:**
Immutability can be enforced using `Object.freeze`, `Object.seal`, or cloning with spread operator. Immutability helps prevent side effects and bugs.

**Code:**
```js
const obj = {a:1};
Object.freeze(obj);
obj.a = 2;
console.log(obj.a); // 1
```

---

## 20. Inheritance using ES6 Classes
**Theory:**
Classes can inherit properties and methods from parent classes using `extends` and `super`, enabling code reuse and modular design.

**Code:**
```js
class Animal{ speak(){ console.log('Animal speaks'); } }
class Dog extends Animal{ speak(){ console.log('Dog barks'); super.speak(); } }
const d = new Dog();
d.speak(); // Dog barks
           // Animal speaks
# 03. JavaScript Objects & Prototypes – 50 Interview Questions with Detailed Explanations (Continued)

---

## 21. Inheritance using Object.create
**Theory:**
`Object.create` allows creating an object with a specified prototype, enabling inheritance without using classes.

**Code:**
```js
const parent = {greet(){ console.log('Hi'); }};
const child = Object.create(parent);
child.greet(); // Hi
```

---

## 22. Prototypal Inheritance vs Classical Inheritance
**Theory:**
JavaScript uses prototypal inheritance where objects inherit directly from other objects. Classical inheritance uses classes and instances. Prototypal inheritance allows flexible object extension at runtime.

**Code:**
```js
function Parent(){ this.name='Parent'; }
Parent.prototype.sayHi = function(){ console.log(this.name); };
const child = new Parent();
child.sayHi(); // Parent
```

---

## 23. hasOwnProperty vs in operator
**Theory:**
`hasOwnProperty` checks if the property exists directly on the object. The `in` operator checks both the object and its prototype chain.

**Code:**
```js
const obj = {a:1};
console.log(obj.hasOwnProperty('a')); // true
console.log('toString' in obj); // true
```

---

## 24. instanceof Operator
**Theory:**
`instanceof` checks if an object is an instance of a constructor function, following the prototype chain. It is useful for type checking.

**Code:**
```js
function Person(){}
const p = new Person();
console.log(p instanceof Person); // true
```

---

## 25. Constructor vs Factory Function
**Theory:**
Constructor functions use `new` to create objects and support prototypes. Factory functions return objects directly without using `new`. Choice depends on inheritance and code structure.

**Code:**
```js
function createPerson(name){ return {name}; }
const p = createPerson('Vikas');
console.log(p.name); // Vikas
```

---

## 26. Object Cloning Techniques
**Theory:**
Objects can be cloned using spread operator, `Object.assign`, or JSON methods. Deep cloning is necessary for nested objects.

**Code:**
```js
const obj1 = {a:1};
const obj2 = {...obj1};
console.log(obj2); // {a:1}
```

---

## 27. Object Reference Issues
**Theory:**
Assigning objects creates references, not copies. Modifying one object affects all references pointing to it.

**Code:**
```js
const obj1 = {a:1};
const obj2 = obj1;
obj2.a = 2;
console.log(obj1.a); // 2
```

---

## 28. Symbols as Object Keys
**Theory:**
Symbols provide unique keys for object properties, preventing accidental property overwrites and ensuring privacy.

**Code:**
```js
const sym = Symbol('id');
const obj = {[sym]: 123};
console.log(obj[sym]); // 123
```

---

## 29. Computed Property Names
**Theory:**
ES6 allows dynamic property names in object literals using computed expressions. Useful for programmatic property creation.

**Code:**
```js
const key = 'name';
const obj = {[key]:'Vikas'};
console.log(obj.name); // Vikas
```

---

## 30. Object Methods Shorthand
**Theory:**
ES6 allows defining methods in object literals without the `function` keyword, improving readability.

**Code:**
```js
const obj = { greet(){ console.log('Hi'); } };
obj.greet(); // Hi
```

---

## 31. Object Destructuring with Rest
**Theory:**
The rest operator collects remaining properties into a new object, simplifying object manipulation.

**Code:**
```js
const obj = {a:1, b:2, c:3};
const {a, ...rest} = obj;
console.log(rest); // {b:2, c:3}
```

---

## 32. Merging Objects
**Theory:**
Multiple objects can be merged using `Object.assign` or spread operator. Later properties override earlier ones.

**Code:**
```js
const obj1 = {a:1};
const obj2 = {b:2};
const merged = {...obj1, ...obj2};
console.log(merged); // {a:1,b:2}
```

---

## 33. Freezing Nested Objects
**Theory:**
`Object.freeze` only freezes the first-level properties. Deep freezing requires recursively freezing nested objects to ensure immutability.

**Code:**
```js
const obj = {a:{b:2}};
Object.freeze(obj);
obj.a.b = 3;
console.log(obj.a.b); // 3 (not frozen)
```

---

## 34. Prototypal Method Sharing
**Theory:**
Methods can be shared across instances via the prototype, saving memory and ensuring consistent behavior.

**Code:**
```js
function Person(name){ this.name=name; }
Person.prototype.greet=function(){ console.log('Hi '+this.name); };
const p1 = new Person('Vikas');
const p2 = new Person('John');
p1.greet(); // Hi Vikas
p2.greet(); // Hi John
```

---

## 35. __proto__ vs prototype
**Theory:**
- `__proto__` is the actual object’s prototype. 
- `prototype` is a property of functions used to build `__proto__` for instances. Understanding this distinction is key for inheritance.

**Code:**
```js
function Person(){}
const p = new Person();
console.log(p.__proto__ === Person.prototype); // true
```

---

## 36. Deleting Inherited Properties
**Theory:**
Deleting a property only affects the object itself, not its prototype. Prototype chain properties remain accessible.

**Code:**
```js
const proto = {a:1};
const obj = Object.create(proto);
delete obj.a;
console.log(obj.a); // 1 (from prototype)
```

---

## 37. Object Extensibility
**Theory:**
`Object.preventExtensions` stops adding new properties but allows existing ones to be modified or deleted.

**Code:**
```js
const obj = {a:1};
Object.preventExtensions(obj);
obj.b = 2;
console.log(obj.b); // undefined
```

---

## 38. Checking Property Descriptors
**Theory:**
`Object.getOwnPropertyDescriptor` reveals property attributes like writable, enumerable, and configurable.

**Code:**
```js
const obj = {a:1};
console.log(Object.getOwnPropertyDescriptor(obj,'a'));
```

---

## 39. Sealing Objects
**Theory:**
`Object.seal` prevents addition or deletion of properties but allows modification of existing ones.

**Code:**
```js
const obj = {a:1};
Object.seal(obj);
delete obj.a;
console.log(obj.a); // 1
```

---

## 40. Object.is vs ===
**Theory:**
`Object.is` is similar to strict equality (`===`) but treats `NaN` as equal to itself and distinguishes +0 and -0.

**Code:**
```js
console.log(NaN === NaN); // false
console.log(Object.is(NaN, NaN)); // true

# 03. JavaScript Objects & Prototypes – 50 Interview Questions with Detailed Explanations (Continued)

---

## 41. Object Prototype Pollution
**Theory:**
Prototype pollution occurs when an object’s prototype is maliciously or accidentally modified, affecting all objects that inherit from it. Understanding this helps in writing secure code.

**Code:**
```js
const obj = {};
Object.prototype.polluted = 'yes';
console.log({}.polluted); // yes
```

---

## 42. Object Iteration
**Theory:**
Objects can be iterated using `for...in`, `Object.keys`, `Object.values`, or `Object.entries`. Each has use cases and caveats regarding inherited properties.

**Code:**
```js
const obj = {a:1,b:2};
for(let key in obj){ console.log(key,obj[key]); }
Object.keys(obj).forEach(k => console.log(k,obj[k]));
```

---

## 43. Object.hasOwn (ES2022)
**Theory:**
`Object.hasOwn` is a safer and modern alternative to `hasOwnProperty`, preventing prototype pollution issues.

**Code:**
```js
const obj = {a:1};
console.log(Object.hasOwn(obj,'a')); // true
```

---

## 44. Dynamic Property Access
**Theory:**
Bracket notation allows dynamic access to object properties, useful when property names are computed at runtime.

**Code:**
```js
const obj = {a:1};
const prop = 'a';
console.log(obj[prop]); // 1
```

---

## 45. Object Property Shorthand
**Theory:**
ES6 allows property shorthand when variable names match object keys, reducing verbosity.

**Code:**
```js
const name = 'Vikas';
const obj = {name};
console.log(obj.name); // Vikas
```

---

## 46. Object Method Borrowing
**Theory:**
Objects can borrow methods from other objects using `call` or `apply`, enabling code reuse without inheritance.

**Code:**
```js
const obj1 = {name:'Vikas', greet(){ console.log(this.name); }};
const obj2 = {name:'John'};
obj1.greet.call(obj2); // John
```

---

## 47. Object Destructuring with Renaming
**Theory:**
Destructuring allows renaming variables while extracting properties for clarity or avoiding conflicts.

**Code:**
```js
const obj = {firstName:'Vikas'};
const {firstName: fname} = obj;
console.log(fname); // Vikas
```

---

## 48. Objects in JSON
**Theory:**
Objects can be serialized to JSON using `JSON.stringify` and parsed back using `JSON.parse`. Useful for storing or sending data over networks.

**Code:**
```js
const obj = {a:1};
const json = JSON.stringify(obj);
console.log(json); // "{"a":1}"
console.log(JSON.parse(json)); // {a:1}
```

---

## 49. Object.hasOwnProperty vs Object.keys.includes
**Theory:**
`hasOwnProperty` checks only own properties. `Object.keys(obj).includes('prop')` achieves similar functionality but creates an array, which may affect performance.

**Code:**
```js
const obj = {a:1};
console.log(obj.hasOwnProperty('a')); // true
console.log(Object.keys(obj).includes('a')); // true
```

---

## 50. Objects and Memory Management
**Theory:**
Objects are stored in heap memory. Unreferenced objects are garbage collected. Understanding memory allocation helps prevent leaks and optimize performance.

**Code:**
```js
let obj = {a:1};
obj = null; // eligible for garbage collection