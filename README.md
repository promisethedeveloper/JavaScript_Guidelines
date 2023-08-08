# JavaScript Guidelines

## Arrays

### Array Creation
For creating arrays, use literal and not constructors.

Create arrays like this:

```
  const companyNames = [];

```

Don't do this while creating arrays:

```
  const companyNames = new Array(length);

```

### Item addition
When adding items to an array, use `push()` and not direct assignment. Consider the following array:

```
  const roles = [];

```

Add items to the array like this:

```
   roles.push("Software Developer");

```

Don't add items to the array like this:

```
   roles[roles.length] = "Software Developer";

```

## Asynchronous methods

Writing asynchronous code improves performance and should be used when possible. In particular, you can use:
* `Promises`
* `async / await`

When both techniques are possible, we prefer using `async / await` syntax.

## Comments
Comments are critical to writing good code examples. They clarify the intent of the code and help developers understand it. Pay special attention to them.

* If the purpose or logic of the code isn't obvious, add a comment with your intention, as shown below:


```
  let total = 0;

  // Calculate the sum of the four first elements of arr
   for (let i = 0; i < 4; i++) {
      total += arr[i];
  }

```

On the other hand, restating the code in prose is not a good use of comments:


```
  let total = 0;

  // For loop from 1 to 4
   for (let i = 0; i < 4; i++) {
      // Add value to the total
      total += arr[i];
  }

```

* Comments are also not necessary when functions have explicit names that describe what they're doing. Write:
  
```
startConnection();

```

Don't write:

```
startConnection(); // Starting the connection

```

## Use single-line comments
Single-line comments are marked with `//`, as opposed to block comments closed between `/* ... */`.

In general, use single-line comments to comment code. Writers must mark each line of the comment with `//`, so that it's easier to notice commented-out code visually. In addition, this convention allows to comment out sections of code using `/* ... /*` while debugging.

* Leave a space between the slashes and the comment. Start with a capital letter, like a sentence, but don't end the comment with a period.

  ```
  
  // This is a well-written single-line comment
  
  ```

* If a comment doesn't start immediately after a new indentation level, add an empty line and then add the comment. It will create a code block, making it obvious what the comment refers to.
Also, put your comments on seperate lines preceding the code they are referring to. This is shown in the following example:

```

function checkOut(goodPrice, shipmentPrice, taxes) {
  // Calculate the total price
  const total = goodPrice + shipmentPrice + taxes;

  // Create and append a new paragraph to the document
  const para = document.createElement("p");
  para.textContent = `Total price is ${total}`;
  document.body.appendChild(para);
}

```


## Output of logs
* In code intended to run in a production environment, you rarely need to comment when you log some data. In code examples, we often use `console.log()`, `console.error()`, or similar functions to output important values. To help the reader understand what will happen without running the code, you can put a comment after the function with the log that will be produced. Write:


```

function exampleFunc(fruitBasket) {
  console.log(fruitBasket); // ['banana', 'mango', 'orange']
}

```

Don't write:

```

function exampleFunc(fruitBasket) {
  // Logs: ['banana', 'mango', 'orange']
  console.log(fruitBasket); 
}

```

* In case the lines becomes too long, put the comment after the function, like this:

```

function exampleFunc(fruitBasket) {
  console.log(fruitBasket);
  //  ['banana', 'mango', 'orange']
}

```


## Multi-line comments
Short comments are usually better, so try to keep them in one line of 60 - 80 characters. If this is not possible, use `//` at the beginning of each line:

```
// This is an example of a multi-line comment.
// The imaginary function that follows has some unusual
// limitations that I want to call out.
// Limitation 1
// Limitiation 2

```
Don't use `/* ... */`:

```
/* This is an example of a multi-line comment.
  The imaginary function that follows has some unusual
  limitations that I want to call out.
  Limitation 1
  Limitiation 2 */

```


## Comment out parameters
When writing code, you usually omit parameters you don't need. But in some code examples, you want to demonstrate that you didn't use some possible parameters.

