## Overhead features supported in TS but not in JS.

- Optional Chaining Move ahead only when the condition is true

```js
var objectA = {
  nestedProperty: {
    name: "nestedPropertyName",
  },
};

function printNestedObject(obj) {
  console.log("obj.nestedProperty.name = " + obj.nestedProperty.name);
}
printNestedObject(objectA);

// This has the effect that if any one of the nested properties returns
// null or undefined, the entire statement will return undefined.

function printNestedOptionalChain(obj: any) {
  if (obj?.nestedProperty?.name) {
    // returns null if any statement returns null
    console.log(`name = ${obj.nestedProperty.name}`);
  } else {
    console.log(`name not found or undefined`);
  }
}
```

- Nullish Coalescing - Optional Chanining with expressions to provide optional values for null or undefined

```js
function nullishCheck(a: number | undefined | null): number {
  return a ?? 0;
}
// return a if it is defined otherwise zero. This hold true for operator checks too
function testNullOperands(a: number, b: number | null | undefined) {
  let addResult = a + (b ?? 0);
}
```

- Define Assignments : Breaking the rule of typescript to check the code to press that this value exists. To achieve the same, we use _definitive assignment operator_ or `!` mark.

```js
console.log(username); // undefined. Has  undefined value
var username = "username";
console.log(username); // username
// TS will  check that username is being usef before being assigned.

var globalString: string;
setGlobalString("this string is set");
console.log(`globalString = ${globalString}`); // error: used before being assigned.
function setGlobalString(value: string) {
  globalString = value;
}


// This will tell the compiler that we are overriding its type checking rules,
// and are willing to let it use the globalString variable, even though it thinks it has not been assigned.
var globalString: string;
setGlobalString("this string is set");
console.log(`globalString = ${globalString!}`);
function setGlobalString(value: string) {
  globalString = value;
}

// or alternatively while declaring the variable itself.
var globalString!: string;

```

- Object Types: This is a general type covering all data types which are not strings, numbers, null, undefined, symbol or boolean.

```js
let structuredObject: object = {
  // aceept any object
  name: "myObject",
  properties: {
    id: 1,
    type: "AnObject",
  },
};
function printObjectType(a: object) {
  console.log(`a: ${JSON.stringify(a)}`);
}
```

- ## Instance of
  to check that an object is an instance of a class or not. It can be used to determine that an entity has all object has properties and methods of a native class

```js
class A {}
class BfromA extends A {}
class CfromA extends A {}
class DfromC extends CfromA {}
console.log(`A instance of A :
 ${new A() instanceof A}`);
console.log(`BfromA instance of A :
 ${new BfromA() instanceof A}`);
console.log(`BfromA instance of BfromA :
 ${new BfromA() instanceof BfromA}`);
/*
 A instance of A :
 true
BfromA instance of A :
 true
BfromA instance of BfromA :
 true
 */
```

Instance of returns true if the class exists anywhere in extension chain of classes i.e. It does not need to extends directly to the class it is being checked against.
