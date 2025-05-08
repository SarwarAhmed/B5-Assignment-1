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
