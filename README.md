# Wes Bos - ES6 for Everyone

## Module 1 - New Variables — Creation, Updating and Scoping

> Use `const` for most scenarios unless you need a value that you need to rebind, then use `let`

- `var` is function-scoped
- `let` and `const` is block-scoped

## Module 2 - Function Improvements: Arrows and Default Arguments

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
