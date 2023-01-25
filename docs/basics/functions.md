## Functions in TS

Passing Optional Parameters

```js
function concatValues(a: string, b?: string) {
  // value of b defaults to undefined.
  // optional parameters precede in the order. Optional parameters should always appear in the last.or can have a default value.
  console.log(`a + b = ${a + b}`);
}
concatValues("first", "second");
concatValues("third");
```

In a quite quirky way, we can still access or pass the value even if we have not accepted any parameter while defining the array in JS but **NOT** in TS.

```js
function testArguments() {
  // arguements is an array
  // argument[0] = 1
  // argument[1] = 2

  for (var i = 0; i < arguments.length; i++) {
    console.log("argument[" + i + "] = " + arguments[i]);
  }
}
testArguments(1, 2);
testArguments("first", "second", "third");
```

In order to do that in TS, we can use rest syntax

```js
function testArguments(...args: string[] | number[]) {
  // arguements is an array
  // argument[0] = 1
  // argument[1] = 2

  for (let i in args) {
    console.log("argument[" + i + "] = " + arguments[i]);
  }
}
testArguments(1, 2);
testArguments("first", "second", "third");
```

TS provides more safety specially when the type of an argument is to be defined during the runtime like callback functions.

```js
function myCallback(text: string): void {
  console.log(`myCallback called with ${text}`);
}
function withCallbackArg(message: string, callbackFn: (text: string) => void) {
  console.log(`withCallback called, message : ${message}`);
  callbackFn(`${message} from withCallback"`);
}
```

We can annonoate the function signature to match a specific pattern.

In TS,we can create multiple signatures of a function with same name but with different parameters or even the order in which they are declared
TS intellisense will hint the number of function overrides that exist. This pattern is quite useful for creating API functions with same name but with different implemetations.

```js
function add(a: string, b: string): string;
function add(a: number, b: number): number;
function add(a: any, b: any) {
 return a + b;
}
add("first", "second");
add(1, 2);
```
