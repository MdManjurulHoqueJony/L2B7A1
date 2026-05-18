# How Generics Build Reusable and Strictly Typed Code in TypeScript

## Introduction

Generics allows developers to create reusable functions, classes, and components while still maintaining strict type safety.

Without generics, developers often need to write duplicate code for different data types.

---

## Problem Without Generics

Suppose we want a function that returns the same value.

```ts
function returnString(value: string): string {
  return value;
}

function returnNumber(value: number): number {
  return value;
}
```

This creates unnecessary duplication.


## Using Generics

Generics solve this problem by allowing a type to be passed dynamically.

```ts
function returnValue<T>(value: T): T {
  return value;
}
```

Now the same function works for multiple types.

```ts
const name = returnValue<string>("John");
const age = returnValue<number>(25);
```

TypeScript automatically keeps the correct type.

## Generics with Arrays

Generics are also useful when working with arrays.

```ts
function getFirstElement<T>(items: T[]): T {
  return items[0];
}


const firstNumber = getFirstElement<number>([1, 2, 3]);
const firstString = getFirstElement<string>(["a", "b", "c"]);
```

This makes the function reusable for any array type.

## Benefits of Generics

1. Reusability

One function or class can work with multiple data types.

2. Type Safety

TypeScript still checks types strictly.

3. Cleaner Code

Developers avoid writing duplicate logic.

4. Better Maintainability

Updating one generic function is easier than maintaining multiple similar functions.

## Conclusion

Generics help developers write reusable, scalable, and type-safe code. They are especially useful in large TypeScript applications where flexibility and reliability are both important. By using generics properly, developers can reduce duplication while keeping strong type checking across the entire project.