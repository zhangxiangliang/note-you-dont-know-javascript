# You Don't Know JS: Up & Going
# Chapter 2: Into JavaScript

## Variables
* An identifier must start with `a`-`z`, `A`-`Z`, `$`, or `_`. It can then contain any of those characters plus the numerals `0`-`9`.
* `Reserved words` and `Javascript` keywords can't use as variables name.

### Function Scopes
* use `var` keyword to declare a variable that will belong to the current function scope, or the global scope if at the top level outside of any function.

#### Hoisting
* when a `var` declaration is conceptually "moved" to the top of its enclosing scope.
* We do with the variable call appearing before its formal declaration.

#### Nested Scopes
* When you declare a variable, it is available anywhere in that scope, as well as any lower/inner scopes.
* Always formally declare your variables.
* In ES6 *lets* you declare variables to belong to individual blocks (pairs of `{ .. }`), using `let` keyword.

## Conditionals
* `if..else..if` statements.
* sometime use `switch..case..defalut` replace `if..else..if`.
* sometime use `? :` replace a single `if..else`.

## Strict Mode
* We should use it for all your programs.
* In strict mode is disalloing the implicit auto-global variable declaration from omitting the `var`.
* Not only will strict mode keep your code to a safer path, and not only will it make your code more optimizable, but it also represents the future direction of the language.

## Functions As Values
* a function value should be thought of as an expression, much like any other value or expression
* make a variable is called *anonymous*.
* make a variable is reference to the function.

### Immediately Invoked Function Expressions (IIFEs)
* The outer `( .. )` that surrounds the `(function IIFE(){ .. })` function expression is just a nuance of JS grammar needed to prevent it from being treated as a normal function declaration.

### Closure
* closure as a way to "remember" and continue to access a function's scope (its variables) even once the function has finished running.

#### Modules
* The most common usage of closure in JavaScript is the module pattern. Modules let you define private implementation details (variables, functions) that are hidden from the outside world, as well as a public API that *is* accessible from the outside.
```
Module.User = () => {
    let username, password
    return {
        login: (user, pw) => {
            username = user
            password = pw
        }
    }
}
var xiaoer = Module.User()
xiaoer.login('xiaoer', '123456')
```

## `this` Identifier
* `this` is related to "object-oriented patterns," in JS `this` is a different mechanism.
* If a function has a `this` reference inside it, that `this` reference usually points to an `object`. But which `object` it points to depends on how the function was called.

## Prototypes
* The simplest way to illustrate it is with a built-in utility called `Object.create(..)`.

## Old & New
### Polyfilling
* The word "polyfill" is an invented term used to refer to taking the definition of a newer feature and producing a piece of code that's equivalent to the behavior, but is able to run in older JS environments.

### Transpiling
* `void 0` (aka `undefined`)
* Babel
* Traceur

## Non-JavaScript
* So far, the only things we've covered are in the JS language itself.
* The reality is that most JS is written to run in and interact with environments like browsers.
* A good chunk of the stuff that you write in your code is, strictly speaking, not directly controlled by JavaScript.
