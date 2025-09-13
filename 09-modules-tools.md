# 09. JavaScript Modules, Tooling & Environment – 50 Interview Questions with Detailed Explanations

---

## 1. What are JavaScript modules?
**Theory:**
Modules allow you to split code into reusable, maintainable pieces. Each module can export variables, functions, or classes and import them in other modules.

**Code:**
```js
// utils.js
export function sum(a,b){ return a+b; }

// main.js
import { sum } from './utils.js';
console.log(sum(2,3));
```

---

## 2. CommonJS modules
**Theory:**
Used in Node.js. Exports and imports are done using `module.exports` and `require`.

**Code:**
```js
// utils.js
module.exports.sum = (a,b)=>a+b;

// main.js
const { sum } = require('./utils');
console.log(sum(2,3));
```

---

## 3. Default exports
**Theory:**
Each module can have one default export. Useful for exporting a single main functionality.

**Code:**
```js
// math.js
export default function(a,b){ return a*b; }

// main.js
import multiply from './math.js';
console.log(multiply(2,3));
```

---

## 4. Named exports
**Theory:**
Export multiple values from a module and import only what is needed.

**Code:**
```js
export const a=1; export const b=2;
import {a} from './file.js';
```

---

## 5. Dynamic imports
**Theory:**
Load modules dynamically using `import()` for lazy loading.

**Code:**
```js
import('./utils.js').then(module=> console.log(module.sum(2,3)));
```

---

## 6. Module scope
**Theory:**
Variables and functions inside a module are private unless explicitly exported.

**Code:**
```js
const secret = 42; // private
export const visible = 10;
```

---

## 7. Module caching
**Theory:**
Modules are cached after first load. Subsequent imports retrieve cached version.

**Code:**
```js
import {sum} from './utils.js'; // cached on first import
```

---

## 8. Node.js module resolution
**Theory:**
Node searches for modules in node_modules folder, relative paths, or global paths.

**Code:**
```js
const express = require('express');
```

---

## 9. ES6 vs CommonJS
**Theory:**
ES6 modules use `import/export`, CommonJS uses `require/module.exports`. ES6 supports static analysis and tree-shaking.

---

## 10. Using npm
**Theory:**
Node package manager to install and manage dependencies.

**Code:**
```bash
npm install lodash
```

---

## 11. package.json
**Theory:**
Defines project metadata, scripts, and dependencies.

**Code:**
```json
{
  "name":"my-app",
  "version":"1.0.0",
  "scripts": {"start": "node index.js"}
}
```

---

## 12. Node.js global objects
**Theory:**
`__dirname`, `__filename`, `process`, `global` are globally available in Node.

**Code:**
```js
console.log(__dirname);
console.log(process.env.NODE_ENV);
```

---

## 13. require.cache
**Theory:**
Node caches modules. You can inspect and delete from `require.cache`.

**Code:**
```js
delete require.cache[require.resolve('./utils')];
```

---

## 14. Module patterns
**Theory:**
IIFE and Revealing Module Pattern were used before ES6 to achieve modularity.

**Code:**
```js
const Module = (function(){
  const privateVar=1;
  return { getVar:()=>privateVar };
})();
console.log(Module.getVar());
```

---

## 15. Bundlers (Webpack, Parcel)
**Theory:**
Combine multiple modules into a single file for browsers, allowing code splitting, minification, and optimization.

**Code:**
```js
// webpack.config.js
module.exports = { entry: './index.js', output: { filename: 'bundle.js' } };
```

---

## 16. Transpilers (Babel)
**Theory:**
Convert modern JS code to older versions for browser compatibility.

**Code:**
```bash
babel src --out-dir dist
```

---

## 17. Environment variables
**Theory:**
Store configuration values outside code. Accessible via `process.env` in Node.

**Code:**
```js
console.log(process.env.PORT);
```

---

## 18. Using dotenv
**Theory:**
Load environment variables from a .env file.

**Code:**
```js
require('dotenv').config();
console.log(process.env.DB_HOST);
```

---

## 19. Linting tools
**Theory:**
Static code analysis to enforce coding standards. E.g., ESLint, JSHint.

**Code:**
```bash
eslint index.js
```

---

## 20. Prettier
**Theory:**
Code formatter for consistent code style.

**Code:**
```bash
prettier --write index.js
```

---

## 21. Source maps
**Theory:**
Map minified/transpiled code to original source for debugging.

**Code:**
```js
//# sourceMappingURL=app.js.map
```

---

## 22. Node.js REPL
**Theory:**
Interactive shell to execute JS code in Node.

**Code:**
```bash
node
> console.log('Hello')
```

---

## 23. Using ts-node for TypeScript
**Theory:**
Run TypeScript files directly in Node without compilation.

**Code:**
```bash
ts-node index.ts
```

