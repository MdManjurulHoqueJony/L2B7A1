# Why is `any` Called a Type Safety Hole and Why is `unknown` Safer?

## Introduction

Not all types in TypeScript provide the same level of protection, such as `any` and `unknown`.

Though both can store any kind of value, they behave very differently. The `any` type removes TypeScript safety completely, while `unknown` forces developers to verify data before using it.

---

## Why is `any` Called a Type Safety Hole?

The `any` type disables TypeScript checking. Once a variable becomes `any`, TypeScript stops validating operations on it.

```ts
let value: any = "Hello";

value = 100;
value.toUpperCase();
```

In the example above, TypeScript allows toUpperCase() even though the value is a number at runtime. This can cause runtime errors.

Because any bypasses the type system, it is known as a “type safety hole.”

## Why is unknown Safer?

The unknown type can also hold any value, but TypeScript does not allow unsafe operations directly.

```ts
let value: unknown = "TypeScript";

value.toUpperCase();
```

The code above produces an error because TypeScript does not know whether value is actually a string.

Before using the value, we must narrow its type.

```ts
let value: unknown = "TypeScript";

if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

This approach prevents unexpected runtime issues.

## vWhat is Type Narrowing?

Type narrowing means reducing a broad type into a more specific type using checks.

TypeScript commonly uses:

typeof
instanceof
in operator
custom type guards
Example
```ts
function printValue(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }

  return value.toFixed(2);
}
```

Here, TypeScript narrows the type based on the condition.

## Conclusion

The any type removes TypeScript’s protection and can introduce bugs into applications. On the other hand, unknown forces developers to validate data before using it, making code safer and more predictable.

Using unknown together with type narrowing is considered a best practice for handling unpredictable data in TypeScript.