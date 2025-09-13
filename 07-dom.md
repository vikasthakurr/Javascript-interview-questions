# 07. JavaScript DOM & Browser APIs – 50 Interview Questions with Detailed Explanations

---

## 1. What is the DOM?
**Theory:**
DOM (Document Object Model) represents HTML or XML as a tree structure where each element is a node. It allows JS to access and manipulate page content dynamically.

**Code:**
```js
console.log(document.body); // <body> element
```

---

## 2. Selecting elements
**Theory:**
Use `getElementById`, `getElementsByClassName`, `querySelector` and `querySelectorAll` to select elements.

**Code:**
```js
const el = document.getElementById('myId');
const els = document.querySelectorAll('.myClass');
```

---

## 3. Modifying element content
**Theory:**
`textContent` and `innerHTML` allow changing an element’s content.

**Code:**
```js
const el = document.getElementById('demo');
el.textContent = 'Hello World';
el.innerHTML = '<b>Hello</b>';
```

---

## 4. Changing styles
**Theory:**
Modify element styles via the `style` property or CSS classes.

**Code:**
```js
el.style.color = 'red';
el.classList.add('active');
```

---

## 5. Creating elements
**Theory:**
Use `document.createElement` to create new elements and `appendChild` to insert them into DOM.

**Code:**
```js
const div = document.createElement('div');
div.textContent = 'New Div';
document.body.appendChild(div);
```

---

## 6. Removing elements
**Theory:**
Use `removeChild` or `element.remove()` to delete elements from DOM.

**Code:**
```js
const el = document.getElementById('removeMe');
el.remove();
```

---

## 7. Event listeners
**Theory:**
Attach functions to elements to handle events using `addEventListener`.

**Code:**
```js
el.addEventListener('click',()=>console.log('Clicked'));
```

---

## 8. Event object
**Theory:**
The event handler receives an event object containing information about the event.

**Code:**
```js
el.addEventListener('click',(e)=>console.log(e.target));
```

---

## 9. Event delegation
**Theory:**
Attach a single event listener on a parent element to handle events for multiple children, improving performance.

**Code:**
```js
document.body.addEventListener('click',(e)=>{
  if(e.target.classList.contains('btn')) console.log('Button clicked');
});
```

---

## 10. Event bubbling & capturing
**Theory:**
Events propagate from target to root (bubbling) or root to target (capturing). Use third argument in addEventListener to control.

