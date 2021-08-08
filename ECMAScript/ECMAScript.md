### ES 2015 (ES6)

#### let, const 

let const 都是作用于块级作用域。

const 被用于声明常量。 

#### class , extends ,  super

```javascript
//class 定义一个 类
//class 之间通过 extends 实现继承
// super 关键字，替代父类的实例
class Animal {
    constructor(){
        this.type = 'animal'
    }
    says(say){
        console.log(this.type + ' says ' + say)
    }
}

let animal = new Animal()
animal.says('hello') //animal says hello

class Cat extends Animal {
    constructor(){
        super()
        this.type = 'cat'
    }
}

let cat = new Cat()
cat.says('hello') //cat says hello

```

#### Arrow function 

写法更简洁。

```javascript
function (i){return i + 1}
(i) => i+1 
```

##### this的指向 

当我们使用箭头函数时，函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。

#### template string (模版字符串)

```javascript
const template = 'template'
let a = `this is a ${template} string`

```



#### destructuring

ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构

```javaScript
const object ={a:'a',b:'b'}
let {a,b} = object

let newObject ={a,b , c:'c'}
```

#### default, rest

default ： function 默认参数

```javascript
function animal(type= 'cat'){
 	console.log(type)
}
animal()   //'cat'
```

rest 

```javascript
function animals(...types){
		console.log(types)
}
```

#### Set Map    

Set数据结构，类似于array, 成员的值都是唯一。

```javascript
cosnt s = new Set()
[2,3,4].forEach(ele=>s.add(ele))
```

- Set.prototype.consructor
- Set.prptotype.size

- Set.prototype.add(value)
- Set.prototype.delete(value)
- Set.prototype.has(value)
- Set.prototype.clear()

Array.from

```javascript
//数组去重
let arr = [3,4,5,5,6]
let newArr = Array.from(new Set(arr))
```



遍历操作

- Set.prototype.keys()
- Set.prototype.values()
- Set.prototype.entries()
- Set.prototype.forEach()

##### WeakSet

于Set 的区别：

1. WeakSet 只能放置对象
2. WeakSet 中的对象都是弱引用，

#### Import  export

#### Promise

### ES 2016

#### Array.proptype.includes()

```javascript
let array = [1,2,3]

array.includes(3) // true
array.includes('3') //false
//
```



#### 指数计算

````javascript
Math.pow(2,2)  //4
2 ** 2   //4
````



### ES 2017

#### String.padding 字符串填充 

 ```javascript
 // .padStart() .padEnd() 字符串填充方式
 
 'let'.padStart(4)    // 'let '
 'let'.padEnd(5)    //'  let'
 ```



Object.entries()       Object.values()     Object.keys()

```javascript
let object = {
   name : 'vino',
   age: 5
}

Object.keys(object)    // ['name','age']
Object.values(object)   //['vino',5]
Object.entries(object)   //[['name' ,'vino'] ,['age', 5]]


```



#### Object.getOwnPropertyDescriptors() 返回对象所有属性描述符

````javascript
const myObj = {
  name: 'Alberto',
  age: 25,
  greet() {
    console.log('hello')
  },
}
Object.getOwnPropertyDescriptors(myObj)
// age:{value: 25, writable: true, enumerable: true, configurable: true}
// greet:{value: ƒ, writable: true, enumerable: true, configurable: true}
// name:{value: "Alberto", writable: true, enumerable: true, configurable: true}

````



#### 在函数列表参数和Object中尾随逗号

语法改变。

```javascript
const  object = {
prop1: 'prop',
prop2: 'propop'
}
```



#### Shared memory(共享内存) and Atomics 

Atomics 不是构造函数，它的所有属性和方法都是静态的(就像 Math 一样) ，因此我们不能将它与新的运算符一起使用，也不能将 Atomics 对象作为函数调用。



#### Async Await 

```javascript
//常见 Promise 
fetch('api.github.com/user/AlbertoMontalesi')
	.then(res=>(res.json()))
	.then(res=>{
	 	consol.log(res)
	}).catch(err=>{console.log(err)})
```

```javascript
function walk(amount) {
	return new Promise((resolve,reject) => {
		if (amount < 500){
			reject('the value is too small')
		}
		setTimeout(()=> resolve(`your walked for ${amount}ms`),amount)
	})
}

// create an async function
async function go() {
  // use the keyword `await` to wait for the response
  const res = await walk(500)
  console.log(res) 
  // 'your walked for 500ms'
  const res5 = await walk(400)
  console.log(res5)
  //Uncaught (in promise) the value is too small
  console.log('finished')
}

go()
```

只能在异步 Async 函数中使用 Await 

Error handing  错误处理

和Promise类似 ，我们使用 try{....}catch(err){....}来补捉Error 

```javascript
async function asyncFunc() {
  	try{
  		let response = await fetch('anyURL')
  	}catch (err){
  		console.log(err)
  	}
}
```