To do so, use `/* ... */` in the parameter list. This is an exception to the rule to only use sigle-line comment (`//`).


```
array.forEach((value /*, index, array /*) => {
  // ...
});
```

## Functions
### Function names
For function names, use camelCase, starting with a lowercase character. Use concise, human-readable, and semantic names where appropriate.

The following is a correct example of a function name:

```
function sayHello() {
  console.log("Hello");
}
```
Don't use functions names like these:


```
function SayHello() {
  console.log("Hello!");
}

function doIt() {
  console.log("Hello!");
}

```

### Function declarations
* Where possible, use the function declaration over function expression to define functions. Here is the recommended way to declare a function:

```
function sum(a, b) {
  return a + b;
}

```

This is not a good way to define a function:

```
let sum = function (a, b) {
  return a + b;
};
```

* When using anonymous functions as a callback (a function passed to another method invocation), if you do not need to access `this`, use an arrow function to make the code shorter and cleaner. Here is the recommnended way:

```
const array1 = [1, 2, 3, 4];
const sum = array1.reduce((a, b) => a + b);
```

Instead of this:
```
const array1 = [1, 2, 3, 4];
const sum = array1.reduce(function(a, b) {
  return a + b;
});
```

* Consider avoiding using arrow functions to assign a function to an identifier. In particular, don't use arrow functions for methods. Use function declarations with the keyword `function`:

```
function x() {
  // ...
}
```

Don't do:

```
const x = () => {
  // ...
}
```

* When using arrow functions, use implicit return (also known as concise body) when possible:

```
arr.map((e) => e.id);
```

And not:

```
arr.map((e) =>  {
  return e.id;
});
```

## Loops and Conditional statements
### Loop initialization
When loops are required, choose the appropriate one from `for(;;)` , `for...of`, `while`, etc.

* When iterating through all collections elements, avoid using the classical `for (;;)` loop; prefer `for..of` or `forEach()`. Note that if you are using a collection that is not an `Array`, you have to check that `for...of` is actually supported (it requires the variable to be iterable), or that the `forEach()` method is actually present. Use `for...of`:


```
const roles = ["Software Developer", "Database Analyst"];
for (const role of roles) {
  console.log(role);
}
```

Or `forEach()`:

```
const roles = ["Software Developer", "Database Analyst"];
roles.forEach((role) => {
  console.log(role);
})
```

Do not use `for (;;)` - not only do you habe to add an extra index, `i`, but you also have to track the length of the array. This can be error-prone for beginners.

```
const roles = ["Software Developer", "Database Analyst"];
for (let i = 0; i < roles.length; i++) {
  console.log(roles[i]);
};
```

* Make sure that you define the initializer properly by using the `const` keyword for `for...of` or `let` for the other loops. Don't omit it. These are correct examples:

```
const cats = ["Athema", "Luna"];
for (const cat of cats) {
  console.log(cat);
}

for (let i = 0; i < 4; i++) {
  result += arr[i];
}

```

The example below does not follow the recommended guidelines for the initialization (it implicitly creates a global variable and will fail in strict mode):

```
const cats = ["Athema", "Luna"];
for (i of cats) {
  console.log(i);
}

```

* When you need to access both the value and the index, you can use `.forEach()` instead of `for (;;)`. Write:

```
const cats = ["Athema", "Luna"];
cats.forEach((cat, i) => {
  console.log(`Cat #${i}: ${cat[i]}`);
});
```

Do not write:

```
const cats = ["Athema", "Luna"];
for (let i = 0; cats.length; i++) {
  console.log(`Cat #${i}: ${cat[i]}`);
}
```
> [!WARNING]  
> Never use `for...in` with arrays and strings.

> [!NOTE]  
> Consider not using a `for` loop at all. If you are using an `Array`. (or a `string` for some operations), consider using more semantic iteration methods instead, like `map()`, `every()`, `findIndex()`, `find()`, `includes()`, and many more.
