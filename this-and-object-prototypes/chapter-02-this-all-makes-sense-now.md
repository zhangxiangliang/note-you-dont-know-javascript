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
