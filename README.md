1.What is the use of the keyof keyword in TypeScript?
In TypeScript, the keyof keyword is a powerful utility that allows us to get the union of string literal types representing the keys of an object type. It enables type-safe operations when accessing or manipulating object properties.

Why is it useful?
Imagine you're building a function that should only accept valid property names of an object. Without keyof, you'd either rely on any or hardcoded strings — both of which break type safety. keyof ensures that only existing property names are accepted.

Example:
type Person = {
  name: string;
  age: number;
  isEmployed: boolean;
};

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const john: Person = { name: "John", age: 30, isEmployed: true };

const nameValue = getProperty(john, "name"); 
// const invalid = getProperty(john, "salary"); 


2.Explain the difference between any, unknown, and never types in TypeScript
TypeScript offers strong type safety, and understanding its special types—any, unknown, and never—is key to writing safer, more predictable code.

#any: Disable Type Checking
The any type tells TypeScript to give up type checking. It can hold any value, and you can do anything with it — no compile-time error.
let data: any = "Hello";
data = 123;
data.toUpperCase(); // No error, even if data is a number now

#unknown: Safe Alternative to any
unknown also accepts any value, but unlike any, you can’t use it directly without checking its type.
let input: unknown = "Hello";

// input.toUpperCase();
if (typeof input === "string") {
  input.toUpperCase();
}


#never: Impossible Values
The never type represents values that should never occur — typically used for functions that throw errors or run infinite loops.

function throwError(message: string): never {
  throw new Error(message);
}

