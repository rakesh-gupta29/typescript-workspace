## TS Enums

Providing a Human readable form to related data. This is converted to bi-directional objects during transpilations i.e. both the kays and values are mapped together

```js
enum DoorState {
 Open,
 Closed,
}

function checkDoorState(state: DoorState) {
 console.log(`enum value is : ${state}`);
 switch (state) {
   case DoorState.Open:
     console.log(`Door is open`);
     break;
   case DoorState.Closed:
     console.log(`Door is closed`);
     break;
 }
}
// assign the value you like to keys in enmus, if not assigned, they are incremented by one starting from zero.
enum DoorStateSpecificValues {
 Open = 3,
 Closed = 7,
 Unspecified = 256,
}

// string enums: assign string values to the keys of enums
enum DoorStateString {
 OPEN = "Open",
 CLOSED = "Closed",
}
```

Due to performace reasons, TS has introduced `const` enums.
They are stripped off during transpilation.

```js
const enum Name {
  first = "rakesh",
  middle = "kumar",
  last = "gupta",
}

let fullName = [Name.first, Name.middle, Name.last];

// this will be compiled to
fullName = ["rakesh", "kumar", "gupta"];
// this is simply the substitution of value wherevere you have usedd the value Name.first and so on.
console.log(fullName);
```
