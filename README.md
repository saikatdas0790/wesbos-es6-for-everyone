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

## 4. Additional String Improvements

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
};
```
