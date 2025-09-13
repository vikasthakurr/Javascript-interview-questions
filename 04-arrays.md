# 04. JavaScript Arrays & Iteration – 50 Interview Questions with Detailed Explanations

---

## 1. What is an array in JavaScript?
**Theory:**
An array is an ordered collection of values that can hold elements of any type. Arrays allow storing multiple items under a single variable, providing methods for iteration, manipulation, and querying.

**Code:**
```js
const arr = [1, 2, 3, 'Vikas'];
console.log(arr[0]); // 1
```

---

## 2. Difference between array and object
**Theory:**
Arrays are ordered lists indexed by numbers, optimized for sequential access. Objects are key-value stores indexed by strings (or symbols), used for unordered data and mappings.

**Code:**
```js
const arr = [1,2];
const obj = {a:1,b:2};
```

---

## 3. Array length property
**Theory:**
The `length` property returns the number of elements in the array. It is dynamic and changes when elements are added or removed.

**Code:**
```js
const arr = [1,2,3];
console.log(arr.length); // 3
```

---

## 4. Adding elements to arrays
**Theory:**
Elements can be added using `push` (end), `unshift` (start), or direct index assignment. Each method has different performance characteristics.

**Code:**
```js
const arr = [1,2];
arr.push(3);
arr.unshift(0);
arr[10] = 10;
console.log(arr);
```

---

## 5. Removing elements from arrays
**Theory:**
`pop` removes the last element, `shift` removes the first, and `splice` removes elements at specific positions. Choosing the method affects performance.

**Code:**
```js
const arr = [1,2,3,4];
arr.pop();
arr.shift();
arr.splice(1,1);
console.log(arr);
```

---

## 6. Iterating over arrays
**Theory:**
Arrays can be iterated using loops (`for`, `for..of`), `forEach`, or higher-order functions like `map`, `filter`, `reduce`. Each approach serves different needs.

**Code:**
```js
const arr = [1,2,3];
arr.forEach(x => console.log(x));
```

---

## 7. map() method
**Theory:**
`map` creates a new array by applying a callback to each element. It doesn’t modify the original array and is widely used for transformations.

**Code:**
```js
const arr = [1,2,3];
const doubled = arr.map(x => x*2);
console.log(doubled); // [2,4,6]
```

---

## 8. filter() method
**Theory:**
`filter` creates a new array with elements that satisfy a given condition. Useful for extracting subsets based on criteria.

**Code:**
```js
const arr = [1,2,3,4];
const even = arr.filter(x => x%2===0);
console.log(even); // [2,4]
```

---

## 9. reduce() method
**Theory:**
`reduce` accumulates array values into a single result by applying a function iteratively. It is powerful for sums, averages, and custom aggregations.

**Code:**
```js
const arr = [1,2,3];
const sum = arr.reduce((acc,x)=>acc+x,0);
console.log(sum); // 6
```

---

## 10. find() method
**Theory:**
`find` returns the first element matching a condition. Useful when only one match is needed.

**Code:**
```js
const arr = [1,2,3];
console.log(arr.find(x => x>1)); // 2
```

---

## 11. findIndex() method
**Theory:**
`findIndex` returns the index of the first element satisfying a condition, or -1 if none.

**Code:**
```js
const arr = [1,2,3];
console.log(arr.findIndex(x => x===2)); // 1
```

---

## 12. includes() method
**Theory:**
Checks if an array contains a specific value, returning a boolean.

**Code:**
```js
const arr = [1,2,3];
console.log(arr.includes(2)); // true
```

---

## 13. indexOf() and lastIndexOf()
**Theory:**
`indexOf` returns the first occurrence index of a value. `lastIndexOf` returns the last occurrence.

**Code:**
```js
const arr = [1,2,3,2];
console.log(arr.indexOf(2)); // 1
console.log(arr.lastIndexOf(2)); // 3
```

---

## 14. Array.from() method
**Theory:**
Converts iterable or array-like objects into arrays, useful for NodeLists or strings.

**Code:**
```js
const str = 'abc';
const arr = Array.from(str);
console.log(arr); // ['a','b','c']
```

---

## 15. Array.isArray()
**Theory:**
Checks if a value is an array, avoiding confusion with objects.

**Code:**
```js
console.log(Array.isArray([1,2])); // true
console.log(Array.isArray({a:1})); // false
```

---

## 16. concat() method
**Theory:**
Merges arrays into a new array without modifying originals.

**Code:**
```js
const a=[1]; const b=[2,3];
const c = a.concat(b);
console.log(c); // [1,2,3]
```

