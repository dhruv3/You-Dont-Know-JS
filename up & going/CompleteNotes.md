# Second Edition
## Ch 1: What is JS?
* JS language is organized: scope/closures, prototypes/objects, and types/coercion.
* 


# Chapter 1
* The JavaScript engine actually compiles the program on the fly and then immediately runs the compiled code.
* For input use the prompt(..) function
* JavaScript uses **dynamic typing** approach, meaning variables can hold values of any type without any type enforcement.
* In JavaScript, each function gets its own scope. Only code inside that function can access that function's scoped variables.

# Chapter 2
* Javascript has typed value and not typed variable.
* Functions are a subtype of objects -- typeof returns "function", which implies that a function is a main type -- and can thus have properties.
* Object Wrapper(String with capital S) that defines the toUpperCase() method on its prototype. JS automatically "boxes" the value to its object wrapper counterpart.
* A `string` value can be wrapped by a `String` object, a `number` can be wrapped by a `Number` object, and a `boolean` can be wrapped by a `Boolean` object. 
* The specific list of "falsy" values in JavaScript:
	* `""` (empty string) 
	* 0, -0, `NaN` (invalid number) 
	* `null`, `undefined` 
	* false
* `==` checks for value equality with coercion allowed, and `===` checks for value equality without allowing coercion. If you can't be certain about the values, use `===`. 
* When comparing non-primitive variables both `==` and `===` comparisons will simply check whether the references match, not anything about the underlying values.
* Arrays are by default coerced to strings by simply joining all the values with commas (,) in between. Eg: `[1,2,3] == "1,2,3" //true`
* If you try to set a variable that hasn't been declared, you'll either end up creating a variable in the top-level global scope. Eg- a = 16; This makes 'a' global variable
* In addition to creating declarations for variables at the function level, ES6 lets you declare variables to belong to individual blocks (pairs of { .. }), using the let keyword.
* Because an IIFE is just a function, and functions create variable scope, using an IIFE in this fashion is often used to declare variables that won't affect the surrounding code outside the IIFE.
* If a function has a `this` reference inside it, that `this` reference usually points to an object. But which object it points to depends on how the function was called.
* Check [this](https://github.com/dhruv3/You-Dont-Know-JS/blob/master/up%20%26%20going/ch2.md#this-identifier) related example.
* Prototype example: 
```js
var foo = {
	a: 42
};

// create `bar` and link it to `foo`
var bar = Object.create( foo );

bar.b = "hello world";

bar.b;		// "hello world"
bar.a;		// 42 <-- delegated to `foo`
```

# Chapter 3
* No notes required
