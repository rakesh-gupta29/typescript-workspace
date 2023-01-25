## Tuples in TS: Specical case of an array

Tuples are a method of defining a type that has a finite number of unnamed properties, with each property having an associated type

```js
let tuple1: [string, boolean];
tuple1 = ["test", true];
```

It always has to have same length and same data type at all indexes mentioned.

We can destructure the elements like an array

```js
let tup: [string, boolean] = ["some string", false];
const [valString, valBoolean] = tup;
console.log(valString[0]);
```

Optional Tuple Elements

```js
let tupleOptional: [string, boolean?]; // will be undefined
tupleOptional = ["test", true];
tupleOptional = ["test"];
console.log(`tupleOptional[0] : ${tupleOptional[0]}`);
console.log(`tupleOptional[1] : ${tupleOptional[1]}`)
```

Tuples with variable length

```js
let tupleRest: [number, ...string[]];
tupleRest = [1];
tupleRest = [1, "string1"];
tupleRest = [1, "string1", "string2"];
```
