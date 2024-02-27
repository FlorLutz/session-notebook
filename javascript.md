# JavaScript

## script in an html

- write `<script></script>` in body and `<script src="script.js" defer></script>` in the head (defer executes it after page load)

## console tricks

- use `\t` for a tab
- use `\n` for a new line
- use `console.clear();` to clear console
- view console in browser or in terminal/VS Code with writing node nameOfJS-file or VSCode: RUN-StartDebugging
- to view the value of a variable, always write `console.log("variableName: ", variableName);` to know which variable is shown
- `console.error("message")` - to view error
- `console.warn("message")` - warning -`console.table(["a", "b", "c"])` - to create a table in the console
- template literals can be used by typing `` and they can have variables, ex.

```
`I really like ${name}, because yes`
```

## data types

- these exist: number, string, boolean, BigInt, undefined, null, symbol
- BigInt is used to store large numbers by writing a number followed by _n_, like let `myBigInt = 38952309529385902835n`
- undefined means variable has not been assigned yet
- null means it has been given _null_ value

## mathematical operations

- +, -, \*, /, ++, --, -=, +=, ... work
- ** does _power to_, like 2**3=8
- % is remainder, like 5%2=1

## selecting HTML-elements - querySelector

- `document.querySelector(element)` with tagName, #id, .class or data-js-attribute (latter should always be preferred)
- give the data-ja-attribute to HTML-elements: ex. `<main data-js="main"></main>`
- refer to the attribute, ex.`document.querySelector('[data-js="main"]')`
  -always store in variables, ex. `const main = document.querySelector('[data-js="main"]')`

## add, remove, toggle classes

- `selectedElement.classList` will show the classes ex. in console
- `selectedElement.classList.add("newClass")` to add class newClass
- `selectedElement.classList.remove("oldClass")` to remove class oldClass
- `selectedElement.classList.toggle("newClass")` to toggle newClass (if element has it, remove it, otherwise add)

## Event listeners

- `selectedElement.addEventListener("click", () => {})` (selected e.g. with querySelector and assigned to variable)
- `() => {}` - arrow function used for short: (possible arguments) => {function body with commands}

## Booleans

- comparisons within var.definition result in booleans, e.g. `const adult = age >= 18; //true for age=20`
- ternary operator `? :` - gives two values for a condition:

```
condition ? expressionIfTrue : expressionIfFalse;
const greetingText = time < 12 ? "Good morning." : "Good afternoon.";
```

## Arrays

- to put undefined as element, better put `null`, because all elements that have not been given a value will also display _undefined_
- `myArray[0][3][2]` to refer to values in nested arrays
- `myArray.push("newElement")` to add new element at the end of the array
- `myArray.pop()` to remove element from the end of the array
- `myArray.shift()` to remove element from the beginning of the array
- `myArray.unshift("newElement")` to add element to the beginning of the array
- arrays/objects that are assigned to each other give out the same contents if changed:

```
let arr1 = [];
let arr2 = arr1;
arr2.push(12);
console.log(arr1);    //[12]
```

## Objects

- access elements by .-notation (ex. person.name) or []-notation (ex. person["name"])
- []-notation needed for working with variables:

```
const propertyName = "name";
console.log(person[propertyName]);    //[nameOfPerson]
```

-create new elements: `person.lastName = "Lutz"`;
-constants with objects or arrays still can be changed by changing, removing or adding elements, but they cannot be reassigned as a whole!

### `npm run test` in terminal to run existing test files in the challenges-folder

## Functions

- anonymous functions only used in one spot can be without name `function(){}`
- regular use:

```
function exampleFunction() {
  console.log("example");
}; // declaration
exampleFunction(); // call
```

- functions can hold parameters as local variables (when called arguments are passed on), ex.

```
function exampleFunction(par1, par2){
console.log(par1 + par2)
}
exampleFunction (5, 2); // call with tow arguments, logs 7
```

## Early return

- return ends the function, no other commands after that will be executed

## Arrow-function

-different ways of writing functions:

```
function sum(a, b) {
  return a + b
}

const sum = function (a, b) {
  return a + b
}

const sum = (a, b) => {
  return a + b
}

sum(5, 7); // same call for all 3 cases
```

- brackets and return-keyword can be left out in arrow-function, if there is only one argument or command:

```
const double = a => a*2;
double (5); //to call
```

- good way to practise is rewriting a function from regular declaration

## HTML forms

- different input types: text, color, number, button, submit, radio (single-choice), checkbox (multiple-choice)
- different button types: reset, button, submit
- `<textarea></textarea>` own tag with attributes `cols` and `rows` for size
- default `<button></button>` type is sumbmit
- select-boxes, ex.:

```
<select name="country" id="coutry">
  <option value="1">Germany</option>
  <option value="2">Austria</option>
</select>
```

- labels assigned to ids, ex.:

```
<label for="name"></label>
<input id="name" type="text">
```