### ES 2018

####  rest/spread syntax 

```javascript
//object 
let a = ['miranda','pentax']
let b = [...a, 'nikon']

let c ={name:'pentax',age:100}
let c = {...c, ...{logo:'nike'}}
```

#### Asynchronous Iteration 异步迭代 

```javascript
const iterables = [1, 2, 3]
async function test() {
  for await (const value of iterables) {
    console.log(value)
  }
}
test()

```

#### Promise.prototype.finally()

Promise结束后的回调函数

```javascript
const myPromise = new Promise((resolve, reject) => {
  resolve()
})
myPromise
  .then(() => {
    console.log('still working')
    return 'still working'
  })
  .finally(() => {
    console.log('Done!')
    return 'Done!'
  })
  .then((res) => {
    console.log(res)
  })
// still working
// Done!
// still working
```

#### RegExp 功能



### ES 2019

#### Array.prototype.flat()  / Array.prototype.flatMap()

Flat() 将递归地压扁数组

``` javascript
const letters = ['a', 'b', ['c', 'd', ['e', 'f']]]

letters.flat()    // ['a' ,'b' ,'c','d', ['e','f']]

letters.flat(Infinity)   // ['a', 'b', 'c', 'd', 'e', 'f']

```



FlatMap() 可以映射并返回新数组中的结果 

```javascript
let greeting = ['Greetings from', ' ', 'Vietnam']
 
greeting.flatMap((x) => x.split(' '))
// ["Greetings", "from", "", "", "Vietnam"]
```



#### Object.fromEntries()

将array键值对转换成object

```javascript
const keyValueArray = [ 
	['key1' ,'value1']
	['key2' ,'value2']
]
const obj = Object.froEntries(keyValueArray)  // {key1: 'value1' ,key2: 'value2'}
```



#### String.trimStart()    / String.trimEnd()

String.trimStart() 从字符串的开头去除空字符，String.trimEnd()从字符串的结尾去除空字符

#### Optional catch binding (可选的补捉绑定)

```javascript
try{ ...} catch(err){...}
//ES2019
try{...} catch{ ....}
```





#### Function.proptotypep.toString()

toString()返回一个function的字符串（甚至包含备注）

#### Symble.prototype.description 



### ES 2020

#### BigInt 

#### 表现最大整数 

```javaScript
let a = 1234567890
let b= 1234567890n

```



#### Dynamic imports  动态导入 

其中按需加载这些逻辑资源都一般会在某一个事件回调中去执行

```javascript
el.onclick = () => {
  import('/modules/my-module.js')
    .then(module => {
      // Do something with the module.
    })
    .catch(err => {
      // load error;
    })
}
```

#### Nullish   空值合并运算符

逻辑操作符，当左侧的操作数为  *null*   或者 *undefined* 返回其右侧操作数，否则返回左侧操作数。

逻辑或操作符 **||** , 会在左侧操作数为 *假值* 时返回右侧操作数

```javascript
const foo = null ?? 'default string'; // default string

let bar = '0' || 45   //45
 
```

#### Optional Chaining 可选链接

可选的链接语法允许您访问深度嵌套的对象属性，而不必担心该属性是否存在。如果它真的存在，那就太好了！如果没有，则返回未定义的。

```javascript
let x ={prop1: {prop2: 200}}

x.props1?.prop2   //200
x.props1?.noPropn?.what    //undefined
```



#### Promise.allSettled

我们知道 Promise.all 具有并发执行异步任务的能力。但它的最大问题就是 **如果参数中的任何一个promise为reject的话，则整个Promise.all 调用会立即终止**

Promise.allSettled跟Promise.all类似, 其参数接受一个Promise的数组, 返回一个新的Promise, **唯一的不同在于, 它不会进行短路**, 也就是说当Promise全部处理完成后,我们可以拿到每个Promise的状态, 而不管是否处理成功。

```javascript
Promise.allSettled([
  Promise.reject({ code: 500, msg: '服务异常' }),
  Promise.resolve({ code: 200, list: [] }),
  Promise.resolve({ code: 200, list: [] })
]).then(res => {
  console.log(res)
  /*
        0: {status: "rejected", reason: {…}}
        1: {status: "fulfilled", value: {…}}
        2: {status: "fulfilled", value: {…}}
    */
  // 过滤掉 rejected 状态，尽可能多的保证页面区域数据渲染
  RenderContent(
    res.filter(el => {
      return el.status !== 'rejected'
    })
  )
})

```

#### String.prototype.matchAll

```javascript
const  regexp = /[a-c]/g
const str = 'abcdefg'
conts iierator = str.matchAll(s)
```

#### globalThis

```javascript
// worker.js
globalThis === self
// node.js
globalThis === global
// browser.js
globalThis === window
```

