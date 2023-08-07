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

On the other hand, restating the code in prose is NOT a good use of comments:


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


## Use comments to mark ellipsis
Skipping reduntant code using ellipses `(..)` is necessary to keep examples short. Still, writers should do it thoughtfully as developers frequently as developers frequently copy & paste examples into their code, and all of our code samples should be valid JavaScript.
