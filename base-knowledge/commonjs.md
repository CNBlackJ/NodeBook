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
- 模块会根据出现的顺序进行加载；
- 每个模块都会有一个`module`方法，可以使用`module.exports`输出模块接口；
- 每个模块也都有一个`exports`变量，该变量指向`module.exports`。即`exports = module.exports`；
  - `exports`不能输出一个函数；
- 一旦输出了模块内的一个值，则模块内部的改变是影响不了这个值的；

**与CommonJS相对应的还有ES6 import 和AMD规范。**