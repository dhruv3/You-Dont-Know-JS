# Chapter 1
* There are two meanings of `this` which are incorrectly assummed. 
	* First: `this` inside of function refers to the function itself.
	* Second: `this` refers to function's scope. It is somewhat correct. To be clear, this does not, in any way, refer to a function's lexical scope.
* You cannot create **bridge** between lexical scopes of two functions. Check [gist](https://gist.github.com/dhruv3/554487d3e9ef1a80a335de1b012e02c4).
* `this` is not an author-time binding but a runtime binding. It is contextual based on the conditions of the function's invocation. `this` binding has nothing to do with where a function is declared, but has instead everything to do with the manner in which the function is called.
* When a function is invoked an execution context is created. This record contains information about where the function was called from (the call-stack), how the function was invoked, what parameters were passed, etc. One of the properties of this record is the `this` reference which will be used for the duration of that function's execution.
* `this` is neither a reference to the function itself, nor is it a reference to the function's lexical scope.
* `this` is actually a binding that is made when a function is invoked, and what it references is determined entirely by the call-site where the function is called.

# Chapter 2
* [Corresponding Gist](https://gist.github.com/dhruv3/c799e122cc5f55b3e2baf55dc88c0ba7)
* Call-Site: the location in code where a function is called (**not where it's declared**).
* There are 4 rules and order of precedence exists in these to determine the correct value of `this`.
* Rule 1: **Default Binding**. Standalone function invocation. If a function is called on its own, foo(), this will be either undefined (if in strict mode) or the global object (if in non-strict mode).
* Rule 2: **Implicit Binding**. `obj.foo();`. Context object(`obj`) which should be used for the function call's `this` binding. **implicitly bound** function sometime lose original binding and default to global binding.
* Rule 3: **Explicit Binding**. Using `call` and `apply` functions to bind `this`. Both functions take an object as first param which is used for `this`.
* Rule 4: **Hard Binding**. ES5 has `bind` function which returns a new function that is hard-coded to call the original function with the `this` context set as you specified. 
* Process when `new` is called:
	1. a brand new object is created (aka, constructed) out of thin air
	2. *the newly constructed object is `[[Prototype]]`-linked*
	3. the newly constructed object is set as the `this` binding for that function call
	4. unless the function returns its own alternate **object**, the `new`-invoked function call will *automatically* return the newly constructed object.
* new binding is more precedent than implicit binding.
* explicit binding is more precedent than implicit binding.

# Chapter 3
* Objects can be created using `literal` format or `constructed` format.
* JS automatically coerces a `"string"` primitive to a `String` object when necessary, which means you almost never need to explicitly create the Object form.
* You *could* use an array as a plain key/value object, and never add any numeric indices, but this is a bad idea because arrays have behavior and optimizations specific to their intended use.
* `Object.assign` creates a shallow copy of non-primitive variables.
* As of ES5, object propertiy descriptor was introduced and it has characterstics: value, writable, enumerable and configurable(means whether or not you can modify the property descriptor).
* `Object.defineProperty` can be used to updated these object descriptors.
* Another thing `configurable:false` prevents is the ability to use the `delete` operator to remove an existing property.
* `Object.preventExtensions()` means no new properties can be added to your object
* `Object.seal()` calls `Object.preventExtensions()`, but also sets configurable to false on every property in the object. This prevents you from adding new properties as well as reconfiguring or deleting them. You can however still modify their values.
* `Object.freeze()` calls `Object.seal()`, but also sets writable to false on every property in the object. This is the highest level of immutability.
* `[[Get]]` operation is performed when property is accessed from an object. If not found it goes up prototype chain.
* `[[Put]]` operation has a 3 step process which is followed by JS.