**Code:**
```js
el.addEventListener('click',fn,true); // capturing phase

# 07. JavaScript DOM & Browser APIs – 50 Interview Questions with Detailed Explanations (Continued)

---

## 11. Prevent default behavior
**Theory:**
Use `event.preventDefault()` to prevent the browser’s default action for an event.

**Code:**
```js
const link = document.querySelector('a');
link.addEventListener('click', e => e.preventDefault());
```

---

## 12. Stop event propagation
**Theory:**
`event.stopPropagation()` stops an event from bubbling up or down the DOM.

**Code:**
```js
el.addEventListener('click', e => e.stopPropagation());
```

---

## 13. Input value handling
**Theory:**
Access input values via `value` property.

**Code:**
```js
const input = document.querySelector('input');
console.log(input.value);
```

---

## 14. Form submission handling
**Theory:**
Capture form submission and prevent default to handle via JavaScript.

**Code:**
```js
const form = document.querySelector('form');
form.addEventListener('submit', e => {
  e.preventDefault();
  console.log('Form submitted');
});
```

---

## 15. Class manipulation
**Theory:**
Add, remove, toggle, or check classes using `classList`.

**Code:**
```js
el.classList.add('active');
el.classList.remove('hidden');
el.classList.toggle('open');
```

---

## 16. DOM traversal
**Theory:**
Navigate the DOM tree using properties like `parentNode`, `children`, `nextSibling`, `previousElementSibling`.

**Code:**
```js
const parent = el.parentNode;
const children = el.children;
```

---

## 17. getComputedStyle
**Theory:**
Get the computed styles of an element, including styles from CSS.

**Code:**
```js
const style = window.getComputedStyle(el);
console.log(style.color);
```

---

## 18. innerHTML vs textContent
**Theory:**
`innerHTML` parses HTML tags; `textContent` returns plain text.

**Code:**
```js
console.log(el.innerHTML);
console.log(el.textContent);
```

---

## 19. dataset attributes
**Theory:**
Access custom `data-*` attributes via `dataset`.

**Code:**
```js
const el = document.querySelector('#item');
console.log(el.dataset.id);
```

---

## 20. Creating document fragments
**Theory:**
`DocumentFragment` allows inserting multiple nodes at once for performance improvement.

**Code:**
```js
const frag = document.createDocumentFragment();
const li = document.createElement('li');
li.textContent = 'Item';
frag.appendChild(li);
document.querySelector('ul').appendChild(frag);
```

# 07. JavaScript DOM & Browser APIs – 50 Interview Questions with Detailed Explanations (Continued)

---

## 21. Event delegation for dynamic elements
**Theory:**
Instead of attaching events to each element, attach to a parent to handle dynamically created child elements efficiently.

**Code:**
```js
document.body.addEventListener('click', e => {
  if(e.target.matches('.dynamic-btn')) console.log('Dynamic button clicked');
});
```

---

## 22. Focus and blur events
**Theory:**
`focus` triggers when an element gains focus, `blur` when it loses focus.

**Code:**
```js
input.addEventListener('focus', ()=>console.log('Focused'));
input.addEventListener('blur', ()=>console.log('Blurred'));
```

---

## 23. Keyboard events
**Theory:**
Detect key actions using `keydown`, `keypress`, and `keyup`.

**Code:**
```js
document.addEventListener('keydown', e => console.log(e.key));
```

---

## 24. Mouse events
**Theory:**
Detect mouse interactions like click, dblclick, mouseover, mouseout.

**Code:**
```js
el.addEventListener('mouseover', ()=>console.log('Hovered'));
```

---

## 25. Touch events
**Theory:**
Detect touch interactions on mobile devices using `touchstart`, `touchmove`, `touchend`.

**Code:**
```js
el.addEventListener('touchstart', e=>console.log('Touched'));
```

---

## 26. Scroll events
**Theory:**
Detect scrolling to implement lazy loading or sticky elements.

**Code:**
```js
window.addEventListener('scroll', ()=>console.log(window.scrollY));
```

---

## 27. Resize events
**Theory:**
Detect window resize for responsive adjustments.

**Code:**
```js
window.addEventListener('resize', ()=>console.log(window.innerWidth));
```

---

## 28. Intersection Observer
**Theory:**
Monitor visibility of elements in viewport efficiently.

**Code:**
```js
const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => console.log(entry.isIntersecting));
});
observer.observe(document.querySelector('#target'));
```

---

## 29. localStorage
**Theory:**
Stores key-value data in the browser that persists across sessions.

**Code:**
```js
localStorage.setItem('name','Vikas');
console.log(localStorage.getItem('name'));
```

---

## 30. sessionStorage
**Theory:**
Stores data for the duration of page session; cleared when tab is closed.

**Code:**
```js
sessionStorage.setItem('token','abc');
console.log(sessionStorage.getItem('token'));
```
# 07. JavaScript DOM & Browser APIs – 50 Interview Questions with Detailed Explanations (Continued)

---

## 31. Cookies in JavaScript
**Theory:**
Cookies store small pieces of data on the client. Can be read and set via `document.cookie`.

**Code:**
```js
document.cookie = 'user=Vikas; path=/; expires=Fri, 31 Dec 2025 23:59:59 GMT';
console.log(document.cookie);
```

---

## 32. Detecting online/offline status
**Theory:**
Use `navigator.onLine` and listen to `online`/`offline` events.

**Code:**
```js
window.addEventListener('online', ()=>console.log('Online'));
window.addEventListener('offline', ()=>console.log('Offline'));
```

---

## 33. Geolocation API
**Theory:**
Access user’s location with user consent.

**Code:**
```js
navigator.geolocation.getCurrentPosition(pos=>console.log(pos.coords.latitude,pos.coords.longitude));
```

---

## 34. Clipboard API
**Theory:**
Read from and write to clipboard using async API.

**Code:**
```js
navigator.clipboard.writeText('Hello');
navigator.clipboard.readText().then(console.log);
```

---

## 35. History API
**Theory:**
Manipulate browser history with pushState, replaceState, and handle popstate events.

**Code:**
```js
history.pushState({page:1},'','?page=1');
window.addEventListener('popstate', e=>console.log(e.state));
```

---

## 36. Fetch API for DOM
**Theory:**
Use fetch to get data dynamically and manipulate DOM accordingly.

**Code:**
```js
fetch('/api').then(res=>res.json()).then(data=>document.body.textContent = JSON.stringify(data));
```

---

## 37. Template literals and innerHTML
**Theory:**
Use template literals to dynamically insert data into DOM elements.

**Code:**
```js
const name='Vikas';
el.innerHTML = `<p>Hello ${name}</p>`;
```

---

## 38. Shadow DOM
**Theory:**
Encapsulates DOM and styles, preventing CSS leakage.

**Code:**
```js
const shadow = el.attachShadow({mode:'open'});
shadow.innerHTML = '<p>Shadow DOM</p>';
```

---

## 39. requestAnimationFrame
**Theory:**
Efficiently schedule animations in sync with browser repaint.

**Code:**
```js
function animate(){
  // update animation
  requestAnimationFrame(animate);
}
requestAnimationFrame(animate);
```

---

## 40. MutationObserver
**Theory:**
Observe DOM changes and react dynamically.

**Code:**
```js
const observer = new MutationObserver(mutations=>console.log(mutations));
observer.observe(document.body,{childList:true,subtree:true});
```
# 07. JavaScript DOM & Browser APIs – 50 Interview Questions with Detailed Explanations (Continued)

---

## 41. Custom events
**Theory:**
Create and dispatch custom events to communicate between components.

**Code:**
```js
const event = new CustomEvent('myEvent', {detail:{msg:'Hello'}});
el.dispatchEvent(event);
el.addEventListener('myEvent', e => console.log(e.detail.msg));
```

---

## 42. Window vs Document
**Theory:**
`window` represents the browser window, `document` represents the HTML content inside the window.

**Code:**
```js
console.log(window.innerHeight);
console.log(document.body.scrollHeight);
```

---

## 43. Client vs offset vs scroll properties
**Theory:**
`clientWidth/Height` – visible area, `offsetWidth/Height` – including borders, `scrollWidth/Height` – including overflow.

**Code:**
```js
console.log(el.clientHeight, el.offsetHeight, el.scrollHeight);
```

---

## 44. getBoundingClientRect()
**Theory:**
Returns element position relative to viewport.

**Code:**
```js
console.log(el.getBoundingClientRect().top);
```

---

## 45. Window location
**Theory:**
`window.location` provides current URL info and allows redirects.

**Code:**
```js
console.log(window.location.href);
window.location.href='/newpage';
```

---

## 46. Window scrollTo & scrollBy
**Theory:**
Scroll the window to a specific position or by a certain offset.

**Code:**
```js
window.scrollTo(0,100);
window.scrollBy(0,50);
```

---

## 47. Element scrollIntoView
**Theory:**
Scroll an element into viewport.

**Code:**
```js
el.scrollIntoView({behavior:'smooth'});
```

---

## 48. requestIdleCallback
**Theory:**
Schedule low priority tasks during browser idle periods.

**Code:**
```js
requestIdleCallback(()=>console.log('Idle task'));
```

---

## 49. Navigator API
**Theory:**
Access browser info, user agent, online status, geolocation.

**Code:**
```js
console.log(navigator.userAgent);
console.log(navigator.onLine);
```

---

## 50. Best practices for DOM manipulation
**Theory:**
- Minimize direct DOM updates, batch changes
- Use DocumentFragment for multiple inserts
- Avoid layout thrashing by reading and writing DOM separately
- Use event delegation for dynamic elements
- Prefer `classList` over style manipulation when possible

**Code:**
```js
const frag = document.createDocumentFragment();
for(let i=0;i<10;i++){
  const li=document.createElement('li');
  li.textContent=i;
  frag.appendChild(li);
}
document.querySelector('ul').appendChild(frag);
```
