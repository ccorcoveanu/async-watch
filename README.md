[![Build Status](https://travis-ci.org/wiresjs/async-watch.svg?branch=master)](https://travis-ci.org/wiresjs/async-watch)
  
# async-watch

AsyncWatch is a small library for watching javascript/node.js objects. It uses Object.defineProperty which makes it compatible with most browsers. 

## Features

 * Asynchronous execution (Changes are triggerd on requestAnimationFrame)
 * Nested object watching
 * Restoring watchers after objects are destroyed
 * No dirty hacks
 * Suitable for angular-like frameworks
 * Good test coverage
 
## Install

For browser:

    bower install async-watch --save
    
For Node.js projects
  
    npm install async-watch --save

## Examples

```js
var AsyncWatch = require('async-watch').AsyncWatch; // not needed for browsers
var obj = {}; // creating an empty object
AsyncWatch(obj, 'a.b.c', function(value){
    console.log('set', value);
});
// You can pass an array as well
//AsyncWatch(obj, ['a', 'b', 'c'])
```
 
 As you can see here, we start with an empty object. AsyncWatch will set a watcher on property "a", which knows about its descendands
 
 ```js
  obj.a = {
   b : {
    c : 1
   }
  };
  obj.a.b.c = 2;
  obj.a.b.c = 3;
 ```
 
 The output will look like this:
 
 ```js 
 set undefined
 set 3
 ```
 
First set happens when AsyncWatch is initialized, after that the program waits for the next available frame to trigger changes.
 
 
## Contribution
 Contribution is greatly appreciated! Please, run tests before submitting a pool request.  
 
### Known issues
 https://github.com/wiresjs/async-watch/blob/master/test/corner_case.js#L54
 
 
 
