# Data type

## 数据类型

#### 基本数据类型（6种）
保存在栈内存的简单数据段，访问方式为按值访问。
- String
- Number
- Boolean
- Null
- Undefined
- Symbol(ES6)

其中null与undefined是特殊的数据类型，`Null`表示值为空，`Undefined`表示没有定义；
Symbol是在ES6新增加的基本数据类型。

```javascript
let m = 1;
```

|栈内存||
|--|--|
| m | 1 |

```javascript
m = 2; // 操作的是变量m中实际保存的值
```
|栈内存||
|--|--|
| m | 2 |

```javascript
let n = m; // 把m复制到n，栈中创建多一个新的变量n,值为m的值1
```
|栈内存||
|--|--|
| m | 1 |
| n | 1 |

```javascript
//然后把m的值2赋予n
m // 1
n // 2
```
|栈内存||
|--|--|
| m | 1 |
| n | 2 |


### 引用数据类型
指保存在堆内存中的对象。访问方式是按引用访问。
也就是，变量中保存的只是一个指针，这个指针指向内存中的另一个位置，该位置保存着对象。

- Object

```javascript
const Pet = new Object(); // 变量保存的是一个指针，指向堆内存中保存的对象。
```
|栈内存|||堆内存|
|--|--|--|--|
|Pet|引用指针|--->|Object|

```javascript
// 操作对象时，需要先从栈内存中读取堆内存地址，然后再找到保存在对内存中的值，再操作。
Pet.name = 'dog';
```
|栈内存|||堆内存|
|--|--|--|--|
|Pet|引用指针|--->|Object{name: 'dog'}|

```javascript
// 复制操作：复制的是栈内存中的指针，复制的指针与原指针指向同一个堆内存中保存的值。
const Animal = Pet;
```
|栈内存|||堆内存|
|--|--|--|--|
|Pet|引用指针|--->|Object{name: 'dog'}|
|Animal|引用指针|___⬆||

```javascript
// 操作的是引用指针指向的Object
Animal.color = 'red';
Pet // { name: 'dog', color: 'red' }
Animal // { name: 'dog', color: 'red' }
Animal === Pet // true
```
|栈内存|||堆内存|
|--|--|--|--|
|Pet|引用指针|--->|Object{name: 'dog',color:'red'}|
|Animal|引用指针|___⬆||