# Learning ES6 (ES2015) and beyond

## JavaScript Data Types

- Boolean
- Null
- Undefined
- Number
- String
- Symbol
- Object

## 1. New Variables — Creation, Updating and Scoping

> Use `const` for most scenarios unless you need a value that you need to rebind, then use `let`

- `var` is function-scoped
- `let` and `const` is block-scoped

## 2. Function Improvements: Arrows and Default Arguments

- Arrow functions are anonymous functions
- `this` keyword used in arrow functions do not rebind to the object being used it. Still refers the parent object
- To use `this` in object method calls, use a `function() {}` block and bind to the object and then use `this` inside arrow functions inside the function to refer to the bound object
- ES6 supports default values for function parameters like so:

```javascript
function someFunction(paramter1 = "someValue") {}
```

### When NOT to use an Arrow Function

- When you really need `this`
- When you need a method to bind to an object
- When you need to add a prototype method
- When you need arguments object

## 3. Template Strings

### Syntax

```javascript
function taggingFunction (strings, ...values) {

}

const someString = taggingFunction`Some literal text ${any JavaScript code} some more literal text${other JavaScript code}`;
```

- `strings` variable is always going to be _one_ more in length than `values` variable

### Features

- Easy string concatenation
- Creating Javascript variables as HTML markup with inline JS in them
- Nesting template strings (including _inline JS_)
- Function tagging

## 4. String Improvements

### New String Methods

#### `.startsWith()`

```javascript
str.startsWith(searchString[, position])
```

> determines whether a string begins with the characters of a specified string, returning true or false

#### `.endsWith()`

```javascript
str.endsWith(searchString[, length])
```

> determines whether a string ends with the characters of a specified string, returning true or false

#### `.includes()`

```javascript
str.includes(searchString[, position])
```

> determines whether one string may be found within another string, returning true or false

#### `.repeat()`

```javascript
str.repeat(count);
```

> constructs and returns a new string which contains the specified number of copies of the string on which it was called, concatenated together

## 5. Destructuring

### Destructuring objects

```javascript
// Accessing a flat object
const someObject = {
  property1: "Value1",
  property2: "Value2",
  property3: "Value3"
};

const { property1, property2, property3 } = { someObject };

// Accessing a nested object
const someObject = {
  property1: "Value1",
  property2: {
    subProperty1: "Subvalue1",
    subProperty2: "Subvalue2"
  },
  property3: "Value3"
};

const { subProperty1: renamedProperty1 = "DefaultValue1", subProperty2: renamedProperty2 = "DefaultValue2", subProperty3 = "DefaultValue3" } = { someObject.property2 };
```

### Destructuring Arrays

```javascript
const someArray = ["Value1", "Value2", "Value3"];

const [item1, ...others] = someArray;
```

## 6. Iterables and Looping

### Different looping constructs in JavaScript

#### `for` loop

```javascript
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}
```

#### `array.forEach()` method

```javascript
array.forEach(element => {
  console.log(element);
});
```

- cannot use `break` or `continue` statements in `forEach()` loops

#### `for...in` loops

```javascript
for (const index in array) {
  console.log(array[index]);
}
```

- iterates over the index of the `iterable` instead of the elements themselves
- iterates over everything in the array including things (properties, methods) that have been added to the `prototype`

#### `for...of` loops

```javascript
for (const element of array) {
  console.log(element);
}
```

- **Use** this looping construct by default
- `array.entries()` lets us get at the generator for the `iterable`

### Iterating over an `Object`

- cannot iterate over an `Object`
- `Object.entries()` and `Object.values()` included in ES2017
- `Object.keys(someObject)` - returns an `array` of the `keys` of the `object`
- Using `for...in` will also allow access to the `object`'s `keys`

## 7. Array Improvements

### `Array.from()`

```javascript
Array.from(arrayLike[, mapFn[, thisArg]])
```

> creates a new, shallow-copied Array instance from an array-like or iterable object

### `Array.of()`

```javascript
Array.of(element0[, element1[, ...[, elementN]]])
```

> creates a new Array instance with a variable number of arguments, regardless of number or type of the arguments.
> The difference between `Array.of()` and the `Array` constructor is in the handling of integer arguments: `Array.of(7)` creates an array with a single element, 7, whereas `Array(7)` creates an empty array with a length property of 7

### `Array.find()`

```javascript
arr.find(callback[, thisArg])
```

> returns the value of the first element in the array that satisfies the provided testing function. Otherwise undefined is returned

### `Array.findIndex()`

```javascript
arr.findIndex(callback[, thisArg])
```

> returns the index of the first element in the array that satisfies the provided testing function. Otherwise -1 is returned

### `Array.some()`

```javascript
arr.some(callback[, thisArg])
```

> tests whether _at least one_ element in the array passes the test implemented by the provided function

### `Array.every()`

```javascript
arr.every(callback[, thisArg])
```

> tests whether _all elements_ in the array pass the test implemented by the provided function

## 8. Spread and Rest operator

