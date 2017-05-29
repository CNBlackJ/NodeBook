# Scope

## Node.js中的数据类型导致了Object的传递性。

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

## 解决方法
知道导致这种问题的原因，拿自然就很容易找到解决的方案。
- 使用第三方包（如：immutable.js）
- 当使用传入的对象时，保证新建一个一样的对象，然后再进行操作
	- `Array`可以采用`Array.concat()`进行新建一个；
	- `Object`可以采用`Object.assign()`进行新建一个；
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