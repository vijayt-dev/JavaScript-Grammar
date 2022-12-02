## 2 Chrome Console
### 2.0.1 Beyond Console Log

**copy(obj) function**

Copying JSON representation of an existing object to your copy buffer.

```javascript
let x = { prop1: 1, prop2: 2, method: function(){} }
copy(x)
```

Now the JSON is in your copy-paste buffer, you can paste it into any text editor.
JSON string format does not support methods, only properties.

### 2.0.2 console.dir

It shows object properties and methods.

```javascript
let x = { prop1: 1, prop2: 2, method: function(){} }
console.dir(x)
```

### 2.0.3 console.error

It print error message

```javascript
console.error("Error")
```

### 2.0.4 console.time() and console.timeEnd()

You can track the amount of time between function calls. This can be helpful when optimizing code:

```javascript
console.time()
let arr = new Array(10000)
for (let i = 0; i < arr.length; i++){
	arr[i] = new Object()
}
console.timeEnd()
```

### 2.0.5 console.clear

It clear the console messages in screen.

```javascript
console.clear()
```

## 3 Welcome To JavaScript

### 3.1 Entry Point

Every computer program has an entry point.
You can start writing your code directly into script tags. But this means it will be executed instantly and simultaneously as the script is being downloaded into the browser, without concern for DOM or other media.
This can create a problem because your code might be accessing DOM elements
before they are fully downloaded from the server.
You may want to wait until the DOM tree is fully available.

**DOMContentLoaded**

To wait on the DOM event, add an event listener to the document object. The name of the event is DOMContentLoaded.

```html
<html>
<head>
<title>DOM Loaded.</title>
<script type="text/javascript">
function load(){
console.log("DOM Loaded.")
}
document.addEventListener("DOMContentLoaded", load)
</script>
</head>
<body>
</body>
</html>
```

**.readyState**

```html
<html>
<head>
<title>DOM Loaded.</title>
<script type="text/javascript">
function load(){
console.log("DOM Loaded.")
}
if(document.readyState == "loading"){
document.addEventListener("DOMContentLoaded", load)
} else{
load()
}
</script>
</head>
<body>
</body>
</html>
```

**window.onload**

You can wait until all images and similar media have been fully downloaded:

```html
<html>
<head>
<title>Window Media Loaded.</title>
<script type="text/javascript">
window.onload = function(){
	console.log("All Loaded")
}
</script>
</head>
<body>
</body>
</html>
```
**Import**

import (and export) keyword to import variables, functions and classes from an external file.

*mouse.js*

```javascript
export function Mouse() {
	this.x = 0
	this.y = 0
}
```

```html
<html>
<head>
<title>Import Module</title>
<script type="module">
import { Mouse } from "./mouse.js"
let mouse = new Mouse()
</script>
</head>
<body>
</body>
</html>
```

### 3.2 Strict Mode

The strict mode operate in strict operating context.
Without strict mode, certain statements might not generate an error at all - even if they are not allowed.

```javascript
"use strict";
var variable = 1
delete variable // syntaxError
```

### 3.3 Literal Values

**What is Literal Value?**
Literal is a value. You can combine literals using operators.

```javascript
// Add two number literals to produce 7:
5 + 2; // 7
```

**Types of literal values**

- numeric literal
- string literal
- array literal
- object literal
- boolean literal

you also add [] + {} literal

```javascript
[] + {} // '[object Object]'
```

Each literal value usually has a construction function

| typeof  | constructor  |
| ------------ | ------------ |
| number  |  Number() |
| string  | String()  |
|  object([]) |  Array() |
| object({})  | Object()  |
| boolean | Boolean()  |
| function | Function()  |

**What is typeof?**

The **typeof(value)** function can be used to determine type of the literal value. You can also use **typeof** as stand-alone keyword without parenthesis: **typeof x**.

**Number(1) vs new Number(1)**

You can instantiate a value using constructor function associated with the type of that value.

```javascript
1 + 2 //3
Number(1) + Number(2) //3
new Number(1) + new Number(2) //3
1 + Number(2) + new Number(4) //7
```

### 3.4 Variables

**What is variables?**

Variables is a location used to store values.
Variable declaration is definition + assignment
Keywords for defining variables include: var, let and const.

```javascript
var a = 10
let b = 20
const c = 30
```

**What is dynamic typing?**

Dynamic typing is dynamically re-assigned to a value of another type in later.

### 3.5 Passing Values By Reference

JS assigns values by reference without making a copy of the original value.
A chain of references without a single copy of original value

```javascript
let x = {p:1}
let y =x
x.p = 2
console.log(y.p) //2
```

### 3.6 Scope Quirks

**Quirk 1 - let and const inside function vs. global variable**

A variable defined using let or const keywords inside a function cannot coexist with global variable of the same name.

