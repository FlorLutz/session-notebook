# Typescript

## setup

- `npm install -g typescript` to install globally
- run `npx tsc` to run it in a project

## use

- introducing type sensitivity to JS
- to start create a .ts file with the same name as the regarding .js-file
- the .js will be updated directly
- .ts only used during development, final app will not have this code

## variables

- can be intitialized, this way they take on the type of its value, ex. `let a = 5` (will take number)
- you can also declare a variable and set a type for it, ex. `let a: number` and assign values later `a = 25`, assigning any other type will give out an error
- types are "any, number, string, boolean, null, ..."
- arrays can also be set to type sensitive, like `const arr: number[] = []`
- objects:

```
const user: User = {
    name: "Manu",
    age: 15,
    isActive: true //this property is optional, because of the question mark, without it, we would need to set a value for the property to not run into an error
}

type User = {
    name: string,
    age: number,
    isActive?: boolean
}

```

- functions can take case sensitive arguments and have a type for return values, ex.

```
  function add(a: number, b: number):number {
  return a+b}

```

- we can combine types with "|" like `let hobby: string | null` - that is called union types
- concrete values as possibilities can also be set: `let a: "yes" | "no"` - other values will give an error
- void as a result for a function that does not return specific values, like EventListeners, ex.

```
function createHTMLElement (): void {
 document.createElement("li");
}
```

- set new types with `type Message = {message: string}` or with interface `interface Message = {author: string}` (interface is less common and not important)
