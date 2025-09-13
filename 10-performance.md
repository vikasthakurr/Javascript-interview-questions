# 10. JavaScript Performance & Memory – 50 Interview Questions with Detailed Explanations

---

## 1. What is JavaScript performance optimization?
**Theory:**
Performance optimization involves improving execution speed, reducing memory usage, and making applications responsive.

**Code:**
```js
console.time('loop');
for(let i=0;i<1000000;i++){}
console.timeEnd('loop');
```

---

## 2. How to measure performance in JS?
**Theory:**
Use `console.time`/`console.timeEnd`, Performance API, or browser profiling tools.

**Code:**
```js
const t0 = performance.now();
for(let i=0;i<100000;i++){}
const t1 = performance.now();
console.log(`Time: ${t1-t0} ms`);
```

---

## 3. What is memory leak?
**Theory:**
Memory leak occurs when unused memory is not released, leading to increased memory usage.

**Code:**
```js
const leakyArray = [];
function leak(){ leakyArray.push(new Array(1000).fill('*')); }
```

---

## 4. How to detect memory leaks?
**Theory:**
Use Chrome DevTools Memory tab, heap snapshots, and timeline to detect increasing memory usage.

---

## 5. What is garbage collection?
**Theory:**
Automatic memory management that removes objects no longer referenced.

---

## 6. Types of garbage collection algorithms
**Theory:**
- Reference counting
- Mark-and-sweep

---

## 7. Optimizing loops
**Theory:**
Avoid unnecessary calculations inside loops, cache length, and prefer for-loops over for-in for arrays.

**Code:**
```js
for(let i=0, len=arr.length;i<len;i++){}
```

---

## 8. Event delegation
**Theory:**
Attach a single event listener to a parent instead of multiple child elements to reduce memory usage.

**Code:**
```js
document.querySelector('#parent').addEventListener('click', e=>console.log(e.target));
```

---

## 9. Debouncing and throttling
**Theory:**
- Debounce: limit function execution after idle time.
- Throttle: limit function execution to fixed intervals.

**Code:**
```js
function debounce(fn, delay){
  let timer;
  return (...args)=>{
    clearTimeout(timer);
    timer=setTimeout(()=>fn(...args), delay);
  };
}
```

---

## 10. Minimizing reflows and repaints
**Theory:**
Batch DOM changes, use classList, avoid inline styles to improve performance.

**Code:**
```js
const frag = document.createDocumentFragment();
for(let i=0;i<100;i++){
  const li=document.createElement('li');
  li.textContent=i;
  frag.appendChild(li);
}
document.querySelector('ul').appendChild(frag);
```

---

## 11. Using requestAnimationFrame
**Theory:**
Synchronize animations with browser repaint for smoother visuals.

**Code:**
```js
function animate(){
  // update animation
  requestAnimationFrame(animate);
}
requestAnimationFrame(animate);
```

---

## 12. Avoiding memory leaks with closures
**Theory:**
Release references in closures if not needed to prevent leaks.

**Code:**
```js
let closure;
function create(){
  let largeObj={};
  closure = ()=>console.log('Using obj');
}
create();
closure=null;
```

---

## 13. Minimizing global variables
**Theory:**
Reduce global variables to prevent accidental memory retention.

**Code:**
```js
(function(){
  const localVar=1;
})();
```

---

## 14. Efficient array methods
**Theory:**
Prefer `map`, `filter`, `forEach` carefully; avoid unnecessary intermediate arrays.

---

## 15. String concatenation
**Theory:**
Use array join or template literals instead of `+` for large strings.

**Code:**
```js
let strArr=[];
for(let i=0;i<1000;i++) strArr.push(i);
let result=strArr.join('');
```

---

## 16. Using Web Workers
**Theory:**
Run heavy computations in background threads to avoid blocking main thread.

**Code:**
```js
const worker = new Worker('worker.js');
worker.postMessage(data);
```

---

## 17. Lazy loading
**Theory:**
Load resources or modules only when needed to improve initial performance.

**Code:**
```js
import('./module.js').then(m=>m.init());
```

---

## 18. Image optimization
**Theory:**
Use compressed formats, proper sizes, and lazy loading.

**Code:**
```html
<img src='image.jpg' loading='lazy'/>
```

---

## 19. Minification
**Theory:**
Reduce JS file size by removing whitespace, comments, and shortening variable names.

---

## 20. Profiling JavaScript
**Theory:**
Use browser DevTools Performance tab to profile function execution and rendering.

---

## 21. Reducing DOM access
**Theory:**
Access DOM as few times as possible; store references in variables.

**Code:**
```js
const el=document.getElementById('myEl');
el.style.color='red';
```

---

## 22. Caching values
**Theory:**
Cache repeated calculations or DOM queries for efficiency.

**Code:**
```js
const len=arr.length;
for(let i=0;i<len;i++){}
```

---

