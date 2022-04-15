# Reproducing the Error

```
git clone https://github.com/jorge-barreto/cljs-in-cra.git
yarn
npx shadow-cljs watch code
yarn start
```

Run the application to see the error below:

```
ReferenceError: process is not defined
    at Object../node_modules/shadow-cljs/cljs_env.js (cljs_env.js:2:1)
    at Object.options.factory (react refresh:6:1)
    at __webpack_require__ (bootstrap:24:1)
    at fn (hot module replacement:62:1)
    at Object../node_modules/shadow-cljs/main.app.js (cljs_env.js:12505:1)
    at Object.options.factory (react refresh:6:1)
    at __webpack_require__ (bootstrap:24:1)
    at fn (hot module replacement:62:1)
    at Module../src/App.js (logo.svg:34:1)
    at Module.options.factory (react refresh:6:1)
```

In ./node_modules/shadow-cljs/cljs_env.js we can see the bad reference:

```
var CLJS_GLOBAL = process.browser ? (typeof(window) != 'undefined' ? window : self) : global;
```
