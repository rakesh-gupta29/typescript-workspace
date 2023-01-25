## Generics in TS

---

What is covered in this module:

- Generic syntax, including:
  - Multiple generic types
  - Constraining and using the type T
  - Generic constraints and interfaces
  - Creating new objects within generics
  - Advanced type inference, including:
- Mapped types
  - Conditional types and conditional type chaining
  - Distributed conditional types
  - Conditional type inference
  - Type inference from function signatures and arrays
  - Standard conditional types

---

Generics, or, more specifically, generic syntax is a way of writing code that will work with a wide range of objects and primitives.

Generic Syntax:

```js
function printGeneric<T>(value: T) {
  console.log(`typeof T is : ${typeof value}`);
  console.log(`value is : ${value}`);
}
// above value will include the type and work accordingly. It is like passing a prop to a function and it will include it as a feature.

// generics can include as many arguements as you like
```

Using this method, we can pass any value to be used as a type for generics. To limit the type of value we can pass in the generics, we will have to specify the traits the generic should have.

```js
class Concat<T extends Array<string>> {
  public concatStrings(items: T): string {
    let returnString = "";
    for (let i = 0; i < items.length; i++) {
      returnString += i > 0 ? "," : "";
      returnString += items[i].toString();
    }
    return returnString;
  }
}

const concatStrings = new Concat();

console.log(concatStrings.concatStrings(["first", "second"])); // this method takes either array of strings and array of numbers
```

In case of multiple generics, we will be able to use only those properties and methods which are common among all types.

```js
interface Man {
  name: string;
  age: number;
}
interface Woman {
  name: string;
  isPregnant: boolean;
}
class CheckManOrWoman<T extends Man | Woman> {
  check(item: T): "man" | "woman" {
    console.log(item.name);
    //  console.log ( item.isPregnant) // error
    return "man";
  }
}
// this method can use only the name property as it is common among all. This is valid for both man and woman.

function isMan<T extends Man | Woman>(item: T): boolean {
  // can use only 'name' on this scope.
  if (item.name) return true;
  return false;
}

function printProperty<T extends object, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}
console.log(
  printProperty({ username: "username", email: "dummy.email" }, "username")
);
```

Besides using generics in functions, we can use them in types and interfaces too.Interfaces too can extend using a generic type.

```js
interface IPerson {
  name: string;
  age: number;
}
interface IActor<T extends IPerson> {
  isEmployed: boolean;
  nextMovieRole(isLead: boolean): string;
  isOld(personWithName: T): boolean;
}

class Actor<T extends IPerson> implements IActor<T> {
  public isEmployed: boolean = true;

  nextMovieRole(isLead: boolean): string {
    return isLead ? "lead" : "support";
  }
  isOld(person: T): boolean {
    return person.age >= 40;
  }
}

const amitabh = new Actor();
console.log(amitabh.isEmployed);
console.log(
  amitabh.isOld({
    name: "Amitabh",
    age: 100,
  })
);
```

```js
class ClassA {}
class ClassB {}
function createClassInstance<T>(arg1: T): T {
  return new arg1(); // error : see below
}
let classAInstance = createClassInstance(ClassA);

// correct implementation would be to create a new type for parameter arg1 which would overload  new function and returns a type of T
function createInstance<T>(arg1: { new(): T }): T {
  return new arg1();
}
```