```javascript
let a = "global a"
let b = "global b"

function x(){
	console.log(b) // global b
	console.log(a) // ReferenceError
	let a = 1
}
x()

// ReferenceError will happen if local variable a is defined inside the function body using either let or const keywords
```

**Quirk 2  - var latches onto window/this object, let and const don't**

When variables are defined using var keyword they become attached to window object, but variables defined using let (and const) are not.

## 4 Statements
### 4.0.1 Evaluating Statements

var, let or const keywords return undefined because they behave only as value assignments.
Statements usually produce a value other return undefined.

### 4.0.2 Expressions

Here is an expression: 1 + 1 that produces the value of 2

```javascript
1 + 1 //2
```

## 5 Primitive Types

JavaScript has 7 primitive types: 
1. null
2. undefined
3. number
4. bigint
5. string
6. boolean
7. symbol

null & undefined none constructor

**ValueOf() Method**

valueOf() method returns instance object value.

### 5.0.1 boolean

| typeof  | constructor  |
| ------------ | ------------ |
| boolean  |  new Boolean() |

### 5.0.2 null

| typeof  | constructor  |
| ------------ | ------------ |
| object  |  none |

### 5.0.3 undefined

| typeof  | constructor  |
| ------------ | ------------ |
| undefined  |  none |

### 5.0.4 number

| typeof  | constructor  |
| ------------ | ------------ |
| number  |  new Number() |

### 5.0.5 bigint

| typeof  | constructor  |
| ------------ | ------------ |
| bigint  |  new Bigint() |

### 5.0.6 typeof

```javascript
typeof 10
typeof 10n
```

### 5.0.7 string

| typeof  | constructor  |
| ------------ | ------------ |
| string  |  new String() |

### 5.0.7 string

| typeof  | constructor  |
| ------------ | ------------ |
| string  |  new String() |

### 5.0.8 Template Strings

String defined the backticks quotes.
Back-tick cannot be used to define an object-literal property name.
JSON format requires double quotes around object’s property names (back-ticks won’t do any good here either, without generating an error):

```javascript
let apples = 10
console.log(`There are ${apples} apples in the basket.`)
```

### 5.0.9 Symbol

| typeof  | constructor  |
| ------------ | ------------ |
| symbol  |  none |

The Symbol primitive provides a way to define a completely unique key.

Symbol doesn't have a constructor and cannot be initialized using new keyword.

```javascript
let sym = new Symbol('sym') // TypeError
```

Symbol will create a new symbol with a unique ID:

```javascript
let sym = Symbol('sym') // Symbol created
```

```javascript
Symbol('sym')  === Symbol('sym') // false
```

Whenever you call Symbol(’sym’) a unique symbol is created. The comparison is made between two logically distinct IDs and therefore evaluates to false.

Symbols can be used to define private object properties. This is not the same
as regular (public) object properties. However, both public and private properties created with symbols can live on the same object:

```javascript
let  sym1 = Symbol("id")
let person = {
	[sym1]: 1,
	value: 20
}
console.log(person)
```

Private (symbol-based) properties are hidden from Object.entries, Object.keys and other iterators (for example for...in loop)

```javascript
let  sym1 = Symbol("id")
let person = {
	[sym1]: 1,
	value: 20
}
console.log(Object.entries(obj)) // ["value":20]
```

In addition symbol properties are also hidden from JSON.stringify method

```javascript
console.log(JSON.stringify(obj))
```

But symbols can be exposed via Object.getOwnPropertySymbols method:

```javascript
console.log(Object.getOwnPropertySymbols(obj))
```

**Global Symbol Registry**

There is a global registry for symbols, that can be accessed using methods Symbol.for and Symbol.keyFor.

```javascript
let sym = Symbol.for("age")
let bol = Symbol.for("age")
obj[sym] = 20
obj[bol] = 25
console.log(obj[sym]) // 25
```

### 5.0.10 Executing Methods On primitive Types

Parenthesis operator gives access a member method or property.
A literal is just a literal value. By accessing its properties, it turns into a reference to the object instance so you can execute object methods on that value.

```javascript
1.toString() // this will freeze execution flow
(1).toString()//1
("hello").toUpperCase() //"hello"
new Number(1).toString() //1
```
**Chaining Methods**
Chain multiple methods using the dot operator.

```javascript
"hello".toUpperCase().substr(1,4) // "ello"
```

## 6 Type Coercion Madness

**What is coercion?**

Coercion is the process of converting a value from one type into another.

### 6.0.1 Examples of Type Coercion

Let's say that it is false because two instances of [] are not the same, because JavaScript == operator tests objects by reference and not by value

```javascript
[] == [] // false
let a = []
a == a // true
```
The unary plus and minus operators force the value to a number. if the value is not a number, NaN is generated:

```javascript
const s = "text"
console.log(-s) // NaN
```

But when unary minus (-), unary plus (+) is applied to a number, it produces expected value:

```javascript
const a = 1
console.log(-a) //-1

const b = 1
console.log(+b) //1
```

### 6.0.2 Adding Multiple Values

```javascript
1 + 1 + 1 + 2 + "" // "5"
```

### 6.0.3 Operator Precedence

Some operators take precedence over others. What this means is that multiplication will be evaluted before addition.

```javascript
1 + 1 + 1 + 2 * "" // "0"
```

After multiplication, the numbers 1 + 1 + 1 will be added up to produce 3. Finally: 3 + 0 will evaluate to 3.

### 6.0.4 String To Number Comparison

```javascript
1 == "1" //true
1 == 1 //true
1 == "a" //false
```

### 6.0.5 Operator Precedence & Associativity Table

There are roughly 20 operator precedence levels. Parenthesis () overrides the natural order.
Associativity flows in either left-to-right or right-to-left direction: it determines the order of the operation, usually for operators that require more than one value.

### 6.0.6 L-value and R-value

**Assignment Operator**

The assignment operator takes the R-value and transfers it over to L-value, which is usually a variable identifier name
L = R

**Arithemetic Addition Operator**

But the arithmetic addition operator takes the L-value and adds R-value to it.
L + R 

### 6.0.7 null vs undefined

null primitive is not an object doesn't have a built in constructor.
null as a unique type for explicitly assigning a "nothing" or "empty" value to a variable.
If the value is unkown at the time of variable definition it is always best to use null instead of undefined.

## 7 Scope
### 7.0.1 Scope

Scope is simply the area enclosed by {} brackets.

There are 3 unique scope types
1. Global Scope
2. Block Scope
3. Function Scope

