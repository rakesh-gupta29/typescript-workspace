## Type Casting

instead of relying on the inference for types, we can explicitly mention the types of variables.
There are folllowing ways to mention the type:

```js
var  user = { name :"username"}

1. using <> syntax
var  user = <any>{ name :"username"}

2. using as operator
var  user = { name :"username"} as any

3. Using : operator
var  user:any = { name :"username"}
```
