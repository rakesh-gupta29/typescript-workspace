## Basics of Type Mathematics

- ### Input a type and create a new class with all of its properties as optional.
  Even in this case, we will not be able to assign any value which is not defined in the type `IStrong`.

```js
interface IStrong {
  name: string;
  age: number;
}
type IWeak<T> = {
  [K in keyof T]?: T[K];
};

const check: IWeak<IStrong> = {
  name: "jkfnjkef",
  age: 10,
};
```

- ### Modify the values to readonly type

```js
type Person = {
  name: string;
};
type ReadOnlyPerson<T> = {
  readonly [K in keyof T]: T[K];
};
const rohit: ReadOnlyPerson<Person> = {
  name: "read only name",
};
rohit.name = "eklfmnke"; // not allowed ;
```

# Mapped Types

- ### Partial Type: Make another type being a partial of input type
  Input a type and create a type accepting only a partial of original type without changing any other attribute type.

```js
type Person = {
  name: string,
  age: number,
};
type PartialName = Partial<Person>; // accept any partial of a person.
```

- ### Pick: Partial with args as to what is to be included.

```js
interface IAbc {
  a: number;
  b: string;
  c: boolean;
}
type PickAb = Pick<IAbc, "a" | "b">;
let pickAbObject: PickAb = {
  a: 1,
  b: "test",
  c: "property not allowed", // error: Not allowed
};
```

- ### Record: Create a type on the fly with the args provided.

```js
type RecordedCd = Record<"c" | "d", number>;
let recordedCdVar: RecordedCd = {
  c: 1,
  d: 1,
};
```

- ### Optional Types: Decide which type will be created based on the type of the condition

```js
 // decide which  type it is based on the  condition.

 type NumberOrString<T> = T extends number ? number : string
```