Event callback functions follow the same rule but slightly different.
Loops also have their own block scope.
A variable defined in global scope. It becomes available anywhere in your program(inner block, function etc.

**Hoisting**

Hoisting simply means placed on top of.
Hoisting is limited to variables defined using var keyword and function name.
Variables defined var keyword inside function-level scope are not hoisted.
It is possible to assign an anonymous function expression to a variable name.
That anonymous functions that were assigned to variable names are not hoisted unlike named functions.
JavaScript hoists variables and functions. Functions are hoisted first. Then variables


### 7.1.2 Scope Visibility Differences

**No Difference In Global Scope**

When variables are defined in global scope there is no differences between var, let and const in terms of scope visibility. They all propagate into inner block-level, function-level and event callback scopes.
Keywords let and const limit variable to the scope in which they were defined.

**Function Scope**

All variable types, including var remain limited to their scope.
You cannot access variables outside of the function scope in which they were defined regardless of which keyword was used.

**Closures**

A function closure is a function trapped inside another function.
let It provides automatic privacy for variables defined in block-level scope.

**In Classes**

Class methods let or var or const only create a local variable to that scope. It cannot be accessed outside of the method in which it was defined.

### 7.1.3 const

The const keyword is distinct from let and var.
It’s still possible to change values of a more complex data structure such as Array or objects, even if variable was defined using const.

### 7.1.4 const and Arrays

Changing a value in the const array is still allowed.
You just can't assign any new objects.

### 7.1.6 Dos and Dont's

Do not use var unless for some reason is not good software design.
Do use let and const instead of var.
Do use const to define constants.

## 8 Operators
### 8.0.1 Arithmetic

| operator  | name  |
| ------------ | ------------ |
| +  |  Addition |
| -  |  Subtraction |
| *  |  Multiplication |
| /  |  Division |
| %  |  Modulus |
| ++ |  Increment |
| --  |  Decrement |

### 8.0.2 Assignment

| operator  | name  |
| ------------ | ------------ |
| =  |  Assignment |
| +=  |  Addition |
| -=  |  Subtraction |
| *= |  Multiplication |
| /=  |  Division |
| %= |  Modulus |

### 8.0.3 String

| operator  | name  |
| ------------ | ------------ |
| =  |  Assignment |
| +=  |  Concatenation |
| +  |  Addition |

### 8.0.4 Comparison

| operator  | name  |
| ------------ | ------------ |
| ==  |  equality |
| ===  |  equality of value and type |
| !=  |  inequality |
| !==  |  inequality of value and type |
| >  |  greater than |
| <  |  less than |
| >=  |  greater or equal |
| <=  |  less or equal |

### 8.0.5 Logical

| operator  | name  |
| ------------ | ------------ |
| &&  |  Logical AND |
|    |  Logical OR |
| !  |  Logical NOT |

### 8.0.6 Bitwise

| operator  | name  |
| ------------ | ------------ |
| &  |  Bitwise AND |
|    |  Bitwise OR |
| ^  | Bitwise XOR |
| ~ |  Bitwise NOT |
| << |  Left Shift |
| >>  | Right Shift |

###8.0.7 typeof

The typeof operator is used to check the type of a value.

`typeof 1`

### 8.0.8 Ternary (?:)

The ternary operator is like an inline if-statement. It does not support {} brackets or multiple statements.

```javascript
let number = 1
let result = number > 0 ? "positive" : "negative"
console.log(result)
```

### 8.0.9 delete

The delete keyword can be used to delete an object property.

```javascript
let obj = {prop1:"value1",prop2:"value2"}
console.log(obj) // {prop1:"value1",prop2:"value2"}
delete obj.prop2
console.log(obj) //{prop1:"value1"}
```

### 8.0.10 in

The in operator can be used to check if a property name exists in an object.

```javascript
"c" in {"a":1,"b":2,"c":3} // true
```

The in operator with arrays, will check if an index exists.

```javascript
0 in ["a","b","c"] // true
```

You can check for properties on built-in data types. The length property is native to all arrays.

```javascript
"length" in [] // true
```

## 9 ...rest and ...spread
### 9.0.1 Rest Properties

The ...rest  refer to a larger number of items by extracting them from a single function parameter name. 
The single ...rest parameter is
assumed to contain one or more arguments passed to the function:

```javascript
let arr = [1,2,3,4,5]
function print(...value){
console.log(value) 
}
print(arr)
```

### 9.0.2 Spread Properties

Spread as an opposite of rest.
It can help you extract parts from an object.

```javascript
let arr = [1,2,3,4,5]
function print(val1,val2,val3,val4,val5){
console.log(val1,val2,val3,val4,val5) // 1,2,3,4,5
}
print(...arr)
```

### 9.1 Destructuring Assignment

Destructuring assignment can be used to extract multiple items from arrays and objects and assign them to variables.

```javascript
[a,b] = [10,20]
console.log(a,b) // 10 20
```

```javascript
[a,b,...rest] = [30,40,50,60,70]
console.log(a,b)
console.log(rest)
```

Destructuring is often used to extract object properties to a matching name:

```javascript
let { oranges } = { oranges : 1}
console.log(oranges) // 1
```

Destructuring is not implicitly recursive, second-level objects are not scanned:

```javascript
let { oranges } = { apples:1,inner:{oranges:2}}
console.log(oranges) // undefined
```

It is possible to destructure and rename at the same time:

```javascript
let { automobile: car} = {automobile:"Tesla"}
console.log(car) // Tesla
```

**Merging objects with ...spread**

You can use ...spread syntax to easily merge two or more objects:

```javascript
let a = {p;1,q:2,m:()=>{}}
let b = {r:3,s:4,n:()=>{}}
let c = {...a,...b}
console.log(c) // {p;1,q:2,m:f,r:3,s:4,n:f}
```
## 10 Closure

**What is Closure?**
Closure enables you to keep  a reference to all local function variables after were found after the function exited.

```javascript
function outerFunction(outerVar){
	function innerFunction(innerVar){
		console.log(innerVar)
	}
}

let fun = outerFunction(10)
fun() // 10
```

### 10.0.1 Arity
Arity is the number of arguments a function takes

```javascript
function f(a,b,c){
	let arity = f.length;
	console.log(arity) // 3
}
```

### 10.0.2 Currying

In JavaScript functions are expressions. This also means a function can return
another function. Currying
is a pattern that immediately evaluates and returns another function expression.
A curried function can be constructed by chaining closures by defining and immediately returning all inner functions at the same time.

```javascript
let planets = function(a) {
	return function(b) {
		return a + " " + b
	}
}

let favoritePlanets = planets("Jupiter")
favoritePlanets("Earth") // "Jupiter Earth"
```

Currying in anonymous function

```javascript
let planets = (a) => (b) => a + " " + b
planets("Venus")("Mars") // "Venus Mars"
```

## 11 Loops
### 11.1 for loops

For loops require 3 statements separated by two semicolons, which can be any
legal JavaScript statement, a function call, or even an empty statement.
You’ll often use the following pattern in basic implementations: 1) initialize
counter 2) test condition and 3) increment or decrement counter.

```javascript
let counter = 0
for(let i = 0; i < 10; i++)
	counter++
console.log(counter) // 10
```

**Continue**
You can skip an iteration step by using continue keyword

```javascript
for(let i = 0; i < 3; i++){
	if (i == 1)
		continue
	console.log(i) // 0 2
}
```

**Break**
You can break out of a for loop by using break keyword

```javascript
for(let i = 0; i < 3; i++){
	console.log("loop") // loop
	break;
}
```

**Label**
A statement can be labeled when a label_name is prepended to statement.

