# 12. JavaScript Machine Coding Round – 20 Questions with Solutions

---

## 1. Live Search Bar
**Theory:**
Filter a list of items as user types in input.

**Code:**
```html
<input id='search' placeholder='Search...'/>
<ul id='list'>
  <li>Apple</li>
  <li>Banana</li>
  <li>Cherry</li>
</ul>
<script>
document.getElementById('search').addEventListener('input',function(){
  const filter=this.value.toLowerCase();
  document.querySelectorAll('#list li').forEach(li=>{
    li.style.display=li.textContent.toLowerCase().includes(filter)?'':'none';
  });
});
</script>
```

---

## 2. To-Do List App
**Theory:**
Add, remove, and mark tasks dynamically.

**Code:**
```html
<input id='task'/><button id='add'>Add</button>
<ul id='tasks'></ul>
<script>
const input=document.getElementById('task');
const ul=document.getElementById('tasks');
document.getElementById('add').addEventListener('click',()=>{
  const li=document.createElement('li');
  li.textContent=input.value;
  li.addEventListener('click',()=>li.classList.toggle('done'));
  ul.appendChild(li);
  input.value='';
});
</script>
<style>
.done{text-decoration:line-through;}
</style>
```

---

## 3. Modal Popup
**Theory:**
Open modal on button click and close on outside click.

**Code:**
```html
<button id='open'>Open Modal</button>
<div id='modal' style='display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.5)'>
  <div style='background:#fff;margin:100px auto;padding:20px;width:200px;'>Modal Content</div>
</div>
<script>
const modal=document.getElementById('modal');
document.getElementById('open').addEventListener('click',()=>modal.style.display='block');
modal.addEventListener('click',e=>{ if(e.target===modal) modal.style.display='none';});
</script>
```

---

## 4. Tab Switcher
**Theory:**
Clicking tab shows corresponding content.

**Code:**
```html
<div class='tabs'>
  <button data-tab='1'>Tab 1</button>
  <button data-tab='2'>Tab 2</button>
</div>
<div id='content1'>Content 1</div>
<div id='content2' style='display:none'>Content 2</div>
<script>
document.querySelectorAll('.tabs button').forEach(btn=>{
  btn.addEventListener('click',()=>{
    document.getElementById('content1').style.display=btn.dataset.tab==='1'?'block':'none';
    document.getElementById('content2').style.display=btn.dataset.tab==='2'?'block':'none';
  });
});
</script>
```

---

## 5. Image Slider / Carousel
**Theory:**
Cycle images with next/prev buttons.

**Code:**
```html
<img id='slide' src='1.jpg' width='200'/>
<button id='prev'>Prev</button><button id='next'>Next</button>
<script>
const imgs=['1.jpg','2.jpg','3.jpg'];
let i=0;
const imgEl=document.getElementById('slide');
document.getElementById('next').addEventListener('click',()=>{ i=(i+1)%imgs.length; imgEl.src=imgs[i]; });
document.getElementById('prev').addEventListener('click',()=>{ i=(i-1+imgs.length)%imgs.length; imgEl.src=imgs[i]; });
</script>
```

---

## 6. Dynamic Dropdown
**Theory:**
Generate options and handle selection.

**Code:**
```html
<select id='dropdown'></select>
<script>
const options=['Option 1','Option 2','Option 3'];
const select=document.getElementById('dropdown');
options.forEach(o=>{
  const opt=document.createElement('option');
  opt.value=o; opt.textContent=o; select.appendChild(opt);
});
select.addEventListener('change',()=>console.log(select.value));
</script>
```

---

## 7. Accordion Component
**Theory:**
Expand/collapse sections on click.

**Code:**
```html
<div class='accordion'>
  <h3>Section 1</h3>
  <div class='panel'>Content 1</div>
  <h3>Section 2</h3>
  <div class='panel'>Content 2</div>
</div>
<script>
document.querySelectorAll('.accordion h3').forEach(h=>{
  h.addEventListener('click',()=>{
    const panel=h.nextElementSibling;
    panel.style.display=panel.style.display==='block'?'none':'block';
  });
});
</script>
<style>
.panel{display:none;}
</style>
```

---

## 8. Form Validation
**Theory:**
Validate input fields before submission.

**Code:**
```html
<form id='form'>
  <input id='email' placeholder='Email'/>
  <button type='submit'>Submit</button>
</form>
<script>
document.getElementById('form').addEventListener('submit',e=>{
  e.preventDefault();
  const email=document.getElementById('email').value;
  if(!email.includes('@')) alert('Invalid email');
  else alert('Valid');
});
</script>
```

---

## 9. Theme Switcher (Dark/Light Mode)
**Theory:**
Toggle page styles dynamically.

**Code:**
```html
<button id='theme'>Toggle Theme</button>
<script>
document.getElementById('theme').addEventListener('click',()=>{
  document.body.classList.toggle('dark');
});
</script>
<style>
.dark{background:#333;color:#fff;}
</style>
```

---

## 10. Counter Increment/Decrement
**Theory:**
Increment/decrement number dynamically.

