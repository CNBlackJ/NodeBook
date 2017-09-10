# Scope

## 作用域

### Node.js中的数据类型导致了Object的传递性。

```javascript
const ar = [1, 2, 3];
function showArray(oldAr){
	oldAr.push(4);
	return oldAr;
}
console.log(ar); // [1, 2, 3]
const newAr = showArray(ar);
console.log(ar); // [1, 2, 3, 4]
console.log(newAr); // [1, 2, 3, 4]
```

在上面的例子中，可以看到`ar`的值在进入到`showArray`这个方法之后就发生了值的改变，
一般来说，我们是预期`ar`这个变量进入到方法之后不会被改变。导致这个现象的原因是Node.js
中的基本数据类型是按值访问，而对象（Object / Array）则是按引用访问[见`data-type`这一章节]。

#### 解决方法
知道导致这种问题的原因，那自然就很容易找到解决的方案。
- 使用第三方包（如：immutable.js）
- 当使用传入的对象时，保证新建一个一样的对象，然后再进行操作
	- `Array`可以采用`Array.concat()`进行新建一个；
	- `Object`可以采用`Object.assign()`进行新建一个；
	- `...`: a = [1]; b = [..a]; b.push(2);
 	- 上述例子改进：
	```javascript
		const ar = [1, 2, 3];
		function showArray(oldAr){
			const newAr = [].concat(oldAr);
			newAr.push(4);
			return newAr;
		}
		console.log(ar); // [1, 2, 3]
		const newAr = showArray(ar);
		console.log(ar); // [1, 2, 3]
		console.log(newAr); // [1, 2, 3, 4]
		```

### `const` vs `let` vs `var`

先来看看一个例子：

```javascript
let pet = { name: 'samll_white' }
const weightData = []
for(let age of [10, 20, 30]) {
	var weight = age * 2
	weightData.push(weight)
}
console.log(weight)     // [ 20, 40, 60 ]
console.log(weightData) // 60
console.log(age)        // ReferenceError: age is not defined.
weightData = [1, 2, 3]  // TypeError: Assignment to constant variable.
```

先来看看`let`和`var`
- `var`: 作用域会上浮，也会下沉；该关键字定义的变量可以被重新赋值；例子中weight是在for循环里面被定义的，但是在循环区块外也可以被读取到。
- `let`: 作用域不能上浮，只能下沉；可以被重新赋值；例子中for循环里定义的age，只能在for循环这个区块进行使用。
- `const`: 作用域不能上浮，只能下沉；不能被重新赋值；例子中的weightData