```javascript
let c  = 0
mark: for(let i = 0; i < 5; i++){
	inner: for(let j = 0; j < 5; j++){
		c++;
		if(i == 2)
			break mark
	}
	console.log(c) // 11
}
```

### 11.2 for...of Loop

for of loop can iterate over each in arrays or object properties

#### for...of and Generators
A generator – a special type of
function with star * character appended to the function* keyword.

When a generator function is called, the multiple yield statements inside it do not execute at the same time, as you would normally expect.

```javascript
function* generator(){
	yield 1
	yield 2
	yield 3
}

for(let value of generator())
	console.log(value) // 1 2 3
```

```javascript
function* generator(){
	yield 1
	yield 2
	yield 3
}
let gen = generator()
console.log(gen.next().value) //1
```

#### 11.2.2 for...of and Strings

Strings are iterable

```javascript
let string = "text"
for(let value of string)
	console.log(value)
```

#### 11.2.3 for...of and Arrays

```javascript
let array = [0,1,2]
for(let value of array)
	console.log(value)
```

#### 11.2.4 for...of and Objects

for...of loops work only with iterable values. An object is not an iterable. (It
has enumerable properties.) One solution is to convert the object to an iterable first before using it in a for...of loop.

#### 11.2.5 for...of loops and objects converted to iterables

Some built in Object methods .keys, .values or entries.

```javascript
let enumerable = { prop1 : 1, method: () => {}}

for(let key of Object.keys(enumerable))
	console.log(value)
// prop1 method

for(let value of Object.values(enumerable))
	console.log(value)
// 1 () => {}

for (let entry of Object.entries(enumerable))
	console.log(entry)

// (2) ["prop1",1]
// (2) ["method",f()]
```

### 11.3 for...in Loops
for...in loops work with enumerable object properties. It’s a much more elegant solution for iterating through Object properties.

```javascript
let object = { prop1 : 1, method: () => {}}

for(let value in object)
	console.log(value, object[value])
	// 1 () => { }
```

### 11.4 While Loops

A while loop will iterate for an indefinite number of times until the specified condition (there is only one) evaluates to false.

```javascript
let c = 0
while (c++ < 5)
	console.log(c) // 1 2 3 4 5
```

## 12 Arrays
### 12.0.1 Array.sort
sort() function sorts values as strings.
Then Strings converted to Character code utf 16 set.
Sort return the value based on three condition:

- a > b  -> -1  a
- a < b -> 1 b
- a === b -> 0 a and b

```javascript
let arr = [1,10,-1,100,80]
arr.sort(function(a,b){
	return a - b
}) // -1,1,10,80,100
```

### 12.0.2 Array.forEach

The forEach method will execute a function for every item in the array.
Each iteration step receives 3 arguments value, index, object.

```javascript
let fruit = ["pear","banana","orange"]
fruit.forEach((value,index) => {
	console.log(value) // pear 0,  banana 1, orange 2
}) 
```

### 12.0.3 Array.every

The method every will return true if the value of every single item in the array satisfies the condition specified in its function argument:

Return value: boolean

Array.every does not modify the original array. The value inside the function is a copy, not a reference to the value in the original array:

```javascript
let fruit = ["pear","banana","orange","apple"]
let res = fruit.every(function(value){
    return value.length > 2 
})
console.log(res) // true
```

### 12.0.4 Array.some

Some returns true when immediately returns true without having to check the rest of the values.

Every returns false when immediately returns false without having to check the rest of the values.

Return value: boolean

```javascript
let numbers = [0,10,2,3,4,5,6,7]
let condition = value => value < 10
let some = numbers.some(condition)
let every = numbers.every(condition)

console.log(some) // true
console.log(every) // false
```
Note: try not to think of some as an "opposite" of every. In some cases they return the same result on the same data set.

### 12.0.5 Array.filter

The array consisting only of items that passed a condition.

```javascript
let numbers = [0,10,2,3,4,5]
let filtered = numbers.filter(function(value){
    return value < 10
})
console.log(filtered) // [0,2,3,4,5]
```

### 12.0.6 Array.map

A copy of the original array with modified values.

```javascript
let numbers = [0,10,2,3,4,5]
let res = numbers.map(function(value){
    return value = value + 1
})
console.log(res) // [1,11,3,4,5,6]
```

### 12.0.7 Array.reduce

Reduce iterate over a value return single value.
The accumulator value adds all numbers.
That reduce is the father of filter and map. Anything you can do with filter and map can be done with reduce.

```javascript
let numbers = [1,2,3,4,5]
let res = numbers.reduce(function(a,b){
    return a + b
},0)
console.log(res) // 15
```

### 12.0.10 Array.flat()

Flattening a multi-dimensional array

```javascript
let multi = [1,2,[3,4],[5,6,[7,8]]]
multi.flat(2)
console.log(multi) // 1 2 3 4 5 6 7 8
```