### Spread

```javascript
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]
func([args ,] ...iterable [, args | ...iterable])
```

> Allows parts of an array literal to be initialized from an iterable expression (such as another array literal), or allows an expression to be expanded to multiple arguments (in function calls).

### Rest

```javascript
function f(a, b, ...theArgs) {
  // ...
}
```

> The rest parameter syntax allows us to represent an indefinite number of arguments as an array

## 9. Object Literal Upgrades

- If property names are the same as variables, the variable name assignments in the object declaration can be skipped by only declaring the properties
- For function declarations, can exclude the property name and set up a function declaration as the property
- For object key-values, keys and objects can be declared using array values or template strings or a combination of the above

## 10. Promises

> The Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value

> Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function

```javascript
new Promise(function(resolve, reject) {
  // any processing code
  // code for resolve
  // code for reject
});
```

### Useful methods

- `Promise.all`
- `Promise.race`

## 11. Symbols

> "Symbol" is a primitive data type having the quality that, values of this type can be used to make object properties that are anonymous. This data type is used as the key for an object property when the property is intended to be private, for the internal use of a class or an object type

## 12. Code Quality with ESLint and Prettier

- Set up ESLint plugin and use node modules to import packages for ESLint and Prettier and configure them to work well with each other
- Modify the git commit message hook to deny commits that fail eslint error validations

## 13. JavaScript Modules and Using npm

### `import` statement

> import statement is used to import bindings which are exported by another module

```javascript
import defaultExport from "module-name";
import * as name from "module-name";
import { export } from "module-name";
import { export as alias } from "module-name";
import { export1 , export2 } from "module-name";
import { export1 , export2 as alias2 , [...] } from "module-name";
import defaultExport, { export [ , [...] ] } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";
var promise = import(module-name);
```

#### Dynamic Imports

> The import keyword may be called as a function to dynamically import a module. When used this way, it returns a promise.

```javascript
import("/modules/my-module.js").then(module => {
  // Do something with the module.
});
```

> This form also supports the await keyword

```javascript
let module = await import('/modules/my-module.js');
```

### `export` statement

> export statement is used when creating JavaScript modules to export functions, objects, or primitive values from the module so they can be used by other programs with the import statement

```javascript
export { name1, name2, …, nameN };
export { variable1 as name1, variable2 as name2, …, nameN };
export let name1, name2, …, nameN; // also var, const
export let name1 = …, name2 = …, …, nameN; // also var, const
export function FunctionName(){...}
export class ClassName {...}

export default expression;
export default function (…) { … } // also class, function*
export default function name1(…) { … } // also class, function*
export { name1 as default, … };

export * from …;
export { name1, name2, …, nameN } from …;
export { import1 as name1, import2 as name2, …, nameN } from …;
export { default } from …;
```

#### Named exports:

```javascript
// exports a function declared earlier
export { myFunction };

// exports a constant
export const foo = Math.sqrt(2);
```

#### Default exports (function)

```javascript
export default function() {}
```

## 14. ES6 Tooling

### Alternative Tools

- SystemJS - For ES6 module support
- Polyfill.io - For polyfilling in browsers

## 15. Classes

### Prototypal Inheritance

When it comes to inheritance, JavaScript only has one construct: objects. Each object has a private property which holds a link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with null as its prototype. By definition, null has no prototype, and acts as the final link in this prototype chain

JavaScript objects are dynamic "bags" of properties (referred to as **own properties**). JavaScript objects have a link to a prototype object. When trying to access a property of an object, the property will not only be sought on the object but on the prototype of the object, the prototype of the prototype, and so on until either a property with a matching name is found or the end of the prototype chain is reached

### `Class` features

#### `constructor` method

The `constructor` method is a special method for creating and initializing an object created with a `class`. There can only be one special method with the name "constructor" in a class. A `SyntaxError` will be thrown if the class contains more than one occurrence of a `constructor` method.

A constructor can use the `super` keyword to call the constructor of the super class.

#### `static` keyword

The `static` keyword defines a static method for a class. Static methods are called without instantiating their class and **cannot** be called through a class instance. Static methods are often used to create utility functions for an application.

#### `get` properties

The `get` syntax binds an object property to a function that will be called when that property is looked up.

```javascript
class SomeClass {
  get prop() {
    return someProperty;
  }
}
```

#### `set` properties

The `set` syntax binds an object property to a function to be called when there is an attempt to set that property

```javascript
class SomeClass {
  let someVariable;
  set prop(value) {
    this.someVariable = value;
  }
}
```

#### `super` keyword

The `super` keyword is used to access and call functions on an object's parent.

The `super.prop` and `super[expr]` expressions are valid in any method definition in both classes and object literals

```javascript
super([arguments]); // calls the parent constructor.
super.functionOnParent([arguments]);
```

#### `extends` keyword

The `extends` keyword is used in class declarations or class expressions to create a class which is a child of another class

```javascript
class ChildClass extends ParentClass {
  ...
}
```
