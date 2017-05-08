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
* Coercion is implicit.
* Coercion is not evil, nor does it have to be surprising.
* You can construct with type coercion are quite sesible and understandable, and can even be used to improve the readability of your code.

#### Truthy & Falsy
* `""`, `0`, `-0`, `NaN`, `null`, `undefined`, `false` (=> falsy).
* `"hello"`, `42`, `true`, `[]`, `{}`, `function foo() {......}` (=> truthy).

#### Equality
* `==`, `===`, `!=` and `!==` (=> equality).
* `===` and `!==` is often called "strict equality".
* `==` and `!=` is often called "loose equality".
* If either value in a comparison could be the `true` or `false` value, avoid `==` and use `===`.
* If either value in a comparison could be of these specific values (`0`, `null`, `""`, or `[]`), avoid `==` and use `===`.
* In all other cases, you're safe to use `==`. Not only is it safe, but in many cases it simplifies your code in a way that improves readability.
* `object`, `function`, `array` comparisons will simply check whether the references match, not anything
about the underlying values.

#### Inequality
* The `<`, `>`, `<=`, and `>=` operators are used for inequality, will be used with ordinally comparable values like `number`s.
* If comparable values is `string` using typical alphabetic rules.
* If comparable values is `string` and only compose by `number`s, will coercion the string to number.
* If comparable between potentially different value types, is when one of the values cannot be made into a valid number.

```js
var a = 42;
var b = "foo";

a < b;      // false => 42 < NaN
a > b;      // false => 42 > NaN
a == b;     // false => 42 == NaN
```