### 12.0.11 Array.flatMap()

Flat the return array in the map

```javascript
let array = [1,2,3,4,5]
let arr = array.map(x => [x,x*2])
console.log(arr) //  1,2,2,4,3,6,4,8,5,10
```

## 13 Functions
### 13.1 Functions

A function is a block of code designed to perform a particular task.

#### 13.1.1 Function Anatomy

function keyword followed by its name  parenthesis containing a list of parameter name (a,b,c) and the function body enclosed in brackets.

```javascript
function greeting(message,greetingText = "Hi"){
	return greetingText + " "+ message
}
let greet = greeting("How are you!")
console.log(greet) // Hi How are you!
```

#### 13.1.2 Anonymous Functions

Nameless or anonymous functions can be defined by using the same syntax but skipping the function name.

```javascript
let arr = [1,2,3,4,5]
let arrReduce = arr.reduce(function(total,value,index,array){
    return total + value
},0)
console.log(arrReduce) // 15
```

#### 13.1.3 Assigning Functions To Variables

Anonymous functions can be assigned to a variable, making them named functions again.

```javascript
let greet = function(message,greetingText = "Hi"){
	console.log(greetingText + " "+ message)
}
greet("How are you!") // Hi How are you!
```

### 13.2 Origin of this keyword

The this keyword refers to an object.

```javascript
function print(){
	console.log(this) /*
Window {0: global, window: Window, self: Window, document: document, name: '', location: Location, …}
*/
}
print() 
```

## 14 Higher-order Functions

A higher-order function is a function that either takes a function as one of its parameters or returns a function or both.

## 15 Arrow Functions
**Arrow Functions**

Arrow functions were introduced in ES6 and provide a slim syntax for creating function expressions.

```javascript
() => {};
```

Arrow function can assign them to a variable name.

```javascript
let fun_1 = () => {};

// Call arrow function by its name
fun_1()
```

**return keyword:**

```javascript
let fun_2 = {} => { return 1;}

fun_2(); // 1
```
**return value without using return keyword**

```javascript
let fun_3 = () => 1;

fun_3(); // 1
```

**Parameter without ()**

```javascript
let expression = e => e;

expression(1); // 1
```

### 15.0.1 Arrow Function Anatomy

Arrow functions do not have array-like arguments object. They also cannot be used as constructors.

**Arguments**
Pass arguments to an arrow function via parameters.

```javascript
let x = (arg1,arg2) => { console.log(arg1,arg2); };
x(1,2) // 1, 2
```

**No this binding**

Arrow functions do not bind this keyword. this equals in the outer scope.

**No arguments object**

The arguments object does not exist in arrow function scope, you will get a reference error if you try to access it:

```javascript
let a = () => {
	console.log(arguments); // arguments is not defined
}
```

**No Constructor**

You can create and call a function
but you can also use same function as an object constructor – together with new operator – to instantiate an object. The function itself becomes class definition.

For this reason you would often hear it said that in JavaScript all functions are
objects. After ES6 specification introduced arrow functions to the language this statement is no longer true. Arrow functions cannot be used as object constructors.

**When classic and arrow functions are used as event callbacks**

Inside the arrow function’s scope this property points to Window object.
In classic ES5 function this property points to the target element that was clicked.

**Inherited this Context**

```javascript
function Classic(){
let B = () => {
	console.log("Hello B()");
	console.log(this);
}
document.addEventListener("click",B)
}
let object = new Classic(); // Hello B()
[object Classic]
```

A new context is created when using new operator to instantiate an object. Any-thing called from within that object will have its own context.

## 17 Prototype

### 17.0.1 Prototype

When a function is defined two things happen: the function object is created,
because functions are objects. Then, a completely separate prototype object is
created. The prototype property of the defined function will point to it.

```javascript
function Human(name) { }
typeof Human.prototype // "object"
```

Human.prototype will point to the prototype object. This object has another
property called constructor, which points back to the Human function.

Human is a constructor function, used to create objects of type Human.

Prototype property is not available on an instance of an object, only on the
constructor function. On an instance, you can still access prototype via proto ,
but should probably use static method Object.getPrototypeOf(instance) which
returns the same prototype object as proto (in fact proto () is a getter.)

### 17.0.2 Prototype on Object Literal

```javascript
let person = {
	id: 1,
	name:  'John Doe',
}

person.__proto__ // Object {}
person.__proto__.constructor // f Object{}
person.constructor // f Object {}
```

Internally it is wired into prototype as an object of type Object, even though it
wasn’t created using the new operator.

person.__proto__ point to Object.prototype.

### 17.0.3 Prototype Link

When an object is instantiated using new keyword, the constructor function exe-cutes to build the instance of that object.

