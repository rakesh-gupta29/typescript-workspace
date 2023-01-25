## Types in Javascript

Types in Javascript is defined at runtime. `typeof` operator can be used to determine the types at runtime but this method sometimes provides wrong results. Javascript only has following types:

- number - `NaN` is the result of an arithmatic operation when the result is not a valid number.
- string - textual data and is encoded as a sequence of 16-bit unsigned integer
- boolean - true/false
- symbol - unique and immutable primitive value which is like an unique signature. This can be used a key for objects.
- object - object is a value in memory which is possibly referenced by an identifier.
- null - the intentional absence of any object value.
- undefined - default assignment to primtive data types which are declared but not yet assigned
- bigint - numeric primitive in JavaScript that can represent integers with arbitrary magnitude

Typescript attempts to extend this feature with static typing: Defining the types while coding. using the precompiler of typescript, we can extend the language features with syntax and abilities not supported in javascript. While transpilign the code, this will be converted into syntax supported by javascript.
