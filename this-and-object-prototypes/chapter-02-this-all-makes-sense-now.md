# You Don't Know JS: *this* & Object Prototypes
# Chapter 2: `this` All Makes Sense Now!

## Call-site
* `call-site`: the location in code where a function is called, not where it's declared.
* The stack of functions that have been called to get us to the current moment in execution.
* The call-site we care about is in the invocation before the currently executing function.
* Can use browser see the call-site, In the above snippet, you could have set a breakpoint in the tools for the first line of the function, or simply inserted the `debugger;`.


## Nothing But Rules
### Default Binding
* The rule as the default catch-all rule when none of the other rules apply.
* If `strict mode` is in effect, the global object is not eligible for the the *default binding*, so the `this` is instead set to `undefined`.
* If the contents of `foo()` are not running in `strict mode`; the `strict mode` state of the call-site of `foo()` is irrelevant.

### Implicit Binding
* The rule to consider is: does the call-site have a context object, also referred to as an owning or containing object, though *these* alternate terms could be slightly misleading.
* Only the top/last level of an object property reference chain matters to the call-site.

#### Implicitly Lost
* One of the most common frustrations that `this` binding creates is when an *implicitly bound* function loses that binding, which usually means it falls back to the *default binding*, of either the global object or `undefined`, depending on `strict mode`.
* Even though `bar` function appears to be a reference to `obj.foo`, it's really just another refeerence to `foo` itself.

### Explicit Binding
* functions have `call(...)` and `apply(...)` methods. (In their `[[Prototype]]`).
* `call` and `apply` take first parameter, an object to use for the `this`.
* If you pass a simple primitive value (if type `string`, `boolean`, or `number`) as the `this` binding, the primitive value is warpped in its object-form (`new String(...)`, `new Boolean(...)`, or `new Number(...)`).This is often referred to as "boxing".
* With respect to `this` binding, `call(...)` and `bind(...)` are identical. They do behave differently with their additional parameters.
* But a variation pattern around *explicit binding* actually does the trick.

#### Hard Binding
* common methods

```js
function foo() {
    console.log(this.a);
};
var obj = { a : 2 };
var bar = () => foo.call(obj);

bar.call(window); // 2, so that it cannot be overriden.
```

* The most typical way to wrap a function with a *hard binding* creates a pass-thru of any arguments passed and any return value received.
```
bar = (...arguments) => foo.apply(obj, arguments)
```

* Another way to express this pattern is to create a re-usable helper.
```
bind = (fn, obj) => (...arguments) => fn.apply(obj, arguments)
```

* Since *hard binding* is such a common pattern, it's provided with a built-in utility as of ES5: `Function.prototype.bind`.

#### API Call "Contexts"
* Many libraries's functions, and indeed many new built-in functions is the JavaScript language and host environment, provide an optional parameter, usually called "contexts".
* These various functions almost certainly use *explicit binding*

### `new` Binding
* In JavaScript, constructors are **just functions** that happen to be called with the `new` operator in front of them.
* They are not attached to classes, nor are they instantiating a class. They are not even special types of functions.
* They're just regular functions that are, in essence, hijacked by the use of `new` in their invocation.
* When a function is invoked with `new` in front of it, otherwise known as a constructor call, the following things are done automatically:
    1. a brand new object is created (asa, constructed) out of thin air.
    2. the newly constructed object is `[[Prototype]]`-linked.
    3. the newly constructed object is set as the `this` binding for that function call.
    4. unless the function returns its own alternate `object`, the `new`-invoked function call will automatically return the newly constructed object.

## Everything In Order
### Determining `this`

1. Is the function called with `new` (**new binding**)? If so, `this` is the newly constructed object.
2. Is the function called with `call` or `apply` (**explicit binding**), even hidden inside a `bind` *hard binding*? If so, `this` is the explicitly specified object.
3. Is the function called with a context (**implicit binding**), otherwise known as an owning or containing object? If so, `this` is *that* context object.
4. Otherwise, default the `this` (**default binding**). If in `strict mode`, pick `undefined`, otherwise pick the `global` object.

That's it. That's *all it takes* to understand the rules of `this` binding for normal function calls. Well... almost.

## Binding Exceptions

### Ignored `this`
1. If you pass `null` or `undefined` as a `this` binding parameter to `call`, `apply` or `bind`, those values are efeectively ignored, and instead the *deafult binding* rule applies to the invocation.

2. Why would you intentionally pass something like `null` for a `this` binding?
    * It quite common to use `apply(...)` for spreading out arrays of values as parameters to a function call `foo.apply(null, [1,2])`, in ES6 `foo(...[1,2])` equals `foo(1,3)`.
    * Use `bind(..)` can curry parameters (pre-set values), which can be very helpful.

3. use `null` is a hidden "danger", when a function does make a `this` reference, the `default binding` rule means it might inadvertently reference the `global` object.

#### Safer `this`
* If we always pass a DMZ object for ignored `this` bindings we don't think we need to care about, we're sure any hidden/unexpected usage of `this` will be restricted to the empty object, which insulates our program's `global` object from side-effects.
* Since this object is totally empty, I personally like to give it the variable name `ø`.
* Set `ø` up as totally empty is `Object.create(null)`.
* `Object.create(null)` is similar to `{ }`, but without the delegation to `Object.prototype`, so it's "more empty" than just `{ }`.
* `foo.bind(ø, 2)`

### Indirection
* The *result value* of the assignment expression `p.foo = o.foo` is a reference to just the underlying function object. The effective call-site is just `foo()`, not `p.foo()` or `o.foo()` as you might expect. Per the rules above, the *default binding* rule applies.

### Softening Binding
* `hard-binding` greatly reduces the flexibility of a function, preventing manual `this` override with either the `implicit binding` or even subsequent `explicit binding` attempts.
* we can use `soft-binding utility provided here works similarly to the built-in ES5 `bind(..)`. It wraps the specified function in logic that checks the `this` at call-time and if it's `global` or `undefined`, uses a pre-specified alternate *default* (`obj`). Otherwise the `this` is left untouched. It also provides optional currying.

## Lexical `this`
* arrow-function does not use the 4 rules.
* While arrow-functions provide an alternative to using `bind(..)` on a function to ensure its `this`, which can seem attractive, it's important to note that they essentially are disabling the traditional `this` mechanism in favor of more widely-understood lexical scoping.
* If you find yourself writing `this`-style code, but most or all the time, you defeat the `this` mechanism with lexical `self = this` or arrow-function "tricks", perhaps you should either:
    1. Use only lexical scope and forget the false pretense of `this`-style code.
    2. Embrace `this`-style mechanisms completely, including using `bind(..)` where necessary, and try to avoid `self = this` and arrow-function "lexical this" tricks.

## Review
* Four rules can be applied to the call-site, in `this` order of precedence:
    1. Called with `new`? Use the newly constructed object.
    2. Called with `call` or `apply` (or `bind`)? Use the specified object.
    3. Called with a context object owning the call? Use that context object.
    4. Default: `undefined` in `strict mode`, global object otherwise.
* Be careful of the `default binding` rules.If want to "safely" ignore a `this` binding, a "DMZ" object like `ø = Object.create(null)` is a good placeholder value that protects the `global` object from unintended side-effects.
* ES6 arrow-functions use lexical scoping for `this` binding, which means they adopt the `this` binding from its enclosing function call. They are essentially a syntactic of `self = this` in pre-ES6 coding.