## 23. Using localStorage/sessionStorage efficiently
**Theory:**
Store only necessary data, avoid frequent writes to reduce blocking main thread.

**Code:**
```js
localStorage.setItem('key','value');
```

---

## 24. Using Map and Set
**Theory:**
Maps and Sets provide faster lookups and unique collections compared to arrays.

**Code:**
```js
const map=new Map(); map.set('a',1);
const set=new Set([1,2,3]);
```

---

## 25. Memory profiling
**Theory:**
Use Chrome DevTools Memory tab to take heap snapshots and detect leaks.


## 26. Debounce vs Throttle
**Theory:**
Debounce delays function execution until after a pause. Throttle executes function at regular intervals.

**Code:**
```js
function throttle(fn, limit){
  let lastCall=0;
  return function(...args){
    const now = Date.now();
    if(now - lastCall >= limit){ fn(...args); lastCall = now; }
  };
}
```

---

## 27. Optimizing event listeners
**Theory:**
Attach listeners to parent using event delegation instead of multiple child listeners.

**Code:**
```js
document.body.addEventListener('click', e=>{ if(e.target.matches('.btn')) console.log('Clicked'); });
```

---

## 28. Virtual DOM (React)
**Theory:**
Minimizes DOM updates by computing diffs and updating only changed parts.

---

## 29. Avoiding forced synchronous layouts
**Theory:**
Reading and writing layout properties repeatedly causes reflows. Batch reads/writes.

**Code:**
```js
const width = el.offsetWidth;
el.style.height = width + 'px';
```

---

## 30. Using requestIdleCallback
**Theory:**
Run non-critical tasks during browser idle periods.

**Code:**
```js
requestIdleCallback(()=>{ console.log('Idle task'); });
```

---

## 31. Profiling memory in Node.js
**Theory:**
Use `--inspect` and DevTools to monitor Node app memory usage.

---

## 32. Optimizing JSON operations
**Theory:**
Use streaming parsers for large JSON, avoid unnecessary stringify/parse cycles.

**Code:**
```js
const obj = JSON.parse(jsonString);
```

---

## 33. Using WebAssembly
**Theory:**
Move CPU-intensive code to WebAssembly for faster execution.

---

## 34. Minimizing DOM nodes
**Theory:**
Fewer nodes reduce layout calculation and memory usage.

---

## 35. Lazy evaluation
**Theory:**
Delay computations until needed to save resources.

**Code:**
```js
const lazyVal = ()=>computeHeavy();
```

---

## 36. Using document fragments
**Theory:**
Append multiple nodes using a fragment to reduce reflows.

**Code:**
```js
const frag = document.createDocumentFragment();
arr.forEach(i=>frag.appendChild(document.createElement('div')));
document.body.appendChild(frag);
```

---

## 37. Minimize use of with statement
**Theory:**
`with` can slow performance due to scope chain changes.

---

## 38. Optimize CSS selectors
**Theory:**
Simpler selectors improve DOM query performance.

---

## 39. Using Web Workers for computation
**Theory:**
Offload heavy loops or calculations to workers to keep UI responsive.

**Code:**
```js
const worker = new Worker('worker.js');
worker.postMessage(data);
```

---

## 40. Avoid unnecessary libraries
**Theory:**
Large libraries add overhead. Use native functions or small modules.

---

## 41. Image lazy loading
**Theory:**
Use `loading='lazy'` or IntersectionObserver to load images when visible.

**Code:**
```html
<img src='img.jpg' loading='lazy'/>
```

---

## 42. Minimize HTTP requests
**Theory:**
Combine files or use HTTP/2 to reduce network overhead.

---

## 43. Prefetching and preloading
**Theory:**
Load resources in advance for smoother performance.

**Code:**
```html
<link rel='preload' href='script.js'>
```

---

## 44. Optimize loops with map/filter/reduce
**Theory:**
Avoid multiple iterations, chain methods wisely.

---

## 45. Avoiding excessive DOM reads/writes
**Theory:**
Batch updates, avoid layout thrashing.

---

## 46. Using CSS containment
**Theory:**
`contain` property isolates layout, paint, and size for performance.

**Code:**
```css
.my-component { contain: layout paint; }
```

---

## 47. Using passive event listeners
**Theory:**
Improve scroll performance by marking listeners passive.

**Code:**
```js
document.addEventListener('scroll', handler, { passive: true });
```

---

## 48. Memory management with closures
**Theory:**
Avoid retaining large objects in closures unnecessarily.

---

## 49. Profiling with Chrome DevTools
**Theory:**
Use Timeline and Performance tabs to identify bottlenecks.

---

## 50. Best practices
**Theory:**
- Minimize DOM access
- Reduce memory leaks
- Use efficient algorithms
- Lazy load resources
- Use requestAnimationFrame for animations
- Profile regularly and optimize bottlenecks

**Code:**
```js
// Example: optimized loop
for(let i=0,len=arr.length;i<len;i++){
  process(arr[i]);
}
```
