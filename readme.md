# WebPack
Recap of all features I have learned through Node & LaraveL journey.
First time I have learned was through Jeffrey's way great series at laracast.
But it was based on webpack@2.2 and now we are at 5.7 - different galaxy

free and open-source module bundler for JavaScript
popularized by Instagram announcement and microsoft 
**benefits**
- let us write modue amd compile it for browser 
- support any module format
- handle resources and assets 
- support code spliting and async bunlding 

## 1. Getting Started
```bash
npm init -y
npm install webpack webpack-cli --save-dev
```
**edit package.json**
- setup 2 scripts inside package.json  
- remove main etnry
- add private entry
```json
  "private": true,
"scripts": {
    "webpack": "webpack",
    "dev": "npm run webpack -- --mode development --watch",
    "prod": "npm run webpack -- --mode production",
```

> ./src/index.js 
> ./src/function.js 


```js
// index.js
import {test} from "./function";
console.log(test);

// function.js
export function test()
{
    console.log('hej');
}
```

it will generated distributed file into `.dist/main.js`


## 2. Configuration
version 4 does not require but supports config file  - more efficient

`./webpack.config.js`

```js
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

## 3. Modules are
 webpack transpiles code to browser 

`./src/Notification.js` 

 ```js
 function shoutOut(msg) {
    alert(msg);
}
function log(msg) {
    console.log(msg);
}

export{shoutOut, log};
```

`./src/index.js`
```js
import {log, shoutOut} from "./Notification";
log("webpack 4");
shoutOut("WebPack 5");
``` 