**Code:**
```html
<button id='dec'>-</button><span id='count'>0</span><button id='inc'>+</button>
<script>
let count=0;
const span=document.getElementById('count');
document.getElementById('inc').addEventListener('click',()=>span.textContent=++count);
document.getElementById('dec').addEventListener('click',()=>span.textContent=--count);
</script>
```

---
# 12. JavaScript Machine Coding Round – 20 Questions with Solutions (Continued)

---

## 11. Dynamic Table Creation
**Theory:**
Generate a table from JSON data dynamically.

**Code:**
```html
<table id='table'></table>
<script>
const data=[{name:'John',age:30},{name:'Jane',age:25}];
const table=document.getElementById('table');
data.forEach(obj=>{
  const row=document.createElement('tr');
  Object.values(obj).forEach(val=>{
    const td=document.createElement('td'); td.textContent=val; row.appendChild(td);
  });
  table.appendChild(row);
});
</script>
```

---

## 12. Drag-and-Drop List Reordering
**Theory:**
Reorder list items using mouse events.

**Code:**
```html
<ul id='list'><li draggable='true'>Item 1</li><li draggable='true'>Item 2</li></ul>
<script>
let dragSrc=null;
document.querySelectorAll('#list li').forEach(item=>{
  item.addEventListener('dragstart',e=>dragSrc=item);
  item.addEventListener('drop',e=>{
    e.preventDefault();
    const parent=dragSrc.parentNode;
    parent.insertBefore(dragSrc,item.nextSibling);
  });
  item.addEventListener('dragover',e=>e.preventDefault());
});
</script>
```

---

## 13. Filterable Product List
**Theory:**
Filter items by category dynamically.

**Code:**
```html
<input id='filter'/><ul id='items'><li data-cat='fruit'>Apple</li><li data-cat='veg'>Carrot</li></ul>
<script>
document.getElementById('filter').addEventListener('input',function(){
  const val=this.value.toLowerCase();
  document.querySelectorAll('#items li').forEach(li=>{
    li.style.display=li.dataset.cat.includes(val)?'':'none';
  });
});
</script>
```

---

## 14. Resizable Div / Box
**Theory:**
Allow a div to be resized by dragging its corner.

**Code:**
```html
<div id='box' style='width:100px;height:100px;background:red;resize:both;overflow:auto;'></div>
```

---

## 15. Tooltip on Hover
**Theory:**
Show info when hovering over an element.

**Code:**
```html
<button id='btn'>Hover me</button>
<div id='tip' style='display:none;position:absolute;background:#333;color:#fff;padding:5px;'>Tooltip</div>
<script>
const btn=document.getElementById('btn'), tip=document.getElementById('tip');
btn.addEventListener('mouseenter',e=>{tip.style.display='block'; tip.style.left=e.pageX+'px'; tip.style.top=e.pageY+'px';});
btn.addEventListener('mouseleave',()=>tip.style.display='none');
</script>
```

---

## 16. Auto-complete Input
**Theory:**
Suggest options as user types.

**Code:**
```html
<input id='auto'/><ul id='suggestions'></ul>
<script>
const list=['Apple','Banana','Cherry'];
const input=document.getElementById('auto');
const ul=document.getElementById('suggestions');
input.addEventListener('input',()=>{
  ul.innerHTML='';
  list.filter(item=>item.toLowerCase().includes(input.value.toLowerCase()))
    .forEach(item=>{const li=document.createElement('li'); li.textContent=item; ul.appendChild(li);});
});
</script>
```

---

## 17. Infinite Scroll / Load More
**Theory:**
Load more items when user scrolls near bottom.

**Code:**
```html
<div id='container' style='height:200px;overflow:auto;'></div>
<script>
const container=document.getElementById('container');
let i=0;
function load(){for(let j=0;j<20;j++){const div=document.createElement('div'); div.textContent='Item '+i++; container.appendChild(div);}}
load();
container.addEventListener('scroll',()=>{if(container.scrollTop+container.clientHeight>=container.scrollHeight) load();});
</script>
```

---

## 18. Countdown Timer
**Theory:**
Display a countdown from specified seconds.

**Code:**
```html
<div id='timer'></div>
<script>
let time=10;
const div=document.getElementById('timer');
const interval=setInterval(()=>{
  div.textContent=time--;
  if(time<0) clearInterval(interval);
},1000);
</script>
```

---

## 19. Sticky Navigation Bar
**Theory:**
Make navbar stick to top when scrolling.

**Code:**
```html
<div id='nav' style='background:#333;color:#fff;padding:10px;'>Nav</div>
<div style='height:1000px'>Content</div>
<script>
const nav=document.getElementById('nav');
const sticky=nav.offsetTop;
window.addEventListener('scroll',()=>{
  if(window.pageYOffset>=sticky) nav.style.position='fixed';
  else nav.style.position='static';
});
</script>
```

---

## 20. Image Upload Preview
**Theory:**
Preview image before upload.

**Code:**
```html
<input type='file' id='file'/><img id='preview'/>
<script>
document.getElementById('file').addEventListener('change',e=>{
  const file=e.target.files[0];
  const reader=new FileReader();
  reader.onload=()=>document.getElementById('preview').src=reader.result;
  reader.readAsDataURL(file);
});
</script>
```