---

## 24. Import maps (browser)
**Theory:**
Map module specifiers to URLs in browsers.

**Code:**
```html
<script type="importmap">
  {"imports": {"lodash": "https://cdn.com/lodash.js"}}
</script>
```

---

## 25. Module aliasing
**Theory:**
Create shortcuts for module paths to simplify imports.

**Code:**
```js
import utils from '@utils';
```

---

## 26. Tree-shaking
**Theory:**
Remove unused code during bundling to optimize size.

**Code:**
```js
import { usedFn } from './utils.js'; // only usedFn included
```

---

## 27. Hot Module Replacement
**Theory:**
Update modules in browser without full reload.

**Code:**
```js
if(module.hot){ module.hot.accept(); }
```

---

## 28. Using npx
**Theory:**
Run Node packages without global installation.

**Code:**
```bash
npx create-react-app my-app
```

---

## 29. Debugging Node.js
**Theory:**
Use `node inspect` or VSCode debugger to inspect Node applications.

**Code:**
```bash
node --inspect index.js
```

---

## 30. REPL commands
**Theory:**
Commands like `.help`, `.break`, `.clear` help navigate Node REPL.

---

## 31. Module circular dependency
**Theory:**
Modules referencing each other can cause incomplete exports; avoid or resolve carefully.

**Code:**
```js
// A.js imports B.js, B.js imports A.js
```

---

## 32. ES Modules in Node
**Theory:**
Use "type": "module" in package.json to enable ESM.

**Code:**
```json
{"type":"module"}
```

---

## 33. Using top-level await
**Theory:**
Await can be used at module top-level in ES modules.

**Code:**
```js
const data = await fetch('/api').then(res=>res.json());
```

---

## 34. Using import.meta.url
**Theory:**
Get current module URL in ESM.

**Code:**
```js
console.log(import.meta.url);
```

---

## 35. Module bundling vs native modules
**Theory:**
Bundlers allow old browsers to use modules; native modules supported in modern browsers.

---

## 36. Using rollup.js
**Theory:**
Bundler focused on ES modules and tree-shaking.

**Code:**
```js
// rollup.config.js
export default { input:'src/main.js', output:{file:'bundle.js', format:'esm'} };
```

---

## 37. Webpack loaders
**Theory:**
Transform files during bundling, e.g., Babel-loader for JS, CSS-loader for CSS.

**Code:**
```js
module: { rules: [{ test:/\.js$/, use:'babel-loader' }] }
```

---

## 38. Webpack plugins
**Theory:**
Extend webpack capabilities, e.g., HtmlWebpackPlugin.

**Code:**
```js
plugins: [new HtmlWebpackPlugin({template:'index.html'})]
```

---

## 39. Node.js versions and nvm
**Theory:**
Manage Node versions using nvm for compatibility across projects.

**Code:**
```bash
nvm install 18
nvm use 18
```

---

## 40. Bundler source maps
**Theory:**
Enable debugging of bundled code by mapping back to source files.

**Code:**
```js
devtool:'source-map'
```

---

## 41. Lint-staged
**Theory:**
Run linters only on staged files before commit.

**Code:**
```json
"lint-staged": {"*.js": ["eslint --fix"]}
```

---

## 42. Husky
**Theory:**
Git hooks manager, e.g., pre-commit hooks for linting.

**Code:**
```bash
npx husky add .husky/pre-commit "npm test"
```

---

## 43. Using esbuild
**Theory:**
Super fast bundler and minifier.

**Code:**
```bash
esbuild src/index.js --bundle --outfile=dist/bundle.js
```
## 44. Code splitting
**Theory:**
Split code into smaller bundles to load only what is needed, improving performance.


**Code:**
```js
import('./module.js').then(module=>module.init());
```


---


## 45. Tree-shaking in bundlers
**Theory:**
Remove unused code during bundling to reduce bundle size.


**Code:**
```js
import { used } from './utils.js'; // unused code not included
```


---


## 46. Polyfills
**Theory:**
Add support for features missing in older browsers.


**Code:**
```js
import 'core-js/stable';
import 'regenerator-runtime/runtime';
```


---


## 47. Module hot reloading
**Theory:**
Update modules in browser without full reload for faster development.


**Code:**
```js
if(module.hot){ module.hot.accept('./module.js', ()=>console.log('Module updated')); }
```


---


## 48. Cross-platform Node scripts
**Theory:**
Write scripts that work on multiple OS using Node.js and npm scripts.


**Code:**
```json
"scripts": {"start": "node index.js"}
```


---


## 49. Environment-based configuration
**Theory:**
Load different configs based on NODE_ENV for dev, test, and production.


**Code:**
```js
const config = process.env.NODE_ENV==='prod'? prodConfig: devConfig;
```
```