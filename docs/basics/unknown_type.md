## Unknown type in TS

This is used when the type of data being stored is not known at the time. It differs from `any` in the sense that it can be reassigned to a type again.

```js
let a: any = "test";
let aNumber: number = 2;
aNumber = a; // assignment of a string to a number. It is allowed as a is any.
// Basically, any type is allowed to be a value of any type.
let isDone: boolean = false;
isDone = a;
```

`any` type is interchangeable with every type. This happens with `object` type too. They are interchangeable.

```js
let unknown_counter: unknown = 0;
let counter: number = 10;
counter = unknown_counter; // Error: type unknown is not assignable to type number
```

Unknown type is peculiar is a way. `any` disables all type checkings at all times but `unknown` relaxes the type checkings only untill the checks are done. unknown behaves like a type itself and can be reassigned to unknown type only. The unkown does not mingle well with other types.

> Using the unknown type forces us to make a conscious decision when using these values. In essence, we are letting the compiler know that we know what type this value should be when we actually want to use it. This is why it is seen as a type-safe version of any, as we need to use explicit casting to convert an unknown type into a known type before using it.
