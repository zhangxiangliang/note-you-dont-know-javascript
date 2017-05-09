# You Don't Know JS: *this* & Object Prototypes
# Chapter 1: `this` Or That?

## Why `this`?
* Let's try to illustrate the motivation and utility of `this`.
* This code snippet allows the functions to be re-used against multiple context objects, rather than needing a separate version of the function for each object.
* The `this` mechanism provides a more elegant way of implicitly "passing along" an object reference, leading to cleaner API design and easier re-use.
* If not use `this`, you could have explicitly passed in a context object.

## Confusions
### Itself
* all functions in JavaScript are objects!
* `this` is not to refers to the function itself.

### Its Scope
* `this` does not, in any way, refer to a function's `lexical scope`.

## What's `this`?
* `this` is not an author-time binding but a runtime binding. It is contextual based on the conditions of the function's invocation. `this` binding has nothing to do with where a function is declared, but has instead everything to do with the manner in which the function is called.
* When a function is invoked, an activation record, otherwise known as an execution context, is created. This record contains information about where the function was called from (the call-stack), *how* the function was invoked, what parameters were passed, etc. One of the properties of this record is the `this` reference which will be used for the duration of that function's execution.

## Review
* `this` is actually a binding that is made when a function is invoked, and *what* it references is determined entirely by the call-site where the function is called.
