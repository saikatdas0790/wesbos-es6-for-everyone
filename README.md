# Learning ES6 (ES2015) and beyond

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