The instance of an object of type Object has proto property which points to the prototype object of the constructor from which it was instantiated.
This three-way relationship between the Object, secondary prototype object that was created, and the instance of that object with proto pointing to Object’s
prototype.
This pattern represents just one link in a prototype chain of objects.

### 17.0.5 Method look-up

When you call Array.toString() what actually happens is, JavaScript will first look for method toString on the prototype of Array object. But it does not find it there. Next, JavaScript decides to look for toString method on the prototype
property of Array’s parent class: Object.
It finally finds Object.prototype.toString() and executes it.

### 17.1 Parenting

#### 17.1.2 constructor property

The constructor property of Object class points to Function.
The constructor property of Function class points to Function.

#### 17.1.3 Function

Function is the constructor of all object types.

1. Object()
2. Function()
3. Array()
4. Number()
5. String()
6. Custom()

## 19 Events

### Events

Events are functions executed at the time when a specific action occurs.

Two types of events:
1. Browser events.
2. Synthetic events.

### 19.0.1 Browser Events

Built-in browser events are already pre-determined and executed by the browser when an action occurs. You don’t need to create them yourself, only to intercept them. When browser window changes size, a resize event is automatically dispatched.

### 19.0.2 Synthetic Events
#### Event Object

```javascript
let startEvent = new Event("start");
document.addEventListener("start",function (event){
},false)
```

#### dispatchEvent

Once addEventListener fucntion is executed. The browser will be continuously listening for the "start" event to occur. But the callback remains dormant until event is actually dispatched using the dispatchEvent method.

```javascript
document.dispatchEvent(startEvent);
```
The dispatchEvent method actually triggers our custom ”start” event.

#### removeEventListener

Event listeners take memory and can affect performance of your program if there are too many listeners running at the same time. If we no longer need to listen for the event it’s a good idea to call removeEventListener method.

```javascript
function callback() {
	console.log("Clicked");
}
document.addEventListener("click",callback);
document.removeEventListener("click",callback);
```

Anonymous functions cannot be used to remove event listeners, so the following call will not remove the event listener.

```javascript
document.removeEventListener("click",function() { });
```
Whenever you use an anonymous function expression, it will occupy a new location in memory. This means removeEventListener will not be able to locate it among already existing callbacks.

#### CustomEvent Object

Events can carry additional data, specifying details of the event.

```javascript
let event = new CustomEvent("map",{
	detail: {
		x: 123,
		y: 234
	}
});

let callback = function(event) {
	console.log(event);
};

document.addEventListener("map",callback);
document.dispatchEvent(event)
```
#### Event Capture and Event Bubbling

Event Bubbling down to top.
Event Capturing top to down also known as trickling down.
If you have Event capture as well as Event bubbling. W3C tells the event capture to event bubbling.
It takes lot of memory.

```javascript
document.querySelector("#grandparent").addEventListener("click", () => {
    console.log("Grandparent Clicked")
},false)

document.querySelector("#parent").addEventListener("click", () => {
    console.log("Parent Clicked")
},true)
document.querySelector("#child").addEventListener("click", () => {
    console.log("Child Clicked")
},false)
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>JS</title>
    <style>
      div {
        min-width: 100px;
        min-height: 100px;
        padding: 30px;
        border: 1px solid black;
      }
    </style>
  </head>
  <body>
    <h1>JavaScript Web Page</h1>
    <p id="para">This is a demo paragraph from this web page.</p>
    <button id="clickMe">Click</button>

    <div id="grandparent">
      <div id="parent">
        <div id="child">
        </div>
      </div>
    </div>
  <script src="app.js"></script> 
  </body>
</html>
```
### 19.0.4 setTimeout

It execute the callback function after the delay.
Resetting the timeout using clearTimeout function will cancel the event and
prevent it from occurring in the future.

```javascript
let id = setTimeout(function() {
	console.log("Hello");
},1000);
clearTimeout(id);
```

### 19.0.5 setInterval

The setInterval function works exactly like setTimeout, except it will continue executing the callback function for an indefinite number of times at a time interval specified as its second argument.

```javascript
let id = setInterval(function() {
	console.log("Hello");
},1000);
clearInterval(id);
```

## 21 Event Loop

### How JS Engine Executes the Code using Call Stack

One call stack at a time 1 thing can do.
Inside a JS Engine have call stack.

### Main Job of the Call Stack

Whatever comes in the call stack it execute and it doesn’t wait for anything.

### How does JavaScript perform async tasks

The call stack doesn’t have a timer.

### Behind the scenes in Browser

Components

1. Call Stack
2. JS Engine
3. Browser
4. URL
5. Video
6. Web server
7. Timer
8. Bluetooth
9. Geo location
10. Local Storage

### Web APIs

The JavaScript engine access to web APIs through window global object.

### How setTimeout Works behind the scenes in Browsers

