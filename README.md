# Differences Between Interfaces and Types in TypeScript

## Declaration Syntax

- **Types** use the `type` keyword: `type Person = { name: string }`
- **Interfaces** use the `interface` keyword: `interface Person { name: string }`

## Key Differences

### 1. Declaration Merging

- Interfaces support declaration merging - multiple declarations combine automatically
- Types cannot be re-opened to add new properties

### 2. Extending and Implementing

- Interfaces can extend other interfaces and classes using `extends`
- Types use intersection operators (`&`) for combining types
- Classes can implement interfaces but cannot implement type aliases directly

### 3. Primitive Types

- Types can create unions and tuples: `type Status = "success" | "error"`
- Interfaces are primarily for object shapes

### 4. Computed Properties

- Types support mapped types and advanced type operations
- Interfaces are more limited to straightforward object-like declarations

## Code Examples
```typescript
// Interface example
interface Animal {
  name: string;
}

interface Animal {
  age: number; // Declaration merging: Animal now has name and age
}

// Type example
type StringOrNumber = string | number; // Union type
type Point = [number, number]; // Tuple type
```


# What is type inference in TypeScript? Why is it helpful?
Type inference is TypeScript's ability to automatically determine and assign types to variables. This is one of TypeScript's most powerful features that makes the language both safer and more convenient to use.

Here's how it works with some examples:
```typescript
// Type inference with variables
let message = "Hello"; // 'string'
let number = 42;       //  'number'
let isActive = true;   //  'boolean'

// Type inference with arrays
let numbers = [1, 2, 3]; //  'number[]' array
let mixed = [1, "hello"]; //  (string | number)[]

// functions
function add(a: number, b: number) {
    return a + b; // Return type is inferred as number
}

// Type inference with object literals
const person{     
    name: "Mr Name", 
    age: 23
} // { name: string; age: number }
```

### Type inference is helpful for several reasons:
1. **Reduces Boilerplate**: You don't need to explicitly declare types when TypeScript can figure them out, making code more concise and readable.
2. **Maintains Type Safety**: Even though you're not explicitly declaring types, you still get all the benefits of TypeScript's type checking.
3. **Better Developer Experience**:
    - You get excellent IDE support (autocompletion, refactoring)
    - Errors are caught at compile time
    - TypeScript can suggest correct types based on usage

4. **Best of Both Worlds**: You get the convenience of JavaScript-like coding with the safety of a statically typed language.

While type inference is powerful, there are times when you'll want to explicitly declare types:
- When you want to document your code's intent more clearly
- When TypeScript's inferred type is not exactly what you want
- When declaring interfaces or type definitions for API contracts

```typescript
// Type inference in array methods
const numbers = [1, 2, 3, 4, 5];

numbers.map(num => num * 2); // TypeScript knows 'num' is a number
                            // and the result will be number[]

// With objects and destructuring
const users = [
    { name: "Alice", age: 25 },
    { name: "Bob", age: 30 }
];

users.forEach(({ name, age }) => {
    // TypeScript infers:
    // name is string
    // age is number
    console.log(`${name} is ${age} years old`);
});
```
