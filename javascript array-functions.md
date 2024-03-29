# JavaScript-Array: tricks and functions

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

## Array Methods

- **.forEach()** executes function for each array element, ex.:

```
const myArray = ["a", "b", "c"];
myArray.forEach((element) => console.log(element)) // logs a /n b /n c
```

- called with the following arguments: callbackFn(function to execute on each element), element(individual element of array), index(index of the element), array(the array it is executed on)
- **.map()** creates new array from old array, ex.:

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

- **arr.includes("Harry")** - checks, if Harry is an element of arr
- **arr.find(age=>age>30)** - returns first element that meets condition (as opposed to .filter which gives out all)
- **arr.findIndex(age=>age>30)** - returns index of first element that meets condition
- **arr.sort()** - returns the sorted array in alphanumerical order; **arr.sort(a, b) => a-b** in correct order and ...b-a in reverse order; make sure strings are toLowerCase before sorting (if not the sort does not work properly)
- **arr.reverse()** - reverses order of array
- **arr.slice()** creates copy to avoid mutation
- **arr.some(element=>element.length>5)** gives true or false if any element meets condition
- **arr.every(element=>element.length>5)** gives true or false if ALL elements meet condition
- **arr.reduce()** gives out single value like a sum in arr.reduce((a,b)=>a+b)

## Recent methods not mutating original

- good alternatives instad of cpoying before with ".slice()" or ".map()"
- start with "to", like ".toReduced()", ".toSpliced()", ...