```javascript
console.log("Start")
setTimeout(function cb(){
    console.log("Callback")
},5000)
console.log("End")
```

1. Print Start through console web API
2. It register callback function in the Web API and start timer through setTimeout Web API
3. Print End through console web API
4. Global Execution context is pop in call stack
5. While the timer is finished the call back function execute in the call stack

### Event Loop & CallBack Queue or Task Queue

When the timer is finished the callback function put into the callback queue.
The event loop check it have anything in the callback queue if have the it take it from the callback queue put into the call stack.
The call stack execute the callback function.
The callback queue is cleared.
The call stack is also cleared when the function is executed.
Event loop mediator between the call stack and callback queue.

### How Event Listeners Work

```javascript
console.log("Start")
setTimeout(function cb(){
    console.log("Callback")
},5000)
console.log("End")
```

1. Print Start through console web API
2. It register callback function in the Web API
3. Print End through console web API
4. When the user click the callback function put into the callback queue.
5. The event loop check the call stack is empty if empty the callback queue check it for then callback function put into the call stack
6. Callback queue is vanished.

### Why do we need Event Loop

Lot more events happen the callback queue execute one after another

### How fetch() function works

This not work as setTimeout and DOM APIs.

```javascript
console.log("Start");

setTimeout(function cbT() {
	console.log("CB SetTimeout");
}, 5000);
fetch("https://api.netflix.com")
.then(function cbf() {
	console.log("CB Netflix");
});
console.log("End");
```

1. Print Start through console web API
2. It register callback function and start timer in the Web API
3. Fetch get data from the API then call the callback function and register in the Web API
4. Print End through console web API
5. While fetch is get data from the API it store in the microTask Queue it has higher priority, as same as callback queue
6. While setTimeout function is finished is store in the callback queue
7. The event loop first execute the microTask queue then callback queue
8. Then microTask and callback queue is vanished

### What are MicroTasks in JS

Whatever comes in callback function in promise and mutation observer it comes in microTask queue.

Mutation Observer keeps on check in mutation on DOM tree it execute the callback function.

### Starvation of Functions is in Callback Queue

If callback function create another microTask in microTask queue so on. The callback queue wait until the microTask queue is finished. The wait is called starvation.

## 22 Call Stack

The call stack is a place to keep track of currently executing functions. As your code executes, each call is placed on the call stack in order in which it appears in your program. Once the function returns it is removed from the call stack.

### 22.1 Execution Context

The call stack is a stack of execution contexts.

#### What is Execution Context?

It is contains the code that's currently running, and everything that aids in its execution.
Note that the execution context is pointed to by this keyword in each scope. Not only function-scope either. Block-scope also carries with it a link to execution context via this keyword.

It is just not used to access its properties or methods. Instead, it establishes a link between sections of code flow across multiple scopes.

#### Root Execution Context

When your program opens in a browser, an instance of a window object is created automatically. This window object becomes the root execution context, because it’s the first object instantiated by the browser’s JavaScript engine itself. The window object is the execution context of global scope – they refer to the same thing. The window object is an instance of Window class.

### 22.2 Execution Context In Code

#### 22.2.1 Window / Global Scope

The window object is created,  A new lexical environment is created. It contains variable envrionment for that scope - a place in memory for storing your local variables.

A new execution context is created when main window object is instantiated. The this keyword points to the window object

#### 22.2.2 The Call Stack

The call stack keeps track of function calls. If you call a function from context of the global scope, a new entry will be placed ”on top” of the current context. The newly created stack will inherit execution context from the previous environment.

#### 22.2.3 .call(), .bind(), .apply()

##### .call()
The JavaScript Function call() method is used to call a function.

```javascript
function print() {
    console.log(this.firstName + " " + this.lastName);
  }
const person1 = {
  firstName:"John",
  lastName: "Doe"
}
person.fullName.call(person1); //John Doe
```

##### .apply()
It same as call() but different is The apply() method accepts arguments in an array:

```javascript
function print() {
    console.log(this.firstName + " " + this.lastName + "," + city + "," + country);
  }
const person1 = {
  firstName:"John",
  lastName: "Doe"
}
person.fullName.call(person1,  ["Oslo", "Norway"]); // John Doe,Oslo,Norway
```

##### .bind()
bind is a method on the prototype of all functions in JavaScript. It allows you to create a new function from an existing function, change the new function's this context, and provide any arguments you want the new function to be called with.

```javascript
function print() {
    console.log(this.firstName + " " + this.lastName);
  }
const person1 = {
  firstName:"John",
  lastName: "Doe"
}
let fullName = person.fullName.bind(person1); // John Doe
```

#### 22.2.4 Stack Overflow

A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.
Stack Overflow occurs when the memory required to build the call stack exceeds the address space allocated for the stack. This amount is determined and managed internally by the browser.
