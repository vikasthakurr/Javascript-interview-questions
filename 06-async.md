# 06. JavaScript Asynchronous – 50 Interview Questions with Detailed Explanations

---

## 1. What is asynchronous JavaScript?
**Theory:**
Asynchronous JS allows tasks to run in the background without blocking the main thread. This prevents UI freezing and enables handling long-running operations like API calls efficiently.

**Code:**
```js
setTimeout(()=>console.log('Hello'),1000);
console.log('World'); // prints first
```

---

## 2. Callback functions
**Theory:**
A callback is a function passed as an argument and executed after a task completes. Traditional async handling before Promises.

**Code:**
```js
function fetchData(cb){ setTimeout(()=> cb('Data'),1000); }
fetchData(data => console.log(data));
```

---

## 3. Callback Hell
**Theory:**
Nesting multiple callbacks leads to hard-to-read code and error handling difficulties. Modern solutions use Promises or async/await.

**Code:**
```js
setTimeout(()=>{
  setTimeout(()=>{
    console.log('Nested');
  },1000);
},1000);
```

---

## 4. Promises
**Theory:**
A Promise represents a value that may be available now, in the future, or never. It has states: pending, fulfilled, rejected.

**Code:**
```js
const p = new Promise((res,rej)=> res('Success'));
p.then(console.log);
```

---

## 5. Promise chaining
**Theory:**
Promises can be chained using `.then` to perform sequential asynchronous operations cleanly.

**Code:**
```js
Promise.resolve(1)
  .then(x=>x+1)
  .then(console.log); // 2
```

---

## 6. Promise.all
**Theory:**
Waits for all promises to resolve, or rejects if any fail. Useful for parallel async operations.

**Code:**
```js
Promise.all([Promise.resolve(1),Promise.resolve(2)]).then(console.log); // [1,2]
```

---

## 7. Promise.race
**Theory:**
Returns the first resolved/rejected promise among multiple promises.

**Code:**
```js
Promise.race([Promise.resolve(1),new Promise(r=>setTimeout(()=>r(2),100))]).then(console.log); // 1
```

---

## 8. Async/Await
**Theory:**
Async functions return a promise. `await` pauses execution until the promise resolves, making async code readable like synchronous code.

**Code:**
```js
async function fetchData(){
  const data = await Promise.resolve('Hello');
  console.log(data);
}
fetchData();
```

---

## 9. try/catch with async/await
**Theory:**
Use try/catch to handle errors in async/await code instead of `.catch`.

**Code:**
```js
async function f(){
  try{
    const data = await Promise.reject('Error');
  } catch(e){ console.log(e); }
}
f();
```

---

## 10. Event Loop
**Theory:**
Event Loop manages execution of code, callbacks, and async tasks. Microtasks (Promises) have priority over macrotasks (setTimeout).

**Code:**
```js
console.log('Start');
setTimeout(()=>console.log('Timeout'),0);
Promise.resolve().then(()=>console.log('Promise'));
console.log('End');
// Output: Start, End, Promise, Timeout
```

---

## 11. Microtasks vs Macrotasks
**Theory:**
Microtasks include Promises and process after current execution. Macrotasks include setTimeout, setInterval, processed after microtasks.

**Code:**
```js
console.log('Start');
setTimeout(()=>console.log('Macro'),0);
Promise.resolve().then(()=>console.log('Micro'));
console.log('End');
```

---

## 12. setTimeout vs setImmediate (Node.js)
**Theory:**
`setTimeout` schedules after a minimum delay; `setImmediate` executes after the current poll phase, faster than setTimeout(0).

**Code:**
```js
setImmediate(()=>console.log('Immediate'));
setTimeout(()=>console.log('Timeout'),0);
```

---

## 13. process.nextTick (Node.js)
**Theory:**
Executes a callback before the next event loop iteration. Runs before Promises in Node.js.

**Code:**
```js
process.nextTick(()=>console.log('NextTick'));
Promise.resolve().then(()=>console.log('Promise'));
```

---

## 14. fetch API
**Theory:**
Modern browser API to make HTTP requests, returns a promise.

**Code:**
```js
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(res=>res.json())
  .then(console.log);
```

---

## 15. XMLHttpRequest
**Theory:**
Legacy method for HTTP requests before fetch. Uses callbacks.

**Code:**
```js
const xhr = new XMLHttpRequest();
xhr.open('GET','/api');
xhr.onload=()=>console.log(xhr.response);
xhr.send();
```

---

## 16. setInterval
**Theory:**
Executes a function repeatedly at specified intervals.

