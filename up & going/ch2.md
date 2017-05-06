# You Don't Know JS: Up & Going
# Chapter 2: Into JavaScript

## Values & Types
Javascript has typed value, not typed variables. The following built-in types are available:
* `string`
* `number`
* `boolean`
* `null`
* `undefined`
* `object`
* `symbol`

### Typeof
* `typeof null` is an interesting case, because it errantly returns `"object"`, when you'd expect it to return `"null"`.
* `typeof "abc"` returns `"string"`, not `strings`.
* `undefined` including functions that return no values and usage of the `void` operator.

### Objects
* The `object` type refers to a compound value where you can set properties that each hold their own values of any type.
* Properties can accessed with *dot nation*.
* Properties can accessed with *bracket notation*.
* Bracket notation can use `variable` or `string`.
* There are a couple of other value types that you will commonly interact with in JavaScript programs: *array* and *function*.

### Arrays
* An array is an `object` that holds values (of any type) not particularly is named properties/keys, but rather in numerically indexed positions.
* Arrays are special objects, they can also have properties, including the automatically updated `length` property.
* The best and most natural approach is to use `arrays` for numerically positioned values and use `objects` for named properties.

### Functions
* The functions is `object` subtype.
* `typeof` returns `"function"`.

### Built-In Type Methods
* Javascript behaviors exposed as properties and methods that are quite powerful and useful.
* When you use a primitive value, Javascript automatically "boxes" the value to its object wrapper counterpart.
* A `string` value can be wrapped by a `String` object.
* A `boolean` value can be wrapped by a `Boolean` object.

### Comparing Values

* The result of any comparison is a strictly `boolean` value (`true` or `false`), regardless of what value types are compared.

#### Coercion
#### Truthy & Falsy
#### Equality
#### Inequality
