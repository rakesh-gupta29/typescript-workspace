## Are enums harmful? how can we improve this?

```js
enum Options {
"all",
"services",
"industries",
}
```

on transpilation, it is convertied to double inverted object which presents first problem

```js
const option = Options.all;
const optionWithIndex = Options[0];
```

they are basically at intersection of runtime and type system.
GOOD:
ease of refactoring and socpring to specific enums

```js
enum OptionsCopy {
    "all",
    "services",
    "industries",
}
function logOption(entry: Options) {
    console.log(entry);
}
logOption(Options.all);

```

even though OptionsCopy is identical to Options, we can't pass it to the logOption funciton
logOption(OptionsCopy.all); error

## Using const enums

Using const enums will replace the value wherver it used during transpilation. Using a const emun is not recommeneded at all as control of transipilation is required for the same.
In library code, const enums should not be used at all.

```js
enum OptionsCopy {
    "all",
    "services",
    "industries",
}
 const option = OptionsCopy.all // "all"
```

In above cases, using a POJO (Plain Old Javascript Object) will be simpler

```js
const Options = {
  all: "all",
  services: "services",
  industries: "industries",
} as const;

```
