# You Don't Know JS: Up & Going
## Chapter 1: Into Programming

### Statement
```
a = b * 2;
```

### Expressions
```
a = b * 2;
```
This statement has four expressions in it:
* `2` is a literal value expression.
* `b` is a variable expression, which means to retrieve its current value.
* `b * 2` is an arithmetic expression, which means to do the multiplication.
* `a = b * 2` is an assignment expression, which means to assign the result of the `b * 2` expression to the variable `a` (more on assignments later).

```
b * 2
```
* A general expression that stands alone is also called an expression statement.
* It wouldn't do anything with that result.

```
alert( a );
```
* The entire statement is the function call expression itself.

### Executing a Program
* For some computer languages, this translation of commands is typically done from top to bottom, line by line, every time the program is run, which is usually called interpreting the code.
* For other languages, the translation is done ahead of time, called compiling the code, so when the program runs late, what's running is actually the already complied computer instructions ready to go.

### Output
* `console.log(...)`
* `alert(...)`

### Input
* `prompt(...)`

### Operators
* Operators are how we perform actions on variables and values.
* Assignment: `=` as in `a = 2`.
* Math: `+` (addition), `-` (subtraction), `*` (multiplication), and `/` (division), as in `a * 3`.
* Compound Assignment: `+=`, '-=', '*=', '/=' are compound operators that combine a math operation with assignment, as in `a += 2` (same as `a = a + 2`).
* Object Property Access: `.` as in `console.log(...)`, properties can alternatively be accessed as `console['log']`.
* Equality: `==` (loose-equals), `===` (strict-equals), `!=` (loose not-equals), `!==` (strict not-equals), as in `a == b`.
* Comparison: < (less then), > (greater than), <= (less than or loose-equals), `>=` (greater than or loose-equals), as in `a < b`.
* Logical: `&&` (and), `||` (or), as in `a || b` that selects either `a` or `b`.

### Values & Types
* When you need to do math, you want a number.
* When you need to print a value on the screen, you need a string (one or more characters, words, sentences).
* When you need to make a decision in your program, you need a boolean (true or false).
* String literals are surrounded by double quotes `"..."` or single quotes `'...'`.
* number and boolean literals are just presented as is (i.e., 42, true, etc.).

### Converting Between Types
* Implicit coercion can create confusion if you haven't taken the time to learn the rules that govern its behavior. Most JS developers never have, so the common feeling is that implicit coercion is confusing and harms programs with unexpected bugs, and should thus be avoided. It's even sometimes called a flaw in the design of the language.

### Code Comments
* Code without comments is suboptimal.
* Too many comments (one per line, for example) is probably a sign of poorly written code.
* Comments should explain why, not what. They can optionally explain how if that's particularly confusing.
* The `//` single-line comment.
* The `/* ... */` multiline comment.

### Variables
* We declare a variable using the `var` statement.
* We declare a constants variable using the `const` statement (as of ES6).

### Blocks
* A block is defined by wrapping one or more statements inside a curly-brace pair `{ .. }`.

### Conditionals
* `if`, `else`, `else if`.

### Loops
* the `while` loop and the `do..while` loop.
* there's another syntactic form called a `for` loop for just that purpose.

### Functions
* A function is generally a named section of code that can be "called" by name, and the code inside it will be run each time.
* Functions can optionally take arguments (aka parameters) -- values you pass in.
* Functions can also optionally return a value back.

### Scope
* Programming has a term for this concept: scope (technically called lexical scope). In JavaScript, each function gets its own scope. Scope is basically a collection of variables as well as the rules for how those variables are accessed by name. Only code inside that function can access that function's scoped variables.
* A variable name has to be unique within the same scope.
* A scope can be nested inside another scope, just like if a clown at a birthday party blows up one balloon inside another balloon. If one scope is nested inside another, code inside the innermost scope can access variables from either scope
* Lexical scope rules say that code in one scope can access variables of either that scope or any scope outside of it.
### Review
* You need operators to perform actions on values.
* You need values and types to perform different kinds of actions like math on numbers or output with strings.
* You need variables to store data (aka state) during your program's execution.
* You need conditionals like if statements to make decisions.
* You need loops to repeat tasks until a condition stops being true.
* You need functions to organize your code into logical and reusable chunks.
