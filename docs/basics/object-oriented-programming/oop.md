## OOP in TS

Using lastest features like the following, we can create OOP models in TS

- Interfaces
- Classes
- Inheritance
- Modules

### Interfaces

TypeScript will treat interfaces in the same way as it treats primitive types, and it will use duck typing to ensure that when we say that an object matches an interface, then it really does match the interface, with no property left behind or It does not have any other properties. It allows only known properties. It can have optional properties too.

> As per TS language standards, Interfaces should have a prefix character I as it provides readibility and distinctions for IDE not having as good intellisense as VS Code.

We can use `in` operator to check that something exists in an object and then decide accordingly. But, the interfaces are kind of iterables which can be iterated and extracted the key names from the name

```js
interface IPerson {
  id: number;
  name: string;
}
 type KeyNames = keyof IPerson // KeyName allows only the "id" and "name": Iterable result of interfaces.
```

We can make the abstract class pattern in TS: A class implementing an interface.

```js
class PersonA implements PersonWhoCanWalk {
  walk(speed: number): void {
    console.log(`Person A is walking at speed at ${speed}}`);
  }
}
class PersonB {
  walk(speed: number): void {
    console.log(`Person B is walking at speed at ${speed}}`);
  }
}

interface PersonWhoCanWalk {
  walk(speed: number): void;
}

function printClass(a: PersonWhoCanWalk) {
  a.walk(10);
}
let userA = new PersonA();
let userB = new PersonB();
printClass(userA); // this method can accept userA as arg as it implements the interface PersonWhoCanWalk
printClass(userB); // this case is accepted too as it has the said method signature.
```

---

---

### Classes

A class is the definition of an object, what data it holds, and what operations it can perform. This safeguards against accidental assignments.

Class constructors can accept arguements during the initialization.
TS extends the features to modify the property and their accessibility across the code. Since JS does not support this feature, this is stripped during transpilation.
Moreover, we can extend the class with modifiers to enhance the properties and methods:

- property modifiers:
  - private: within the class only
  - readonly: non-writeable properties
  - public: read and write freely as long as you follow other TS properties.
- Method modifiers:
  - get: exposers of property of the class to its users
  - set: set a property of this class
- Static traits: Only one instance of it will be created and shared across all instances of this class. It can be a property or a function

```js
class Person {
  id: number; // id is not definately assigned.
  construtor() {}
  printID() {}
}
// what above error means is that when an instance is created, id will not be assigned and therefore will be `undefined`
// quick fix for above error will either be: to assign a default value or use an union type like number | undefined
```

- Namespaces:To avoid conflict of names when working with large codebases and API implementations:

```js
namespace FirstName {
  export class NameSpaceClass {}
  class NotExported {}
}

// this will be imported as following
const classInstance = new FirstName.NameSpaceClass();
```

During code transpilation, it will be ensured that we have unique class names across the codebase.

---

---

## Inheritance

Inheritance allows us to create an object based on another object,
thereby inheriting all of its characteristics, including properties and functions.

```js
abstract class Emp {
  public id: number;
  constructor(id: number) {}
  abstract leave(exitMessage: string): void;
  // abstract methods which is to be implemented by the classed implementing this
}

class EmpC extends Emp {
  leave(counter: string) {
    console.log(counter);
  }
}

const empc = new EmpC(100);
empc.leave("10");
```

Both classes and methods can be abstract and need to be implemented by their children.

### Modules

TS and JS both support modules. That is similar code can be bundled together to represent as an entity and imported and exported as an unit.

```js
// export
export class SomeClass {}

// partial export
export default function DefaultAdd(a: number, b: number) {
  return a + b;
}
export class ModuleNonDefaultExport {}

// default exports (discouraged. Allows renaming)
import DefaultAdd from "./modules/DefaultExport";
let modDefault = DefaultAdd(1, 2);
```

Modules can be imported as:

```js
// namespace imports: all modules exported will be available under the namespace.
import * as MultipleExports from "./modules/MultipleExports";
let meMc1 = new MultipleExports.MultipleClass1();
let meMc2 = new MultipleExports.MultipleClass2();

// module can be renamed while being imported: strongly discouraged as this might lead to name confusion and lead to lack to coherance in the codebase.
import { Module1 as MyMod1 } from "./modules/Module1";
let myRenamedMod = new MyMod1();
myRenamedMod.print();
```
