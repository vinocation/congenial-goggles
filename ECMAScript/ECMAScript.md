### ES 2015 (ES6)



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

表现最大整数 


