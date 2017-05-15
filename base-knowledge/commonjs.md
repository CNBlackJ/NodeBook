# CommonJS

CommonJS是一种模块规范，可以很好的解决污染全局作用域的问题。
```javascript
// dog.js
const dog = 'small white';
module.exports = dog;

// pet.js
const dog = require('./dog');
const pet = dog;
```
- 作用域通过文件来区分，代码运行在文件内；
- 通过`exports` ／ `require`来实现文件之间的变量访问；
- 模块只会加载一次，然后被缓存起来，再次加载时会从缓存中取结果，清除缓存才可以使得模块再次运行；
  - 在代码中修改完后需要重新启动才可以被应用；
- 模块会根据出现的顺序进行加载。
