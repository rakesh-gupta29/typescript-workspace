## TS Union Types

Sort of `or` operator for types. use type a or type b from type `a | b`. It still holds the duck typing methods and its types.

```js
function add(a: string | number, b: string | number) {
  return a + b;
}
```

As per type inference, this would throw an error sinceIt does not know which type to use for the addition: string or number. Moreover, the return type is `any`.
We can use type-guars in this case that will check the type of arguement before adding

```js
function add(a: string | number, b: string | number) {
  if (typeof a === "string") {
    // a is treated as a string. This will be inferred as string. Typescript respects the typeof checks in the code.
    console.log(`a is of type string`);
    return a + b;
  }

  if (typeof a === "number" && typeof b === "number") {
    // both are numbers
    console.log(`a and b are numbers`);
    return a + b;
  }
  console.log(`default return treat both as strings`);
  return a.toString() + b.toString();
}
```