- usefull attributes: placeholder, value, id, name, type, required
- all elements in a `<form></form>` come with name and assign them a value. That pair is submitted on submit
- specify possible input, like: `<input type="number" min="5" max"10"`>
- more info: https://www.w3schools.com/html/html_forms.asp

## Inputs and Strings

- use `"" or ''`
- template literals:
  - can give out variables inside string \`Hello ${variableName}\`
  - can contain html elements
  - can contain new lines
- methods:
- .length - returns number of characters
- .toUpperCase() - makes string all uppercase
- .toLowerCase() - makes string all lowercase
- .trim() - returns string with all whitespace removed from beginning and end
- .replaceAll(oldString, newString) - replaces all occurences of old to new
- .startsWith(subString), .endsWith(subString), .includes(subString) - returns true or false

## Forms

- preventing default behaviour of buttons or elements (like sending for type="submit"), ex.:

```
const form = document.querySelector('[data-js="form"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
});
```

- by calling `event.preventDefault()` the browser will not perform a GET request that would cause the page to reload on submit
- `event.target` references to element to which it originated from, in the case of submit-button, it's the form, specific form fields can be targetted with dot notation, like `event.target.elements.firstName`
- input values can also be accessed with `FormData()` constructor, ex.:

```
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(event.target);
  const data = Object.fromEntries(formData);

  console.log(data);
});
```

- exceptions are checkboxes, here the key `.checked` needs to be used, like:

```
console.log(formElements.colorBlue.checked); // output: true or false
console.log(formElements.colorBlue.value); // output (always): blue
```

- useful event types:
  - `"input"` - triggered with every change in the field
  - `"change"` - only triggered after focussing a next field or submission
- focus on fields with `.focus()`, like `event.target.elements.message.focus()`
- resetting forms to their default value with `event.target.reset()` on a "submit"

## create HTML-elements in JS

- bad way is using .innerHTML, better:
- `const newPar = document.createElement("p")` to create new element
- `newPar.classList.add("card")` to add class
- `.setAttribute("id", "myId")` to give other attributes
- `document.section.append(newPar)` to add element as last child to section
- use functions to create severeal elements quicker

## for-loops

- regular form, ex. `for(let i=0; i<5; i++){commands}`
- but contents can vary or be left out, like `for(;;)`
- for of - used to loop through arrays, ex. `for(value of array){commands, like console.log(value)}`
- for in - used to loop through objects, ex. `for(key in object){commands, like console.log(object[key])}`
- can be nested, ex. to go through an array inside of an array

## callback functions

- functions can be called inside of functions and even used as parameters, ex.:

```
function calculation (operation, number1, number2) {
  let sum = operation(number1, number2);
}
function addition (num1, num2) {
  return num1+num2;
}

console.log(calculation (addition, 5, 3)); //logs 8
```

## Array Methods

- **.forEach()** executes function for each array element, ex.:

```
const myArray = ["a", "b", "c"];
myArray.forEach((element) => console.log(element)) // logs a /n b /n c
```

- called with the following arguments: callbackFn(function to execute on each element), element(individual element of array), index(index of the element), array(the array it is executed on)
- **.map** creates new array from old array, ex.:

```
const myArray = [1, 3, 5];
const map1 = myArray.map((x) => x*2);
console.log(map1); // logs [2, 6, 10]
```

- **.filter()** gives us an array of elements that fit a condition, ex.:

```
const myArray = ["hi", "hello", "miau"];
const result = myArray.filter((x) => x.length>3);
console.log(result); // logs ["hello", "miau"]
```

## Recursion

- you can call the same function inside a function, ex. for going through nested arrays, etc.
- needs to come with some sort of condition to not become an infinite loop

```
const arr = [1,2, [3, 4], 5, [6, [7, 8]]];

function getElementsCount(arr) {
  let count = 0;
  for (let i of arr) {
    if (Array.isArray(i)) {
      count += getElementsCount(i)
    } else {
      count++;
    }
  }
  return count;
}

console.log(getElementsCount(arr)); //logs 8
```

## Code Structure

- try to break down large code in several .js-files
- organization should be done in sub-folders - lib (for functions), data (for data), components (for app-components like Card or Header) seperately from css or togehter, e.g. put a header function Header.js in a folder Header (components starting with capital letter)
- individual files should be functions or data that are called in index.js
- functions not refering to components can be saved in a lib **folder**
- we need to **import all components** in index.js: `import { Header } from "./components/Header/Header.js"`
- we need to add type="modules" to the `<script type="module" src="./index.js"></script>` tag in the html and get rid of `defer`
- do frequent commits at stable middle stages

## Async methods

-

## fetch-requests

- interaction with APIs
- 'fetch' gets info from API, make sure to use it in async functions to be able to wait for the answer, ex.:

```
button.addEventListener("click", async ()=> {
  const response = await fetch ("https://api.com");
  const data = await response.json();

})
```
