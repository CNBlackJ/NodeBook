# ES6

- `let` & `const`
	- 作用域: 使用这两个关键字定义的变量作用域可以往内层传递，而不能往外层传递。
	```js
	for(let i = 0; i < 10; i++){
		console.log(i);
	};
	console.log(i); // undefined
	```
	- `const`定义的变量是值不可更改的
	```js
	const name = 'J.C';
	name = 'SmallWhite'; // Assignment to constant variable.
	```
	- `let`定义的变量可更改
	```js
	let age = 10;
	age = 12; // good
	```

- spread operator(`...`)
	- 复制数组
	```js
	const a = [1, 2, 3];
	const b = [...a];
	a.push(4);
	console.log(a); // [1, 2, 3, 4]
	console.log(b); // [1, 2, 3]
	```
	- 合并数组
	```js
	const a1 = [1, 2, 3, 4];
	const a2 = [5, 6, 7, 8];
	const c = [...a1, ...a2];
	console.log(c);
	```