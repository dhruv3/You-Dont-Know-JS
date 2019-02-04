# Chapter 1
* JS is a compiled language. Unlike others it is not compiled well in advance nor are the results of compilation portable among various distributed systems.
* JavaScript engines don't get the luxury (like other language compilers) of having plenty of time to optimize, because JavaScript compilation doesn't happen in a build step ahead of time, as with other languages.
* JS engines use all kinds of tricks (like JITs, which lazy compile and even hot re-compile, etc.)
* `console.log(a)` => This is a RHS reference, because nothing is being assigned to a here. Instead, we're looking-up to retrieve the value of `a`, so that the value can be passed to `console.log(..)`.
* To decide if its LHS or RHS think like: "who's the target of the assignment (LHS)" and "who's the source of the assignment (RHS)".
* If RHS look up of a varibale fails then Engine throws `ReferenceError`. If LHS look up of a variable fails then Engine creates a new variable in the global scope(provided strict mode is off). 
* `ReferenceError` is Scope resolution-failure related, whereas `TypeError` implies that Scope resolution was successful, but that there was an illegal/impossible action attempted against the result.

# Chapter 2
* In lex scope you are suppose to know your scope and corresponding variable during lex phase(tokenizing). Alternate to lex scope is dynamic scoping.
* There are two ways to cheat or modify lexical scope at run-time: `eval` and `with`
* The `eval(..)` function in JavaScript takes a string as an argument, and treats the contents of the string as if it had actually been authored code at that point in the program. Eg: `eval("var b = 3")` => This `b` will overshadow any `b` declared in outer scopes.
* **Note:** eval(..) when used in a strict-mode program operates in its own lexical scope, which means declarations made inside of the eval() do not actually modify the enclosing scope.
* When engine comes across `eval` and `with` it doesn't do optimizations it would have done. Without these optimizations our code will run slower than usual.

# Chapter 3
* Way of thinking: Take any arbitrary section of code you've written, and wrap a function declaration around it, which in effect "hides" the code.
* You can avoid collisions of variables by using: `Global "Namespaces"` and `Module Management`
* Functions are by no means the only unit of scope. Block-scope refers to the idea that variables and functions can belong to an arbitrary block (generally, any `{ .. }` pair) of code, rather than only to the enclosing function.
*  ES3 specified the variable declaration in the `catch` clause of a `try/catch` to be block-scoped to the `catch` block.
* Declarations made with `let` will **not** hoist to the entire scope of the block they appear in. Such declarations will not observably "exist" in the block until the declaration statement.
* Block scoping helps in `Garbage Collection`.
* Declaring explicit blocks can help Garbage Collector know that things inside this block will not be used after the block ends.

# Chapter 4
* Functions are hoisted first, and then variables.
* While fultiple/duplicate `var` declarations are effectively ignored, subsequent function declarations do **override** previous ones.

# Chapter 5
* Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.
* "Magic" of closures does not `foo()` to be collected by Garbage Collector happen. That inner scope is in fact still "in use", and thus does not go away. 
* `bar()` still has a reference to that scope, and **that reference is called closure**. `bar()` is inside of `foo()` and `foo()` returns `bar` function.
* Example of real life working closure: [link](https://github.com/dhruv3/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch5.md#now-i-can-see). 
* [Creating a closure vs Exercising a closure](https://gist.github.com/amysimmons/af85281f3f794485e8de9dd76fbaa64f#file-closure-md).
* If no closures were available then we would have to create an object and pass it around the functions we were going to call.
* You can create singleton pattern by wrapping the module inside an IIFE. 
* Two "requirements" for the module pattern to be exercised:
	* There must be an outer enclosing function, and it must be invoked at least once (each time creates a new module instance).
	* The enclosing function must return back at least one inner function, so that this inner function has closure over the private scope, and can access and/or modify that private state.
* **ES6 related**: `import` imports one or more members from a module's API into the current scope, each to a bound variable (hello in our case). `module` imports an entire module API to a bound variable (foo, bar in our case). `export` exports an identifier (variable, function) to the public API for the current module.

