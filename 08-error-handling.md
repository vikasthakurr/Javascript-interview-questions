# 08. JavaScript Error Handling & Debugging – 50 Interview Questions with Detailed Explanations (Completed)

---

## 43. Try/catch for nested functions
**Theory:**
Catch errors from nested function calls without breaking the main flow.

**Code:**
```js
function nested(){ throw new Error('Nested error'); }
try{ nested(); } catch(e){ console.log(e.message); }
```

---

## 44. Using optional chaining to prevent errors
**Theory:**
`?.` prevents runtime errors when accessing properties of null/undefined.

**Code:**
```js
console.log(obj?.prop?.sub);
```

---

## 45. Handling JSON parsing errors
**Theory:**
Wrap JSON.parse in try/catch to catch malformed JSON.

**Code:**
```js
try{ JSON.parse('invalid'); } catch(e){ console.log(e.message); }
```

---

## 46. Handling Type coercion errors
**Theory:**
Check types before operations to prevent implicit coercion errors.

**Code:**
```js
if(typeof val==='number'){ val += 1; } else { console.log('Invalid type'); }
```

---

## 47. Using finally for cleanup
**Theory:**
Ensure cleanup actions like closing files or clearing timers.

**Code:**
```js
try{ risky(); } catch(e){ console.log(e); } finally{ clearTimeout(timer); }
```

---

## 48. Handling multiple errors in async
**Theory:**
Use Promise.allSettled to catch multiple promise errors without stopping execution.

**Code:**
```js
Promise.allSettled([Promise.resolve(1),Promise.reject('fail')]).then(console.log);
```

---

## 49. Using error boundaries in frameworks
**Theory:**
React and other frameworks use error boundaries to catch errors in component trees.

**Code:**
```js
// React example
class ErrorBoundary extends React.Component { ... }
```

---

## 50. Best practices for error handling
**Theory:**
- Always catch errors where appropriate
- Log useful context
- Separate synchronous and asynchronous handling
- Avoid silent failures without logging
- Use tools like ESLint, Sentry, or unit tests

**Code:**
```js
try{
  riskyOperation();
} catch(e){
  console.error('Error:', e);
}