**Code:**
```js
setInterval(()=>console.log('Hello'),1000);
```

---

## 17. clearInterval
**Theory:**
Stops an interval previously started by setInterval.

**Code:**
```js
const id=setInterval(()=>console.log('Hello'),1000);
clearInterval(id);
```

---

## 18. setTimeout returns a timer ID
**Theory:**
Use this ID to cancel the timeout using clearTimeout.

**Code:**
```js
const id=setTimeout(()=>console.log('Hi'),1000);
clearTimeout(id);
```

---

## 19. Promise.resolve vs new Promise
**Theory:**
`Promise.resolve(value)` creates a resolved promise. `new Promise` requires an executor function.

**Code:**
```js
Promise.resolve(1).then(console.log);
new Promise(res=>res(2)).then(console.log);
```

---

## 20. Error handling in promises
**Theory:**
Use `.catch` to handle rejected promises or errors in promise chains.

**Code:**
```js
Promise.reject('Error').catch(console.log);


## 21. Async iteration
**Theory:**
`for await...of` allows iteration over asynchronous iterables, like streams or async generators.

**Code:**
```js
async function* gen(){
  yield Promise.resolve(1);
  yield Promise.resolve(2);
}
(async()=>{
  for await(const val of gen()) console.log(val);
})();
```

---

## 22. Async generators
**Theory:**
Generators that can yield Promises, allowing asynchronous sequences to be processed with `for await...of`.

**Code:**
```js
async function* gen(){
  for(let i=0;i<3;i++) yield Promise.resolve(i);
}
```

---

## 23. Event loop phases
**Theory:**
Node.js event loop has phases: timers, pending callbacks, idle/prepare, poll, check, close callbacks. Each phase executes specific callback types.

**Code:**
```js
// Cannot demonstrate fully in simple snippet, but timers and microtasks run in specific order
```

---

## 24. setImmediate vs setTimeout(0) difference
**Theory:**
`setImmediate` executes after current poll phase. `setTimeout(0)` schedules a macrotask after min delay. Ordering may differ under heavy I/O.

**Code:**
```js
setImmediate(()=>console.log('Immediate'));
setTimeout(()=>console.log('Timeout'),0);
```

---

## 25. Promisify callback functions
**Theory:**
Convert traditional callback-based functions into Promises for easier async handling.

**Code:**
```js
const fs = require('fs');
const readFile = file => new Promise((res,rej)=>{
  fs.readFile(file,'utf8',(err,data)=>err?rej(err):res(data));
});
```

---

## 26. await inside loops
**Theory:**
Using `await` inside loops waits for each promise sequentially. For parallel execution, use `Promise.all`.

**Code:**
```js
for(const p of promises){
  await p; // sequential
}
```

---

## 27. Error propagation with async/await
**Theory:**
Errors inside async functions can be propagated using throw and caught with try/catch at caller.

**Code:**
```js
async function f(){ throw 'err'; }
(async()=>{
  try{ await f(); } catch(e){ console.log(e); }
})();
```

---

## 28. Combining multiple async calls
**Theory:**
Use `Promise.all` or `Promise.allSettled` to execute multiple async tasks in parallel and handle their results.

**Code:**
```js
Promise.all([fetch(url1),fetch(url2)]).then(res=>console.log(res));
```

---

## 29. Promise.allSettled
**Theory:**
Waits for all promises to settle, regardless of success or failure. Useful for reporting results.

**Code:**
```js
Promise.allSettled([Promise.resolve(1),Promise.reject('err')]).then(console.log);
```

---

## 30. Cancellation of async tasks
**Theory:**
Promises cannot be canceled natively, but AbortController can cancel fetch requests.

**Code:**
```js
const controller = new AbortController();
fetch(url,{signal:controller.signal});
controller.abort();
```

---

## 31. Debouncing async operations
**Theory:**
Debouncing ensures a function runs only after a pause in events, reducing API calls.

**Code:**
```js
function debounce(fn,delay){
  let timer;
  return (...args)=>{
    clearTimeout(timer);
    timer=setTimeout(()=>fn(...args),delay);
  }
}
```

---

## 32. Throttling async operations
**Theory:**
Throttling limits function execution to once per time interval.

**Code:**
```js
function throttle(fn,limit){
  let lastCall=0;
  return (...args)=>{
    const now=Date.now();
    if(now-lastCall>=limit){ fn(...args); lastCall=now; }
  }
}
```

---

## 33. Event-driven programming
**Theory:**
JS uses events to respond to user actions or async events without blocking main thread.

**Code:**
```js
document.addEventListener('click',()=>console.log('Clicked'));
```

---

## 34. Promises with setTimeout
**Theory:**
Wrap setTimeout in Promise for async delay.

**Code:**
```js
const delay = ms => new Promise(res=>setTimeout(res,ms));
await delay(1000);
```

---

## 35. Async queue
**Theory:**
Maintain sequential execution of async tasks using a queue or async/await loop.

**Code:**
```js
const tasks=[async()=>1,async()=>2];
for(const t of tasks) await t();
```

---

## 36. Handling API errors
**Theory:**
Always wrap fetch calls in try/catch or catch promise rejection to handle network errors.

**Code:**
```js
try{
  const res=await fetch(url);
} catch(e){ console.log(e); }
```

---

## 37. Retrying async operations
**Theory:**
Retry mechanism attempts async operation multiple times on failure.

**Code:**
```js
async function retry(fn,times){
  for(let i=0;i<times;i++){
    try{ return await fn(); } catch{}
  }
}
```

---

## 38. Using finally with promises
**Theory:**
`finally` runs regardless of promise fulfillment or rejection, useful for cleanup.

**Code:**
```js
Promise.resolve(1).finally(()=>console.log('Done'));
```

---

## 39. Async error bubbles
**Theory:**
Errors inside async functions bubble up and must be caught to prevent unhandled rejection warnings.

**Code:**
```js
async function f(){ throw 'err'; }
f().catch(console.log);
```

---

## 40. Mixing async/await with then
**Theory:**
You can combine await with traditional then chains for flexibility.

**Code:**
```js
async function f(){
  const data=await fetch(url).then(res=>res.json());
}
```
# 06. JavaScript Asynchronous – 50 Interview Questions with Detailed Explanations (Continued)

---

## 41. Async iteration with arrays
**Theory:**
Use `for await...of` to handle async operations inside array iteration.

**Code:**
```js
const urls = ['url1','url2'];
async function fetchAll(){
  for await(const url of urls){
    console.log(await fetch(url));
  }
}
```

---

## 42. Converting callback to promise
**Theory:**
Promisify callback functions for modern async handling.

**Code:**
```js
function oldFunc(cb){ setTimeout(()=>cb(null,'data'),1000); }
const newFunc = () => new Promise((res,rej)=> oldFunc((err,data)=> err?rej(err):res(data)));
```

---

## 43. Async error propagation in chains
**Theory:**
Errors thrown in async functions propagate through promise chains unless caught.

**Code:**
```js
async function f(){ throw 'error'; }
f().catch(console.log);
```

---

## 44. Parallel vs sequential execution
**Theory:**
`Promise.all` for parallel, `for await` loop for sequential execution.

**Code:**
```js
await Promise.all([fetch(url1),fetch(url2)]); // parallel
for(const url of urls){ await fetch(url); } // sequential
```

---

## 45. Using AbortController with fetch
**Theory:**
Cancel fetch requests to save resources or abort on timeout.

**Code:**
```js
const controller = new AbortController();
fetch(url,{signal:controller.signal});
controller.abort();
```

---

## 46. Handling multiple errors
**Theory:**
`Promise.allSettled` provides results of all promises without stopping on first rejection.

**Code:**
```js
Promise.allSettled([Promise.resolve(1),Promise.reject('err')]).then(console.log);
```

---

## 47. Delay utility with promise
**Theory:**
Use a delay function for timeout-based async tasks.

**Code:**
```js
const delay=ms=>new Promise(res=>setTimeout(res,ms));
await delay(1000);
```

---

## 48. Debouncing async events
**Theory:**
Delay execution of async operations on high-frequency events.

**Code:**
```js
const debounce = (fn,ms)=>{
  let timer;
  return (...args)=>{
    clearTimeout(timer);
    timer=setTimeout(()=>fn(...args),ms);
  }
}
```

---

## 49. Throttling async events
**Theory:**
Limit async function calls per time interval to reduce load.

**Code:**
```js
function throttle(fn,limit){
  let last=0;
  return (...args)=>{
    const now=Date.now();
    if(now-last>=limit){ fn(...args); last=now; }
  }
}
```

---

## 50. Best practices for async code
**Theory:**
- Prefer async/await over nested callbacks
- Handle all errors with try/catch or .catch
- Avoid blocking main thread
- Use Promise.all for parallel tasks
- Use debouncing/throttling for frequent async events

**Code:**
```js
async function fetchData(){
  try{
    const res = await Promise.all([fetch(url1),fetch(url2)]);
  } catch(e){ console.log(e); }
}
```