---

## 17. slice() method
**Theory:**
Returns a shallow copy of a portion of an array without modifying it.

**Code:**
```js
const arr=[1,2,3,4];
console.log(arr.slice(1,3)); // [2,3]
```

---

## 18. splice() method
**Theory:**
Adds/removes elements in an array at a specific position, modifying the original array.

**Code:**
```js
const arr=[1,2,3,4];
arr.splice(1,2,9);
console.log(arr); // [1,9,4]
```

---

## 19. join() method
**Theory:**
Converts array elements into a string, separated by a specified delimiter.

**Code:**
```js
const arr=[1,2,3];
console.log(arr.join('-')); // 1-2-3
```

---

## 20. reverse() method
**Theory:**
Reverses the order of array elements in place.

**Code:**
```js
const arr=[1,2,3];
arr.reverse();
console.log(arr); // [3,2,1]


## 21. sort() method
**Theory:**
`sort` arranges array elements in place according to a compare function or lexicographically by default. Numbers require a compare function to avoid incorrect ordering.

**Code:**
```js
const arr = [3,1,2];
arr.sort((a,b) => a-b);
console.log(arr); // [1,2,3]
```

---

## 22. reverse vs slice for copying
**Theory:**
`reverse` modifies the original array, while `slice` can copy elements before reversing to avoid mutation.

**Code:**
```js
const arr=[1,2,3];
const rev=[...arr].reverse();
console.log(rev); // [3,2,1]
console.log(arr); // [1,2,3]
```

---

## 23. flat() method
**Theory:**
`flat` flattens nested arrays up to a specified depth, simplifying complex array structures.

**Code:**
```js
const arr=[1,[2,3],[4,[5]]];
console.log(arr.flat(2)); // [1,2,3,4,5]
```

---

## 24. flatMap() method
**Theory:**
`flatMap` maps each element to a new array and then flattens the result, combining `map` and `flat` in one operation.

**Code:**
```js
const arr=[1,2];
console.log(arr.flatMap(x => [x,x*2])); // [1,2,2,4]
```

---

## 25. fill() method
**Theory:**
`fill` sets all or part of an array to a static value. Useful for initialization.

**Code:**
```js
const arr=new Array(5).fill(0);
console.log(arr); // [0,0,0,0,0]
```

---

## 26. copyWithin() method
**Theory:**
`copyWithin` copies part of an array to another location within the same array, modifying it in place.

**Code:**
```js
const arr=[1,2,3,4];
arr.copyWithin(0,2);
console.log(arr); // [3,4,3,4]
```

---

## 27. some() method
**Theory:**
`some` checks if at least one element satisfies a condition, returning a boolean.

**Code:**
```js
const arr=[1,2,3];
console.log(arr.some(x=>x>2)); // true
```

---

## 28. every() method
**Theory:**
`every` checks if all elements satisfy a condition.

**Code:**
```js
const arr=[1,2,3];
console.log(arr.every(x=>x>0)); // true
```

---

## 29. findLast() and findLastIndex() (ES2022)
**Theory:**
`findLast` returns the last element matching a condition. `findLastIndex` returns its index.

**Code:**
```js
const arr=[1,2,3,2];
console.log(arr.findLast(x=>x%2===0)); // 2
console.log(arr.findLastIndex(x=>x%2===0)); // 3
```

---

## 30. includes() vs indexOf()
**Theory:**
`includes` returns boolean if element exists. `indexOf` returns index or -1. Use `includes` for readability.

**Code:**
```js
const arr=[1,2,3];
console.log(arr.includes(2)); // true
console.log(arr.indexOf(2)); // 1
```

---

## 31. Array destructuring
**Theory:**
Extracts elements into variables easily and supports skipping or default values.

**Code:**
```js
const arr=[1,2,3];
const [a,,c]=arr;
console.log(a,c); // 1,3
```

---

## 32. Swapping variables with destructuring
**Theory:**
Destructuring allows swapping without a temporary variable.

**Code:**
```js
let a=1,b=2;
[a,b]=[b,a];
console.log(a,b); // 2,1
```

---

## 33. Nested array destructuring
**Theory:**
Extract nested elements directly for cleaner code.

**Code:**
```js
const arr=[1,[2,3]];
const [a,[b,c]]=arr;
console.log(a,b,c); // 1 2 3
```

---

## 34. Array of objects destructuring
**Theory:**
Destructures arrays containing objects for direct access to properties.

**Code:**
```js
const arr=[{id:1},{id:2}];
const [{id:first},{id:second}]=arr;
console.log(first,second); // 1 2
```

---

## 35. Array iteration with for...of
**Theory:**
`for...of` provides clean iteration over array values, unlike `for...in` which iterates keys.

**Code:**
```js
const arr=[1,2,3];
for(const val of arr){ console.log(val); }
```

---

## 36. Array iteration with for...in
**Theory:**
`for...in` iterates over enumerable property names (indices) and is less commonly recommended for arrays.

**Code:**
```js
const arr=[1,2];
for(const i in arr){ console.log(i, arr[i]); }
```

---

## 37. Array-like objects
**Theory:**
Objects with numeric keys and `length` property behave like arrays and can be converted with `Array.from`.

**Code:**
```js
function argsToArray(){
  return Array.from(arguments);
}
console.log(argsToArray(1,2,3)); // [1,2,3]
```

---

## 38. Iterables vs Arrays
**Theory:**
Iterables implement `Symbol.iterator`. Arrays are iterables, but not all iterables are arrays (e.g., strings, sets).

**Code:**
```js
const str='abc';
for(const ch of str){ console.log(ch); }
```

---

## 39. Array.every vs some practical use
**Theory:**
Use `every` to validate all elements, `some` to check at least one element satisfies condition.

**Code:**
```js
const arr=[2,4,6];
console.log(arr.every(x=>x%2===0)); // true
console.log(arr.some(x=>x>5)); // true
```

---

## 40. Array.find vs filter
**Theory:**
`find` returns first matching element; `filter` returns all matches in a new array.

**Code:**
```js
const arr=[1,2,3,2];
console.log(arr.find(x=>x>1)); // 2
console.log(arr.filter(x=>x>1)); // [2,3,2]
```

## 41. Array.includes vs Array.indexOf for NaN
**Theory:**
`indexOf` cannot find `NaN`, while `includes` can. Important for special number handling.

**Code:**
```js
const arr=[NaN,2,3];
console.log(arr.indexOf(NaN)); // -1
console.log(arr.includes(NaN)); // true
```

---

## 42. Array.sort stability
**Theory:**
JavaScript `sort` is stable in modern engines: elements with same sort value maintain original order. Important when sorting multiple criteria.

**Code:**
```js
const arr=[{id:1,val:2},{id:2,val:2}];
arr.sort((a,b)=>a.val-b.val);
console.log(arr); // maintains relative order
```

---

## 43. Array.from with mapping function
**Theory:**
`Array.from` can accept a mapping function for transforming elements while converting.

**Code:**
```js
const arr=Array.from([1,2,3], x => x*2);
console.log(arr); // [2,4,6]
```

---

## 44. Array.keys, values, entries
**Theory:**
`keys()` returns indices, `values()` returns values, `entries()` returns [index,value] pairs. Useful for iteration.

**Code:**
```js
const arr=[1,2];
for(const [i,v] of arr.entries()){ console.log(i,v); }
```

---

## 45. Array.some practical example
**Theory:**
Check if any user is active in a users array.

**Code:**
```js
const users=[{name:'A',active:false},{name:'B',active:true}];
console.log(users.some(u=>u.active)); // true
```

---

## 46. Array.every practical example
**Theory:**
Check if all numbers are positive.

**Code:**
```js
const nums=[1,2,3];
console.log(nums.every(n=>n>0)); // true
```

---

## 47. Array.flatMap practical example
**Theory:**
Flatten nested arrays from data transformation.

**Code:**
```js
const arr=[1,2];
console.log(arr.flatMap(x=>[x,x*2])); // [1,2,2,4]
```

---

## 48. Multi-dimensional arrays
**Theory:**
Arrays can be nested. Access elements with multiple indices.

**Code:**
```js
const arr=[[1,2],[3,4]];
console.log(arr[1][0]); // 3
```

---

## 49. Array mutation vs immutability
**Theory:**
Methods like `push`, `pop`, `splice` mutate arrays. Using `map`, `filter`, `slice` creates new arrays. Understanding this prevents bugs.

**Code:**
```js
const arr=[1,2];
const newArr=arr.concat(3);
console.log(arr); // [1,2]
console.log(newArr); // [1,2,3]
```

---

## 50. Performance considerations
**Theory:**
Operations at the start (`unshift`, `shift`) are slower than end (`push`, `pop`). Large array iterations may benefit from traditional loops over higher-order functions.

**Code:**
```js
const arr=[];
for(let i=0;i<1000000;i++){ arr.push(i); }